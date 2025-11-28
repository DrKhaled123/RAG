best docker config:



# 🐳 OPTIMIZED DOCKER HYBRID CONFIGURATION

## 🏗️ OPTIMIZED DOCKERFILE

```dockerfile
# =====================================
# Stage 1: Dependencies
# =====================================
FROM node:20-alpine AS deps

WORKDIR /app

# Copy package files first for better caching
COPY package*.json ./

# Install dependencies with cache mount for speed
RUN --mount=type=cache,target=/root/.npm \
    npm ci --only=production --ignore-scripts

# =====================================
# Stage 2: Build
# =====================================
FROM node:20-alpine AS builder

WORKDIR /app

# Copy dependencies from stage 1
COPY --from=deps /app/node_modules ./node_modules
COPY . .

# Build application
RUN npm run build

# =====================================
# Stage 3: Runtime (Flexible for different use cases)
# =====================================
# Option 1: Standard web app (distroless for security)
FROM gcr.io/distroless/nodejs20-debian12 AS runtime

# Option 2: For LLM apps requiring additional libraries
# FROM node:20-alpine AS runtime
# RUN apk add --no-cache libstdc++ libgomp ca-certificates

WORKDIR /app

# Copy built app and production dependencies
COPY --from=builder /app/build ./build
COPY --from=builder /app/node_modules ./node_modules
COPY --from=builder /app/package.json ./

# Copy models if bundling (for LLM apps)
# COPY --from=builder /app/models ./models

EXPOSE 3000

ENV NODE_ENV=production

CMD ["build/index.js"]
```

## 🐳 DOCKER COMPOSE CONFIGURATIONS

### docker-compose.yml (Development)
```yaml
version: '3.9'

services:
  app:
    build:
      context: .
      dockerfile: Dockerfile
      target: builder  # Use builder stage for development
    container_name: myapp-dev
    restart: unless-stopped
    environment:
      - NODE_ENV=development
      - PORT=3000
    ports:
      - "3000:3000"
    volumes:
      - .:/app  # Mount source for hot reload
      - /app/node_modules  # Use container node_modules
    command: npm run dev
    networks:
      - app-network

  # Optional: Database for development
  db:
    image: postgres:15-alpine
    container_name: myapp-db-dev
    restart: unless-stopped
    environment:
      POSTGRES_DB: mydb
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
    ports:
      - "5432:5432"
    volumes:
      - pgdata-dev:/var/lib/postgresql/data
    networks:
      - app-network

volumes:
  pgdata-dev:

networks:
  app-network:
    driver: bridge
```

### docker-compose.staging.yml (Staging Environment)
```yaml
version: '3.9'

services:
  app:
    build:
      context: .
      dockerfile: Dockerfile
      target: runtime  # Use runtime stage for production
    image: myapp:staging
    container_name: myapp-staging
    restart: unless-stopped
    environment:
      - NODE_ENV=staging
      - PORT=3000
      - DATABASE_URL=postgresql://user:password@db:5432/mydb
      - REDIS_URL=redis://redis:6379
    ports:
      - "3000:3000"
    depends_on:
      db:
        condition: service_healthy
      redis:
        condition: service_healthy
    healthcheck:
      test: ["CMD", "node", "-e", "require('http').get('http://localhost:3000/health', (r) => r.statusCode === 200 ? process.exit(0) : process.exit(1))"]
      interval: 30s
      timeout: 3s
      start_period: 40s
      retries: 3
    networks:
      - app-network
    volumes:
      - ./logs:/app/logs

  db:
    image: postgres:15-alpine
    container_name: myapp-db-staging
    restart: unless-stopped
    environment:
      POSTGRES_DB: mydb
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
    volumes:
      - pgdata-staging:/var/lib/postgresql/data
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U user"]
      interval: 10s
      timeout: 5s
      retries: 5
    networks:
      - app-network

  redis:
    image: redis:7-alpine
    container_name: myapp-redis-staging
    restart: unless-stopped
    command: redis-server --requirepass password
    healthcheck:
      test: ["CMD", "redis-cli", "ping"]
      interval: 10s
      timeout: 5s
      retries: 3
    networks:
      - app-network

volumes:
  pgdata-staging:

networks:
  app-network:
    driver: bridge
```

### docker-compose.prod.yml (Production Environment)
```yaml
version: '3.9'

services:
  # Blue instance (current production)
  app-blue:
    build:
      context: .
      dockerfile: Dockerfile
      target: runtime
    image: myapp:production
    container_name: myapp-blue
    restart: unless-stopped
    environment:
      - NODE_ENV=production
      - PORT=3000
      - DATABASE_URL=postgresql://user:${DB_PASSWORD}@db:5432/mydb
      - REDIS_URL=redis://redis:6379
      - JWT_SECRET=${JWT_SECRET}
    depends_on:
      db:
        condition: service_healthy
      redis:
        condition: service_healthy
    healthcheck:
      test: ["CMD", "node", "-e", "require('http').get('http://localhost:3000/health', (r) => r.statusCode === 200 ? process.exit(0) : process.exit(1))"]
      interval: 30s
      timeout: 3s
      start_period: 40s
      retries: 3
    networks:
      - app-network
    volumes:
      - ./logs:/app/logs
    deploy:
      resources:
        limits:
          cpus: '2'
          memory: 2G
        reservations:
          cpus: '0.5'
          memory: 512M

  # Green instance (new version)
  app-green:
    build:
      context: .
      dockerfile: Dockerfile
      target: runtime
    image: myapp:production
    container_name: myapp-green
    restart: unless-stopped
    environment:
      - NODE_ENV=production
      - PORT=3001  # Different port
      - DATABASE_URL=postgresql://user:${DB_PASSWORD}@db:5432/mydb
      - REDIS_URL=redis://redis:6379
      - JWT_SECRET=${JWT_SECRET}
    depends_on:
      db:
        condition: service_healthy
      redis:
        condition: service_healthy
    healthcheck:
      test: ["CMD", "node", "-e", "require('http').get('http://localhost:3001/health', (r) => r.statusCode === 200 ? process.exit(0) : process.exit(1))"]
      interval: 30s
      timeout: 3s
      start_period: 40s
      retries: 3
    networks:
      - app-network
    volumes:
      - ./logs:/app/logs
    deploy:
      resources:
        limits:
          cpus: '2'
          memory: 2G
        reservations:
          cpus: '0.5'
          memory: 512M

  # Database (shared)
  db:
    image: postgres:15-alpine
    container_name: myapp-db
    restart: unless-stopped
    environment:
      POSTGRES_DB: ${DB_NAME}
      POSTGRES_USER: ${DB_USER}
      POSTGRES_PASSWORD: ${DB_PASSWORD}
    volumes:
      - pgdata:/var/lib/postgresql/data
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U ${DB_USER}"]
      interval: 10s
      timeout: 5s
      retries: 5
    networks:
      - app-network

  # Redis (shared)
  redis:
    image: redis:7-alpine
    container_name: myapp-redis
    restart: unless-stopped
    command: redis-server --requirepass ${REDIS_PASSWORD}
    healthcheck:
      test: ["CMD", "redis-cli", "ping"]
      interval: 10s
      timeout: 5s
      retries: 3
    networks:
      - app-network

  # Caddy with blue-green routing
  caddy:
    image: caddy:2.8-alpine
    container_name: caddy-proxy
    restart: unless-stopped
    ports:
      - "80:80"
      - "443:443"
    volumes:
      - ./Caddyfile:/etc/caddy/Caddyfile
      - ./Caddyfile.green:/etc/caddy/Caddyfile.green
      - caddy-data:/data
      - caddy-config:/config
    depends_on:
      - app-blue
    networks:
      - app-network

volumes:
  pgdata:
  caddy-data:
  caddy-config:

networks:
  app-network:
    driver: bridge
```

### docker-compose.llm.yml (LLM Application)
```yaml
version: '3.9'

services:
  app:
    build:
      context: .
      dockerfile: Dockerfile
      target: runtime  # Use runtime stage with LLM libraries
    image: myapp-llm:production
    container_name: myapp-llm
    restart: unless-stopped
    environment:
      - NODE_ENV=production
      - PORT=3000
      - OLLAMA_HOST=http://ollama:11434
      - OLLAMA_MODEL=${OLLAMA_MODEL:-deepseek-coder-v2:16b-lite-instruct-q4_K_M}
      - PUBLIC_USE_OLLAMA=true
    ports:
      - "127.0.0.1:3000:3000"  # Only expose locally
    depends_on:
      ollama:
        condition: service_healthy
    healthcheck:
      test: ["CMD", "node", "-e", "require('http').get('http://localhost:3000/health', (r) => r.statusCode === 200 ? process.exit(0) : process.exit(1))"]
      interval: 30s
      timeout: 3s
      start_period: 40s
      retries: 3
    networks:
      - app-network
    volumes:
      - ./logs:/app/logs
    deploy:
      resources:
        limits:
          cpus: '2'
          memory: 4G  # More memory for LLM processing
        reservations:
          cpus: '1'
          memory: 2G

  # Ollama service
  ollama:
    image: ollama/ollama:latest
    container_name: ollama-server
    restart: unless-stopped
    ports:
      - "127.0.0.1:11434:11434"
    volumes:
      - ollama-models:/root/.ollama
    environment:
      - OLLAMA_HOST=0.0.0.0:11434
      - OLLAMA_KEEP_ALIVE=24h
      - OLLAMA_NUM_PARALLEL=2
    deploy:
      resources:
        reservations:
          devices:
            - driver: nvidia
              count: all
              capabilities: [gpu]
    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost:11434/api/tags"]
      interval: 30s
      timeout: 10s
      retries: 3
    networks:
      - app-network

volumes:
  ollama-models:

networks:
  app-network:
    driver: bridge
```

## 🛠️ BUILD SCRIPTS

### build.sh (Universal build script)
```bash
#!/bin/bash
set -e

# Configuration
IMAGE_NAME="myapp"
REGISTRY=${REGISTRY:-""}
TAG=${TAG:-"latest"}
BUILD_TARGET=${BUILD_TARGET:-"runtime"}

# Build arguments
BUILD_ARGS=""
if [ -n "$BUILD_TARGET" ]; then
    BUILD_ARGS="--target $BUILD_TARGET"
fi

# Build image
echo "Building $IMAGE_NAME:$TAG with target $BUILD_TARGET..."
docker build $BUILD_ARGS -t $IMAGE_NAME:$TAG .

# Tag with registry if provided
if [ -n "$REGISTRY" ]; then
    docker tag $IMAGE_NAME:$TAG $REGISTRY/$IMAGE_NAME:$TAG
    echo "Tagged as $REGISTRY/$IMAGE_NAME:$TAG"
fi

echo "Build completed successfully!"
```

### build-multi-arch.sh (Multi-architecture build)
```bash
#!/bin/bash
set -e

# Configuration
IMAGE_NAME="myapp"
REGISTRY=${REGISTRY:-""}
TAG=${TAG:-"latest"}
PLATFORMS=${PLATFORMS:-"linux/amd64,linux/arm64"}

# Create builder if not exists
docker buildx inspect multiarch-builder >/dev/null 2>&1 || \
    docker buildx create --name multiarch-builder --use

# Build and push
echo "Building multi-arch image for $PLATFORMS..."
docker buildx build \
    --platform $PLATFORMS \
    --target runtime \
    -t $IMAGE_NAME:$TAG \
    ${REGISTRY:+-t $REGISTRY/$IMAGE_NAME:$TAG} \
    --push \
    .

echo "Multi-arch build completed successfully!"
```

## 📋 .dockerignore (Optimized)
```
# Dependencies
node_modules
npm-debug.log*

# Build outputs
dist
build
.next
.nuxt

# Environment files
.env
.env.local
.env.development.local
.env.test.local
.env.production.local

# IDE
.vscode
.idea
*.swp
*.swo

# OS
.DS_Store
Thumbs.db

# Git
.git
.gitignore

# Docker
Dockerfile*
docker-compose*
.dockerignore

# Logs
logs
*.log

# Tests
coverage
.nyc_output
```

## 🌍 ENVIRONMENT VARIABLES

### .env.example (Template)
```ini
# Application
NODE_ENV=production
PORT=3000

# Database
DB_HOST=db
DB_NAME=mydb
DB_USER=user
DB_PASSWORD=supersecurepassword123
DB_PORT=5432

# Redis
REDIS_HOST=redis
REDIS_PORT=6379
REDIS_PASSWORD=anothersecurepassword456

# Ollama (for LLM apps)
OLLAMA_HOST=ollama
OLLAMA_PORT=11434
DEFAULT_MODEL=deepseek-coder-v2:16b-lite-instruct-q4_K_M

# Security
JWT_SECRET=jwt_secret_here_32_chars_min
SESSION_SECRET=session_secret_here_32_chars_min

# Registry
REGISTRY=your-registry.com
TAG=latest
```

## 🚀 DEPLOYMENT COMMANDS

### Development
```bash
# Start development environment
docker-compose up -d

# View logs
docker-compose logs -f app

# Stop development environment
docker-compose down
```

### Staging
```bash
# Build and deploy to staging
./build.sh
TAG=staging docker-compose -f docker-compose.staging.yml up -d --build

# View logs
docker-compose -f docker-compose.staging.yml logs -f app
```

### Production (Blue-Green)
```bash
# Build and deploy green instance
./build.sh
docker-compose -f docker-compose.prod.yml up -d --build app-green

# Wait for health check
echo "Waiting for green instance to be healthy..."
timeout 300 bash -c 'until curl -f http://localhost:3001/health; do sleep 5; done'

# Switch traffic
echo "Switching traffic to green instance..."
docker-compose -f docker-compose.prod.yml exec -T caddy caddy reload --config /etc/caddy/Caddyfile.green

# Stop blue instance
echo "Stopping blue instance..."
docker-compose -f docker-compose.prod.yml stop app-blue
docker-compose -f docker-compose.prod.yml rm -f app-blue

# Clean up
docker image prune -f
```

### LLM Application
```bash
# Build and deploy LLM app
./build.sh
docker-compose -f docker-compose.llm.yml up -d --build

# Pull model (first time only)
docker-compose -f docker-compose.llm.yml exec ollama ollama pull deepseek-coder-v2:16b-lite-instruct-q4_K_M
```

## 🚨 COMMON DOCKER ERRORS & SOLUTIONS

### Error 1: "Cannot find module" in production
```dockerfile
# ❌ WRONG
FROM node:20-alpine
COPY build ./build
# Missing node_modules!

# ✅ CORRECT
FROM node:20-alpine
COPY --from=builder /app/build ./build
COPY --from=builder /app/node_modules ./node_modules  # Essential!
COPY --from=builder /app/package.json ./
```

### Error 2: "EACCES: permission denied" in container
```yaml
# Solution in docker-compose.yml
services:
  app:
    user: "1001:1001"  # Match host user UID:GID
    volumes:
      - ./logs:/app/logs:Z  # :Z for SELinux contexts
```

### Error 3: "Connection refused" between containers
```yaml
# ❌ WRONG
environment:
  - OLLAMA_HOST=http://localhost:11434

# ✅ CORRECT (use service name from docker-compose)
environment:
  - OLLAMA_HOST=http://ollama:11434
```

### Error 4: GPU not accessible in Docker
```bash
# Install NVIDIA Container Toolkit
distribution=$(. /etc/os-release;echo $ID$VERSION_ID)
curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add -
curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | \
  sudo tee /etc/apt/sources.list.d/nvidia-docker.list

sudo apt-get update && sudo apt-get install -y nvidia-container-toolkit
sudo systemctl restart docker

# Test GPU access
docker run --rm --gpus all nvidia/cuda:12.0-base nvidia-smi
```

### Error 5: Out of Memory (OOM) killer
```yaml
# Solution in docker-compose.yml
services:
  app:
    deploy:
      resources:
        limits:
          memory: 16G  # Set appropriate limit
        reservations:
          memory: 8G
    environment:
      - NODE_OPTIONS=--max-old-space-size=4096  # Node.js heap limit
```

## 🎯 WHY THIS HYBRID IS BETTER

1. **Flexibility**: Supports different environments (dev, staging, prod, LLM)
2. **Security**: Uses distroless images for production
3. **Performance**: Optimized multi-stage builds with caching
4. **Scalability**: Blue-green deployment strategy
5. **LLM Support**: Dedicated configuration for LLM applications
6. **Error Handling**: Comprehensive error solutions
7. **Simplicity**: Clean, coherent structure without overcomplexity

This hybrid Docker configuration provides a solid foundation for any web application, with specialized configurations for different use cases while maintaining a consistent structure and best practices.