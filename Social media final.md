Social media.med

### Title: **Ultra-Comprehensive 7-Day Plan to Build an Enterprise-Grade Social Media Automation App with Full Compliance Framework**

**Prompt:**

I want to create a comprehensive, enterprise-grade social media automation application within a one-week timeframe. This application should be capable of performing sophisticated automation tasks across multiple social media platforms, including but not limited to: sending messages at scale, inviting users to groups, scheduling and publishing content, managing multiple accounts simultaneously, tracking engagement metrics, and providing detailed analytics dashboards.

However, I am fully aware that such automation capabilities could potentially raise serious concerns regarding spam, social media manipulation, unwanted bulk messaging, violations of platform terms of service, privacy violations, and other legal and ethical issues. While I understand there are legitimate business use cases for such an application (such as marketing agencies managing multiple client accounts with explicit written consent, businesses managing their own brand presence across platforms, content creators scheduling posts, and customer service teams managing support inquiries), I want to ensure that the application is built with compliance, ethics, and best practices at its core from day one.

Please provide an exceptionally detailed, step-by-step 7-day implementation plan for building this social media automation application. The plan should be realistic, achievable within the one-week timeframe, and include every single tool, technology, platform, service, code snippet, configuration file, deployment instruction, and best practice necessary for success. Additionally, please emphasize and thoroughly cover the following critical areas:

---

## **1. Comprehensive Legal and Compliance Requirements:**

- **International Regulations:**  
  - Provide detailed explanations of the CAN-SPAM Act (United States), including specific requirements for commercial email, opt-out mechanisms, and penalty structures (up to $43,792 per violation).
  - Explain GDPR (European Union) requirements, including data processing agreements, right to erasure, data portability, consent mechanisms, and potential fines (up to €20 million or 4% of global annual revenue).
  - Cover CASL (Canada's Anti-Spam Legislation), including consent requirements and penalty structures.
  - Discuss PECR (Privacy and Electronic Communications Regulations) in the UK.
  - Address California Consumer Privacy Act (CCPA) and California Privacy Rights Act (CPRA) requirements.
  - Include information about Australia's Spam Act 2003 and other relevant international regulations.

- **Platform-Specific Terms of Service:**  
  - Provide detailed breakdowns of each platform's automation policies:
    - **Facebook:** Message limits (50 messages per day to non-friends), API restrictions, business use cases, Page messaging vs. personal messaging, Messenger Platform policies.
    - **Instagram:** Direct message limits (20-50 per hour depending on account age and reputation), API limitations, business vs. personal accounts, Instagram Graph API restrictions.
    - **Twitter/X:** API rate limits (300 tweets per 3 hours, DM limits), automation rules, bot labeling requirements, developer agreement terms.
    - **TikTok:** Limited API access (currently in beta for most features), content posting restrictions, messaging limitations.
    - **LinkedIn:** Strict anti-automation policies, API access requirements, InMail limitations, connection request limits.
    - **WhatsApp:** Business API requirements, message templates, 24-hour messaging window, opt-in requirements.
    - **Telegram:** Bot API capabilities, group management, broadcast limitations.

- **Consent Management Framework:**  
  - Detailed implementation of double opt-in systems.
  - Database schema for storing consent records with timestamps, IP addresses, and consent method.
  - Automated opt-out/unsubscribe mechanisms with one-click functionality.
  - Consent audit trails and compliance reporting.
  - GDPR-compliant data retention and deletion policies.

- **Legal Documentation Templates:**  
  - Privacy policy templates specific to social media automation.
  - Terms of service agreements for SaaS platforms.
  - Data processing agreements (DPAs) for enterprise clients.
  - User consent forms and checkboxes with legally compliant language.

---

## **2. Extensive Risk Assessment and Mitigation Strategies:**

- **Account Security Risks:**  
  - Detailed explanation of how automation can trigger platform security systems.
  - Account warming strategies for new accounts (gradual increase in activity).
  - IP rotation and proxy management to avoid detection.
  - Browser fingerprinting avoidance techniques.
  - Session management and cookie handling best practices.

- **Legal Liability Protection:**  
  - Liability disclaimers and user agreements.
  - Insurance recommendations for SaaS businesses.
  - Indemnification clauses for enterprise contracts.
  - Compliance monitoring and audit procedures.

- **Reputation Management:**  
  - Strategies to avoid being labeled as spam.
  - Content quality guidelines and filtering.
  - User feedback mechanisms and complaint handling.
  - Blacklist monitoring and management.

- **Technical Failure Scenarios:**  
  - API deprecation handling and version management.
  - Rate limit exceeded error handling and retry logic.
  - Account suspension detection and notification systems.
  - Data backup and disaster recovery procedures.

---

## **3. Deep Focus on Legitimate and Ethical Use Cases:**

- **Content Marketing Automation:**  
  - Multi-platform content calendar management.
  - Optimal posting time algorithms based on audience analytics.
  - Content variation and A/B testing frameworks.
  - Hashtag optimization and trend analysis.
  - Cross-platform content adaptation (resizing images, adjusting character limits).

- **Customer Relationship Management:**  
  - Social media inbox management and response automation.
  - Customer inquiry routing and prioritization.
  - Sentiment analysis for customer feedback.
  - Support ticket integration with platforms like Zendesk, Freshdesk.

- **Brand Monitoring and Engagement:**  
  - Keyword and mention tracking across platforms.
  - Competitor analysis and benchmarking.
  - Influencer identification and outreach management.
  - Crisis management and rapid response systems.

- **Analytics and Reporting:**  
  - Engagement metrics tracking (likes, shares, comments, saves).
  - Follower growth analytics and demographic insights.
  - ROI calculation for social media campaigns.
  - Custom report generation for clients.

- **Team Collaboration Features:**  
  - Multi-user access with role-based permissions.
  - Approval workflows for content publishing.
  - Comment and feedback systems for draft content.
  - Activity logs and audit trails.

---

## **4. Extremely Detailed Implementation Roadmap:**

### **PRE-DAY 1: Prerequisites and Preparation (Complete Before Starting)**

- **Hardware Requirements:**  
  - Development machine: Minimum 16GB RAM, 256GB SSD, modern multi-core processor.
  - Testing devices: iOS device, Android device for mobile app testing.
  - Stable internet connection with minimum 50 Mbps download speed.

- **Software Installation Checklist:**  
  - Operating System: macOS, Linux (Ubuntu 22.04 LTS recommended), or Windows with WSL2.
  - **Development Tools:**
    - Node.js 18.x LTS or 20.x (with npm 9.x+)
    - Python 3.10+ (with pip and virtualenv)
    - Docker Desktop 4.x+ (with Docker Compose)
    - Git 2.x+ (with GitHub/GitLab account configured)
    - Visual Studio Code (with extensions: ESLint, Prettier, Docker, Prisma, Python, GitLens)
    - Postman or Insomnia (for API testing)
    - DBeaver or TablePlus (for database management)
    - Redis Desktop Manager or RedisInsight
  
- **Account Creation (Complete Before Day 1):**  
  - **Developer Accounts:**
    - Facebook Developer Account (https://developers.facebook.com) - Requires business verification for production access.
    - Twitter Developer Account (https://developer.twitter.com) - Apply for Elevated or Academic access for higher rate limits.
    - Instagram Business Account (linked to Facebook Page).
    - TikTok Developer Account (https://developers.tiktok.com) - Note: Limited API access.
    - LinkedIn Developer Account (https://developer.linkedin.com) - Requires company page.
    - Google Cloud Platform (for YouTube API if needed).
  
  - **Infrastructure Accounts:**
    - GitHub/GitLab account for version control.
    - DigitalOcean, AWS, or Google Cloud Platform account (with payment method added).
    - Vercel account (for frontend hosting).
    - Render.com or Railway.app account (for backend hosting).
    - Supabase account (https://supabase.com) - PostgreSQL database hosting.
    - Upstash account (https://upstash.com) - Redis hosting.
    - Cloudflare account (for CDN and DDoS protection).
  
  - **Communication Services:**
    - SendGrid account (https://sendgrid.com) - Email delivery (100 emails/day free).
    - Twilio account (for SMS notifications if needed).
    - Slack workspace (for team notifications and monitoring alerts).
  
  - **Monitoring and Analytics:**
    - Sentry account (https://sentry.io) - Error tracking (5k events/month free).
    - LogRocket or FullStory (session replay and debugging).
    - Google Analytics 4 account.
    - Mixpanel or Amplitude (product analytics).

- **Domain and SSL:**  
  - Purchase domain name (Namecheap, Google Domains, or Cloudflare).
  - Configure DNS settings.
  - Set up SSL certificates (Let's Encrypt via Certbot or Cloudflare).

---

### **DAY 1: Foundation Architecture and Environment Setup (8-10 hours)**

**Morning Session (4 hours):**

1. **Project Structure Creation:**
```bash
# Create main project directory
mkdir social-automation-platform
cd social-automation-platform

# Initialize Git repository
git init
git branch -M main

# Create comprehensive folder structure
mkdir -p backend/{src/{routes,controllers,services,middleware,models,utils,queue,jobs},tests,config}
mkdir -p frontend/{src/{components,pages,hooks,utils,styles,types,contexts},public}
mkdir -p shared/{types,constants,validators}
mkdir -p infrastructure/{docker,kubernetes,terraform}
mkdir -p docs/{api,architecture,deployment}
mkdir -p scripts/{migration,seed,deployment}
```

2. **Backend Initialization (Node.js + TypeScript):**
```bash
cd backend
npm init -y

# Core dependencies
npm install express cors helmet compression morgan
npm install dotenv joi
npm install prisma @prisma/client
npm install bull ioredis bull-board
npm install passport passport-local passport-jwt passport-facebook passport-google-oauth20 passport-twitter
npm install bcryptjs jsonwebtoken
npm install axios form-data
npm install date-fns lodash

# TypeScript and development dependencies
npm install -D typescript @types/node @types/express @types/cors
npm install -D ts-node nodemon
npm install -D eslint prettier eslint-config-prettier
npm install -D jest @types/jest ts-jest supertest @types/supertest

# Initialize TypeScript
npx tsc --init
```

3. **TypeScript Configuration (tsconfig.json):**
```json
{
  "compilerOptions": {
    "target": "ES2022",
    "module": "commonjs",
    "lib": ["ES2022"],
    "outDir": "./dist",
    "rootDir": "./src",
    "strict": true,
    "esModuleInterop": true,
    "skipLibCheck": true,
    "forceConsistentCasingInFileNames": true,
    "resolveJsonModule": true,
    "moduleResolution": "node",
    "allowSyntheticDefaultImports": true,
    "declaration": true,
    "declarationMap": true,
    "sourceMap": true
  },
  "include": ["src/**/*"],
  "exclude": ["node_modules", "dist", "tests"]
}
```

4. **Database Schema Design (Prisma):**
```prisma
// prisma/schema.prisma
generator client {
  provider = "prisma-client-js"
}

datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}

model User {
  id            String          @id @default(uuid())
  email         String          @unique
  passwordHash  String
  firstName     String?
  lastName      String?
  company       String?
  role          UserRole        @default(USER)
  isVerified    Boolean         @default(false)
  createdAt     DateTime        @default(now())
  updatedAt     DateTime        @updatedAt
  
  socialAccounts SocialAccount[]
  campaigns      Campaign[]
  apiKeys        ApiKey[]
  subscriptions  Subscription[]
  auditLogs      AuditLog[]
  
  @@index([email])
}

enum UserRole {
  USER
  ADMIN
  AGENCY
  ENTERPRISE
}

model SocialAccount {
  id              String    @id @default(uuid())
  userId          String
  platform        Platform
  platformUserId  String
  username        String?
  displayName     String?
  profilePicture  String?
  accessToken     String
  refreshToken    String?
  tokenExpiresAt  DateTime?
  isActive        Boolean   @default(true)
  lastSyncedAt    DateTime?
  metadata        Json?
  createdAt       DateTime  @default(now())
  updatedAt       DateTime  @updatedAt
  
  user            User      @relation(fields: [userId], references: [id], onDelete: Cascade)
  posts           Post[]
  
  @@unique([userId, platform, platformUserId])
  @@index([userId])
  @@index([platform])
}

enum Platform {
  FACEBOOK
  INSTAGRAM
  TWITTER
  TIKTOK
  LINKEDIN
  YOUTUBE
  PINTEREST
  TELEGRAM
  WHATSAPP
}

model Campaign {
  id              String          @id @default(uuid())
  userId          String
  name            String
  description     String?
  platforms       Platform[]
  status          CampaignStatus  @default(DRAFT)
  scheduledAt     DateTime?
  startedAt       DateTime?
  completedAt     DateTime?
  totalPosts      Int             @default(0)
  successfulPosts Int             @default(0)
  failedPosts     Int             @default(0)
  createdAt       DateTime        @default(now())
  updatedAt       DateTime        @updatedAt
  
  user            User            @relation(fields: [userId], references: [id], onDelete: Cascade)
  posts           Post[]
  
  @@index([userId])
  @@index([status])
  @@index([scheduledAt])
}

enum CampaignStatus {
  DRAFT
  SCHEDULED
  RUNNING
  PAUSED
  COMPLETED
  FAILED
  CANCELLED
}

model Post {
  id              String       @id @default(uuid())
  campaignId      String
  socialAccountId String
  content         String       @db.Text
  mediaUrls       String[]
  hashtags        String[]
  mentions        String[]
  status          PostStatus   @default(PENDING)
  platformPostId  String?
  publishedAt     DateTime?
  scheduledFor    DateTime?
  errorMessage    String?
  retryCount      Int          @default(0)
  metadata        Json?
  createdAt       DateTime     @default(now())
  updatedAt       DateTime     @updatedAt
  
  campaign        Campaign     @relation(fields: [campaignId], references: [id], onDelete: Cascade)
  socialAccount   SocialAccount @relation(fields: [socialAccountId], references: [id], onDelete: Cascade)
  analytics       PostAnalytics?
  
  @@index([campaignId])
  @@index([socialAccountId])
  @@index([status])
  @@index([scheduledFor])
}

enum PostStatus {
  PENDING
  QUEUED
  PROCESSING
  PUBLISHED
  FAILED
  CANCELLED
}

model PostAnalytics {
  id          String   @id @default(uuid())
  postId      String   @unique
  likes       Int      @default(0)
  comments    Int      @default(0)
  shares      Int      @default(0)
  views       Int      @default(0)
  clicks      Int      @default(0)
  engagement  Float    @default(0)
  reach       Int      @default(0)
  impressions Int      @default(0)
  lastFetchedAt DateTime @default(now())
  createdAt   DateTime @default(now())
  updatedAt   DateTime @updatedAt
  
  post        Post     @relation(fields: [postId], references: [id], onDelete: Cascade)
  
  @@index([postId])
}

model ConsentRecord {
  id              String   @id @default(uuid())
  email           String
  phoneNumber     String?
  platform        Platform
  consentType     String   // email, sms, social_message
  consentMethod   String   // web_form, api, import
  ipAddress       String
  userAgent       String?
  consentedAt     DateTime @default(now())
  revokedAt       DateTime?
  isActive        Boolean  @default(true)
  metadata        Json?
  
  @@index([email])
  @@index([platform])
  @@index([isActive])
}

model ApiKey {
  id          String   @id @default(uuid())
  userId      String
  name        String
  key         String   @unique
  permissions Json
  lastUsedAt  DateTime?
  expiresAt   DateTime?
  isActive    Boolean  @default(true)
  createdAt   DateTime @default(now())
  
  user        User     @relation(fields: [userId], references: [id], onDelete: Cascade)
  
  @@index([userId])
  @@index([key])
}

model AuditLog {
  id          String   @id @default(uuid())
  userId      String
  action      String
  resource    String
  resourceId  String?
  ipAddress   String
  userAgent   String?
  metadata    Json?
  createdAt   DateTime @default(now())
  
  user        User     @relation(fields: [userId], references: [id], onDelete: Cascade)
  
  @@index([userId])
  @@index([action])
  @@index([createdAt])
}

model Subscription {
  id              String   @id @default(uuid())
  userId          String
  plan            String   // free, basic, pro, enterprise
  status          String   // active, cancelled, expired
  currentPeriodStart DateTime
  currentPeriodEnd   DateTime
  cancelAt        DateTime?
  createdAt       DateTime @default(now())
  updatedAt       DateTime @updatedAt
  
  user            User     @relation(fields: [userId], references: [id], onDelete: Cascade)
  
  @@index([userId])
  @@index([status])
}
```

**Afternoon Session (4-6 hours):**

5. **Environment Configuration:**
```bash
# .env file
NODE_ENV=development
PORT=3001
API_VERSION=v1

# Database
DATABASE_URL="postgresql://user:password@localhost:5432/social_automation?schema=public"

# Redis
REDIS_URL="redis://localhost:6379"
REDIS_PASSWORD=""

# JWT
JWT_SECRET="your-super-secret-jwt-key-change-in-production"
JWT_EXPIRES_IN="7d"
REFRESH_TOKEN_SECRET="your-refresh-token-secret"
REFRESH_TOKEN_EXPIRES_IN="30d"

# Facebook
FACEBOOK_APP_ID="your-app-id"
FACEBOOK_APP_SECRET="your-app-secret"
FACEBOOK_CALLBACK_URL="http://localhost:3001/api/v1/auth/facebook/callback"

# Twitter
TWITTER_API_KEY="your-api-key"
TWITTER_API_SECRET="your-api-secret"
TWITTER_ACCESS_TOKEN="your-access-token"
TWITTER_ACCESS_SECRET="your-access-secret"
TWITTER_BEARER_TOKEN="your-bearer-token"
TWITTER_CALLBACK_URL="http://localhost:3001/api/v1/auth/twitter/callback"

# Instagram (via Facebook)
INSTAGRAM_APP_ID="your-instagram-app-id"
INSTAGRAM_APP_SECRET="your-instagram-app-secret"

# TikTok
TIKTOK_CLIENT_KEY="your-client-key"
TIKTOK_CLIENT_SECRET="your-client-secret"

# SendGrid
SENDGRID_API_KEY="your-sendgrid-api-key"
SENDGRID_FROM_EMAIL="noreply@yourdomain.com"
SENDGRID_FROM_NAME="Social Automation Platform"

# Sentry
SENTRY_DSN="your-sentry-dsn"

# Rate Limiting
RATE_LIMIT_WINDOW_MS=900000
RATE_LIMIT_MAX_REQUESTS=100

# CORS
CORS_ORIGIN="http://localhost:3000"

# File Upload
MAX_FILE_SIZE=10485760
ALLOWED_FILE_TYPES="image/jpeg,image/png,image/gif,video/mp4"

# Cloudinary (for media storage)
CLOUDINARY_CLOUD_NAME="your-cloud-name"
CLOUDINARY_API_KEY="your-api-key"
CLOUDINARY_API_SECRET="your-api-secret"
```

6. **Docker Setup:**
```yaml
# docker-compose.yml
version: '3.8'

services:
  postgres:
    image: postgres:15-alpine
    container_name: social_automation_db
    environment:
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
      POSTGRES_DB: social_automation
    ports:
      - "5432:5432"
    volumes:
      - postgres_data:/var/lib/postgresql/data
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U user"]
      interval: 10s
      timeout: 5s
      retries: 5

  redis:
    image: redis:7-alpine
    container_name: social_automation_redis
    ports:
      - "6379:6379"
    volumes:
      - redis_data:/data
    command: redis-server --appendonly yes
    healthcheck:
      test: ["CMD", "redis-cli", "ping"]
      interval: 10s
      timeout: 3s
      retries: 5

  backend:
    build:
      context: ./backend
      dockerfile: Dockerfile
    container_name: social_automation_backend
    ports:
      - "3001:3001"
    environment:
      - NODE_ENV=development
      - DATABASE_URL=postgresql://user:password@postgres:5432/social_automation?schema=public
      - REDIS_URL=redis://redis:6379
    depends_on:
      postgres:
        condition: service_healthy
      redis:
        condition: service_healthy
    volumes:
      - ./backend:/app
      - /app/node_modules
    command: npm run dev

  worker:
    build:
      context: ./backend
      dockerfile: Dockerfile
    container_name: social_automation_worker
    environment:
      - NODE_ENV=development
      - DATABASE_URL=postgresql://user:password@postgres:5432/social_automation?schema=public
      - REDIS_URL=redis://redis:6379
    depends_on:
      postgres:
        condition: service_healthy
      redis:
        condition: service_healthy
    volumes:
      - ./backend:/app
      - /app/node_modules
    command: npm run worker

  frontend:
    build:
      context: ./frontend
      dockerfile: Dockerfile
    container_name: social_automation_frontend
    ports:
      - "3000:3000"
    environment:
      - NEXT_PUBLIC_API_URL=http://localhost:3001/api/v1
    volumes:
      - ./frontend:/app
      - /app/node_modules
      - /app/.next
    command: npm run dev

volumes:
  postgres_data:
  redis_data:
```

7. **Initialize Database:**
```bash
# Generate Prisma client
npx prisma generate

# Create migration
npx prisma migrate dev --name init

# Seed database (optional)
npx prisma db seed
```

---

### **DAY 2: Core Backend Implementation (10-12 hours)**

**Morning Session (5-6 hours):**

1. **Express Server Setup:**
```typescript
// src/server.ts
import express, { Application, Request, Response, NextFunction } from 'express';
import cors from 'cors';
import helmet from 'helmet';
import compression from 'compression';
import morgan from 'morgan';
import { PrismaClient } from '@prisma/client';
import { createBullBoard } from '@bull-board/api';
import { BullAdapter } from '@bull-board/api/bullAdapter';
import { ExpressAdapter } from '@bull-board/express';

import authRoutes from './routes/auth.routes';
import campaignRoutes from './routes/campaign.routes';
import socialAccountRoutes from './routes/socialAccount.routes';
import postRoutes from './routes/post.routes';
import analyticsRoutes from './routes/analytics.routes';
import webhookRoutes from './routes/webhook.routes';

import { errorHandler } from './middleware/errorHandler';
import { rateLimiter } from './middleware/rateLimiter';
import { authenticate } from './middleware/authenticate';
import { logger } from './utils/logger';
import { campaignQueue, postQueue, analyticsQueue } from './queue';

const app: Application = express();
const prisma = new PrismaClient();

// Security middleware
app.use(helmet());
app.use(cors({
  origin: process.env.CORS_ORIGIN?.split(',') || '*',
  credentials: true
}));

// Body parsing
app.use(express.json({ limit: '10mb' }));
app.use(express.urlencoded({ extended: true, limit: '10mb' }));

// Compression
app.use(compression());

// Logging
app.use(morgan('combined', {
  stream: { write: (message) => logger.info(message.trim()) }
}));

// Rate limiting
app.use('/api', rateLimiter);

// Bull Board (Queue monitoring dashboard)
const serverAdapter = new ExpressAdapter();
serverAdapter.setBasePath('/admin/queues');
createBullBoard({
  queues: [
    new BullAdapter(campaignQueue),
    new BullAdapter(postQueue),
    new BullAdapter(analyticsQueue)
  ],
  serverAdapter
});
app.use('/admin/queues', authenticate, serverAdapter.getRouter());

// Health check
app.get('/health', (req: Request, res: Response) => {
  res.json({ status: 'ok', timestamp: new Date().toISOString() });
});

// API routes
const API_VERSION = process.env.API_VERSION || 'v1';
app.use(`/api/${API_VERSION}/auth`, authRoutes);
app.use(`/api/${API_VERSION}/campaigns`, authenticate, campaignRoutes);
app.use(`/api/${API_VERSION}/social-accounts`, authenticate, socialAccountRoutes);
app.use(`/api/${API_VERSION}/posts`, authenticate, postRoutes);
app.use(`/api/${API_VERSION}/analytics`, authenticate, analyticsRoutes);
app.use(`/api/${API_VERSION}/webhooks`, webhookRoutes);

// 404 handler
app.use((req: Request, res: Response) => {
  res.status(404).json({ error: 'Route not found' });
});

// Error handler
app.use(errorHandler);

const PORT = process.env.PORT || 3001;

app.listen(PORT, () => {
  logger.info(`Server running on port ${PORT}`);
  logger.info(`Environment: ${process.env.NODE_ENV}`);
  logger.info(`Queue dashboard: http://localhost:${PORT}/admin/queues`);
});

export default app;
```

2. **Authentication System:**
```typescript
// src/controllers/auth.controller.ts
import { Request, Response, NextFunction } from 'express';
import bcrypt from 'bcryptjs';
import jwt from 'jsonwebtoken';
import { PrismaClient } from '@prisma/client';
import { sendVerificationEmail } from '../services/email.service';
import { logger } from '../utils/logger';

const prisma = new PrismaClient();

export const register = async (req: Request, res: Response, next: NextFunction) => {
  try {
    const { email, password, firstName, lastName, company } = req.body;

    // Check if user exists
    const existingUser = await prisma.user.findUnique({ where: { email } });
    if (existingUser) {
      return res.status(400).json({ error: 'User already exists' });
    }

    // Hash password
    const passwordHash = await bcrypt.hash(password, 12);

    // Create user
    const user = await prisma.user.create({
      data: {
        email,
        passwordHash,
        firstName,
        lastName,
        company
      }
    });

    // Send verification email
    await sendVerificationEmail(user.email, user.id);

    // Generate tokens
    const accessToken = jwt.sign(
      { userId: user.id, email: user.email, role: user.role },
      process.env.JWT_SECRET!,
      { expiresIn: process.env.JWT_EXPIRES_IN }
    );

    const refreshToken = jwt.sign(
      { userId: user.id },
      process.env.REFRESH_TOKEN_SECRET!,
      { expiresIn: process.env.REFRESH_TOKEN_EXPIRES_IN }
    );

    // Log audit
    await prisma.auditLog.create({
      data: {
        userId: user.id,
        action: 'USER_REGISTERED',
        resource: 'USER',
        resourceId: user.id,
        ipAddress: req.ip || 'unknown',
        userAgent: req.get('user-agent')
      }
    });

    res.status(201).json({
      user: {
        id: user.id,
        email: user.email,
        firstName: user.firstName,
        lastName: user.lastName,
        role: user.role
      },
      accessToken,
      refreshToken
    });
  } catch (error) {
    next(error);
  }
};

export const login = async (req: Request, res: Response, next: NextFunction) => {
  try {
    const { email, password } = req.body;

    // Find user
    const user = await prisma.user.findUnique({ where: { email } });
    if (!user) {
      return res.status(401).json({ error: 'Invalid credentials' });
    }

    // Verify password
    const isValidPassword = await bcrypt.compare(password, user.passwordHash);
    if (!isValidPassword) {
      return res.status(401).json({ error: 'Invalid credentials' });
    }

    // Generate tokens
    const accessToken = jwt.sign(
      { userId: user.id, email: user.email, role: user.role },
      process.env.JWT_SECRET!,
      { expiresIn: process.env.JWT_EXPIRES_IN }
    );

    const refreshToken = jwt.sign(
      { userId: user.id },
      process.env.REFRESH_TOKEN_SECRET!,
      { expiresIn: process.env.REFRESH_TOKEN_EXPIRES_IN }
    );

    // Log audit
    await prisma.auditLog.create({
      data: {
        userId: user.id,
        action: 'USER_LOGIN',
        resource: 'USER',
        resourceId: user.id,
        ipAddress: req.ip || 'unknown',
        userAgent: req.get('user-agent')
      }
    });

    res.json({
      user: {
        id: user.id,
        email: user.email,
        firstName: user.firstName,
        lastName: user.lastName,
        role: user.role
      },
      accessToken,
      refreshToken
    });
  } catch (error) {
    next(error);
  }
};
```

**Afternoon Session (5-6 hours):**

3. **Campaign Management:**
```typescript
// src/controllers/campaign.controller.ts
import { Request, Response, NextFunction } from 'express';
import { PrismaClient, CampaignStatus, Platform } from '@prisma/client';
import { campaignQueue } from '../queue';
import { validateCampaign } from '../validators/campaign.validator';

const prisma = new PrismaClient();

export const createCampaign = async (req: Request, res: Response, next: NextFunction) => {
  try {
    const userId = req.user!.userId;
    const { name, description, platforms, posts, scheduledAt } = req.body;

    // Validate input
    const validation = validateCampaign(req.body);
    if (!validation.isValid) {
      return res.status(400).json({ errors: validation.errors });
    }

    // Check user has connected accounts for selected platforms
    const socialAccounts = await prisma.socialAccount.findMany({
      where: {
        userId,
        platform: { in: platforms },
        isActive: true
      }
    });

    const connectedPlatforms = socialAccounts.map(acc => acc.platform);
    const missingPlatforms = platforms.filter((p: Platform) => !connectedPlatforms.includes(p));
    
    if (missingPlatforms.length > 0) {
      return res.status(400).json({
        error: `Please connect accounts for: ${missingPlatforms.join(', ')}`
      });
    }

    // Create campaign
    const campaign = await prisma.campaign.create({
      data: {
        userId,
        name,
        description,
        platforms,
        status: scheduledAt ? CampaignStatus.SCHEDULED : CampaignStatus.DRAFT,
        scheduledAt: scheduledAt ? new Date(scheduledAt) : null,
        totalPosts: posts.length * platforms.length
      }
    });

    // Create posts for each platform
    for (const platform of platforms) {
      const account = socialAccounts.find(acc => acc.platform === platform);
      if (!account) continue;

      for (const postData of posts) {
        await prisma.post.create({
          data: {
            campaignId: campaign.id,
            socialAccountId: account.id,
            content: postData.content,
            mediaUrls: postData.mediaUrls || [],
            hashtags: postData.hashtags || [],
            mentions: postData.mentions || [],
            scheduledFor: scheduledAt ? new Date(scheduledAt) : null,
            status: 'PENDING'
          }
        });
      }
    }

    // Queue campaign if scheduled
    if (scheduledAt) {
      const delay = new Date(scheduledAt).getTime() - Date.now();
      await campaignQueue.add(
        'process-campaign',
        { campaignId: campaign.id },
        { delay: Math.max(0, delay), attempts: 3, backoff: { type: 'exponential', delay: 5000 } }
      );
    }

    // Log audit
    await prisma.auditLog.create({
      data: {
        userId,
        action: 'CAMPAIGN_CREATED',
        resource: 'CAMPAIGN',
        resourceId: campaign.id,
        ipAddress: req.ip || 'unknown',
        metadata: { platforms, totalPosts: campaign.totalPosts }
      }
    });

    res.status(201).json(campaign);
  } catch (error) {
    next(error);
  }
};

export const getCampaigns = async (req: Request, res: Response, next: NextFunction) => {
  try {
    const userId = req.user!.userId;
    const { status, page = 1, limit = 20 } = req.query;

    const where: any = { userId };
    if (status) where.status = status;

    const [campaigns, total] = await Promise.all([
      prisma.campaign.findMany({
        where,
        include: {
          posts: {
            select: {
              id: true,
              status: true,
              socialAccount: {
                select: { platform: true }
              }
            }
          }
        },
        orderBy: { createdAt: 'desc' },
        skip: (Number(page) - 1) * Number(limit),
        take: Number(limit)
      }),
      prisma.campaign.count({ where })
    ]);

    res.json({
      campaigns,
      pagination: {
        page: Number(page),
        limit: Number(limit),
        total,
        pages: Math.ceil(total / Number(limit))
      }
    });
  } catch (error) {
    next(error);
  }
};
```

---

### **DAY 3: Platform Integrations (12-14 hours)**

This is the most critical day. You'll implement API integrations for each social media platform.

**Facebook/Instagram Integration:**
```typescript
// src/services/facebook.service.ts
import axios from 'axios';
import FormData from 'form-data';
import { logger } from '../utils/logger';

export class FacebookService {
  private baseUrl = 'https://graph.facebook.com/v18.0';

  async postToPage(pageId: string, accessToken: string, content: string, mediaUrls: string[] = []) {
    try {
      let endpoint = `${this.baseUrl}/${pageId}`;
      const params: any = {
        access_token: accessToken,
        message: content
      };

      if (mediaUrls.length > 0) {
        // Post with photo
        endpoint += '/photos';
        params.url = mediaUrls[0];
      } else {
        // Text-only post
        endpoint += '/feed';
      }

      const response = await axios.post(endpoint, params);
      return { success: true, postId: response.data.id };
    } catch (error: any) {
      logger.error('Facebook post error:', error.response?.data || error.message);
      throw new Error(error.response?.data?.error?.message || 'Failed to post to Facebook');
    }
  }

  async postToInstagram(instagramAccountId: string, accessToken: string, content: string, imageUrl: string) {
    try {
      // Step 1: Create media container
      const containerResponse = await axios.post(
        `${this.baseUrl}/${instagramAccountId}/media`,
        {
          image_url: imageUrl,
          caption: content,
          access_token: accessToken
        }
      );

      const creationId = containerResponse.data.id;

      // Step 2: Publish media
      const publishResponse = await axios.post(
        `${this.baseUrl}/${instagramAccountId}/media_publish`,
        {
          creation_id: creationId,
          access_token: accessToken
        }
      );

      return { success: true, postId: publishResponse.data.id };
    } catch (error: any) {
      logger.error('Instagram post error:', error.response?.data || error.message);
      throw new Error(error.response?.data?.error?.message || 'Failed to post to Instagram');
    }
  }

  async sendMessage(recipientId: string, pageAccessToken: string, message: string) {
    try {
      // Note: This only works within 24-hour window or with message tags
      const response = await axios.post(
        `${this.baseUrl}/me/messages`,
        {
          recipient: { id: recipientId },
          message: { text: message },
          access_token: pageAccessToken
        }
      );

      return { success: true, messageId: response.data.message_id };
    } catch (error: any) {
      logger.error('Facebook message error:', error.response?.data || error.message);
      throw new Error(error.response?.data?.error?.message || 'Failed to send message');
    }
  }

  async getPageInsights(pageId: string, accessToken: string, metrics: string[] = ['page_impressions', 'page_engaged_users']) {
    try {
      const response = await axios.get(
        `${this.baseUrl}/${pageId}/insights`,
        {
          params: {
            metric: metrics.join(','),
            period: 'day',
            access_token: accessToken
          }
        }
      );

      return response.data.data;
    } catch (error: any) {
      logger.error('Facebook insights error:', error.response?.data || error.message);
      throw new Error('Failed to fetch insights');
    }
  }
}
```

**Twitter/X Integration:**
```typescript
// src/services/twitter.service.ts
import { TwitterApi } from 'twitter-api-v2';
import { logger } from '../utils/logger';
import axios from 'axios';
import fs from 'fs';
import path from 'path';

export class TwitterService {
  private client: TwitterApi;

  constructor(credentials: {
    appKey: string;
    appSecret: string;
    accessToken: string;
    accessSecret: string;
  }) {
    this.client = new TwitterApi(credentials);
  }

  async postTweet(text: string, mediaUrls: string[] = []) {
    try {
      let mediaIds: string[] = [];

      // Upload media if provided
      if (mediaUrls.length > 0) {
        for (const url of mediaUrls) {
          // Download media temporarily
          const tempPath = await this.downloadMedia(url);
          
          // Upload to Twitter
          const mediaId = await this.client.v1.uploadMedia(tempPath);
          mediaIds.push(mediaId);
          
          // Clean up temp file
          fs.unlinkSync(tempPath);
        }
      }

      // Post tweet
      const tweet = await this.client.v2.tweet({
        text,
        ...(mediaIds.length > 0 && { media: { media_ids: mediaIds } })
      });

      return { success: true, tweetId: tweet.data.id };
    } catch (error: any) {
      logger.error('Twitter post error:', error);
      throw new Error(error.message || 'Failed to post tweet');
    }
  }

  async sendDirectMessage(recipientId: string, text: string) {
    try {
      const message = await this.client.v1.sendDm({
        recipient_id: recipientId,
        text
      });

      return { success: true, messageId: message.id_str };
    } catch (error: any) {
      logger.error('Twitter DM error:', error);
      throw new Error('Failed to send direct message');
    }
  }

  async getTweetMetrics(tweetId: string) {
    try {
      const tweet = await this.client.v2.singleTweet(tweetId, {
        'tweet.fields': ['public_metrics', 'created_at']
      });

      return tweet.data.public_metrics;
    } catch (error: any) {
      logger.error('Twitter metrics error:', error);
      throw new Error('Failed to fetch tweet metrics');
    }
  }

  private async downloadMedia(url: string): Promise<string> {
    const response = await axios.get(url, { responseType: 'stream' });
    const tempPath = path.join('/tmp', `media_${Date.now()}_${Math.random().toString(36).substr(2, 9)}`);
    const writer = fs.createWriteStream(tempPath);
    
    response.data.pipe(writer);

    return new Promise((resolve, reject) => {
      writer.on('finish', () => resolve(tempPath));
      writer.on('error', reject);
    });
  }
}
```

**LinkedIn Integration:**
```typescript
// src/services/linkedin.service.ts
import axios from 'axios';
import { logger } from '../utils/logger';

export class LinkedInService {
  private baseUrl = 'https://api.linkedin.com/v2';

  async postToProfile(personUrn: string, accessToken: string, content: string, mediaUrls: string[] = []) {
    try {
      const postData: any = {
        author: personUrn,
        lifecycleState: 'PUBLISHED',
        specificContent: {
          'com.linkedin.ugc.ShareContent': {
            shareCommentary: {
              text: content
            },
            shareMediaCategory: mediaUrls.length > 0 ? 'IMAGE' : 'NONE'
          }
        },
        visibility: {
          'com.linkedin.ugc.MemberNetworkVisibility': 'PUBLIC'
        }
      };

      if (mediaUrls.length > 0) {
        // Upload media first
        const mediaAssets = await this.uploadMedia(personUrn, accessToken, mediaUrls);
        postData.specificContent['com.linkedin.ugc.ShareContent'].media = mediaAssets;
      }

      const response = await axios.post(
        `${this.baseUrl}/ugcPosts`,
        postData,
        {
          headers: {
            'Authorization': `Bearer ${accessToken}`,
            'Content-Type': 'application/json',
            'X-Restli-Protocol-Version': '2.0.0'
          }
        }
      );

      return { success: true, postId: response.data.id };
    } catch (error: any) {
      logger.error('LinkedIn post error:', error.response?.data || error.message);
      throw new Error('Failed to post to LinkedIn');
    }
  }

  private async uploadMedia(personUrn: string, accessToken: string, mediaUrls: string[]) {
    const media = [];

    for (const url of mediaUrls) {
      // Register upload
      const registerResponse = await axios.post(
        `${this.baseUrl}/assets?action=registerUpload`,
        {
          registerUploadRequest: {
            recipes: ['urn:li:digitalmediaRecipe:feedshare-image'],
            owner: personUrn,
            serviceRelationships: [{
              relationshipType: 'OWNER',
              identifier: 'urn:li:userGeneratedContent'
            }]
          }
        },
        {
          headers: {
            'Authorization': `Bearer ${accessToken}`,
            'Content-Type': 'application/json'
          }
        }
      );

      const uploadUrl = registerResponse.data.value.uploadMechanism['com.linkedin.digitalmedia.uploading.MediaUploadHttpRequest'].uploadUrl;
      const asset = registerResponse.data.value.asset;

      // Download and upload image
      const imageResponse = await axios.get(url, { responseType: 'arraybuffer' });
      await axios.put(uploadUrl, imageResponse.data, {
        headers: { 'Content-Type': 'application/octet-stream' }
      });

      media.push({
        status: 'READY',
        description: {
          text: 'Image'
        },
        media: asset,
        title: {
          text: 'Image'
        }
      });
    }

    return media;
  }
}
```

---

I've provided an extremely comprehensive start to your 7-day plan. This response is already quite lengthy, covering:

- **Pre-Day 1:** Complete prerequisites, account setup, and tool installation
- **Day 1:** Full project architecture, database schema, Docker configuration
- **Day 2:** Core backend with authentication, campaign management, and audit logging
- **Day 3:** Platform integrations for Facebook, Instagram, Twitter, and LinkedIn

**Would you like me to continue with:**
- Days 4-7 (Queue workers, frontend implementation, deployment)?
- More platform integrations (TikTok, Pinterest, Telegram)?
- Advanced features (analytics, webhooks, rate limiting)?
- Security and compliance implementations?
- Testing strategies and CI/CD pipelines?

......................................................................


Here’s an expanded, ready-to-use library of natural-language prompts—now longer, richer, and still easy to drop into an assistant, tracker, or CI bot. Each entry has a clear title, intent, constraints, and expected outputs. It mirrors your dashboard’s phases and adds deep, practical detail, including optional configs, thresholds, and failure behaviors.

## 🧭 Context & Overview
Think of this as your prompt playbook for a low‑RAM “right‑hand dashboard.” The prompts below request complete commands, sample configs, CI snippets, and triage tips—organized to run fast on modest runners while keeping signal high. Here’s a quick breakdown of what’s inside:
- Setup/orchestration, strict gates for major languages, supply‑chain security, IaC/K8s, API governance, frontend/E2E/perf, load/monitoring, ultra‑light retrieval, in‑cluster extras, CI wiring, power combos, low‑RAM tactics, and a no‑credentials pack.

---

## 🔧 Setup & Orchestration Prompts

- Title: Right‑Hand Dashboard: Low‑RAM Detection Plan
  Prompt: “Design a full, low‑RAM, high‑signal detection plan for a multi‑service web app. Sequence: run static checks locally and in CI on every PR → run E2E and perf smoke → scan secrets/dependencies/images/IaC → lint APIs and K8s manifests → ship with monitors and uptime checks. Constrain concurrency to safe defaults (2–4), enforce strict timeouts (HTTP 5s), cache outputs, and produce compact reports. Provide exact commands, example configs, and exit‑code policy.”

- Title: Minimal CI Wiring for Fast Feedback
  Prompt: “Propose a CI matrix that fails fast: stage 1 runs language linters and type checks; stage 2 runs security scanners; stage 3 runs Playwright smoke and Lighthouse CI budgets; stage 4 runs k6 quick load and aggregates reports. Include artifact retention, cache usage, timeouts, per‑job RAM estimates, and a ‘retry once with trace’ policy.”

- Title: Upgrade‑Safe Tool Pinning Strategy
  Prompt: “Define how to pin tool versions (npm, pip, go) and manage ‘tool upgrade PRs’ monthly. Include a changelog diff checklist, a small canary pipeline, and how to snapshot baselines for noisy tools so upgrades don’t break PRs unexpectedly.”

- Title: Repo Bootstrap Script (All Platforms)
  Prompt: “Generate a cross‑platform bootstrap script (bash + fallback PowerShell) that installs core CLI tools (Ruff, mypy, Gitleaks, Trivy, Checkov, ShellCheck, kube‑linter, Spectral, Playwright, k6, LHCI), creates default config files, sets sensible defaults (budgets, thresholds), and prints a ‘next steps’ summary.”

---

## 🧹 Language Linters & Type Checkers

- Title: JS/TS Strict Gate with ESLint + TypeScript
  Prompt: “Create ESLint flat config integrating typescript‑eslint for type‑aware rules, plus tsc --noEmit in CI. Enforce --max-warnings=0 and pre‑push hooks. Include: eslint.config.js sample with sensible defaults (no unused vars, no implicit any via TS), tsconfig.json tuned for incremental builds, and recommended ignore patterns for monorepos. Add a 60–120s CI time budget.”

- Title: Python Lint/Format + Types: Ruff + mypy
  Prompt: “Provide a pyproject.toml that enables Ruff check + format (Black-compatible), common rule selections, and mypy in strict mode with gradual opt‑in. Include types-requests stub example, dmypy acceleration, and a 2‑step CI target that fails on any Ruff error or mypy type error. Add a migration note for Flake8/Black/isort users.”

- Title: Monorepo Guardrails (Polyglot)
  Prompt: “Specify a monorepo guard where JS/TS, Python, and Go subprojects each run language‑appropriate linters and type checkers. Include root‑level Makefile targets (lint, type, test), per‑language cache directories, and dependency graph awareness to avoid running unrelated checks on small PRs.”

- Title: IDE + Pre-commit Integration
  Prompt: “Produce pre-commit hooks for Ruff, ESLint, and ShellCheck; VS Code settings to run format on save; and a minimal contributor guide explaining how to run checks locally exactly as CI would.”

---

## 🔐 Secrets, Dependencies, Images, IaC

- Title: Secrets Scan with Gitleaks (Local + PR Hooks)
  Prompt: “Set up Gitleaks with detect in CI and protect via pre-commit locally. Include rules for baseline generation, JSON report path, exit codes, and a short guide for triaging violations (rotate secret, purge history if needed, rebaseline). Provide an example .gitleaks.toml tuned to reduce false positives.”

- Title: Trivy for Filesystem and Image CVEs
  Prompt: “Provide Trivy commands to scan the filesystem and images using --severity HIGH,CRITICAL and --ignore-unfixed. Include SBOM generation, guidance on database caching for faster runs, and a ‘triage notebook’: how to decide between upgrade, pin, or ignore with expiration.”

- Title: Checkov IaC Misconfig Gate
  Prompt: “Generate a Checkov command with --framework terraform,kubernetes and --quiet. Include a sample .checkov.yml enabling/ignoring specific policies (e.g., disallow public S3, enforce encryption at rest). Provide notes for environment variable injection and local module resolution.”

- Title: Unified Supply‑Chain Script (Fail on Real Risk)
  Prompt: “Compose a single bash script that runs Gitleaks, Trivy fs/image, and Checkov. Filter noise with severity and allowlists, aggregate findings to a compact JSON summary, and exit non‑zero only on high‑confidence items. Print a markdown table summary for CI annotations.”

- Title: License Policy Check (Optional)
  Prompt: “Add a lightweight license scanner step compatible with Node and Python, enforce an allowlist (e.g., MIT, Apache-2.0, BSD), and fail on GPL‑3.0 unless explicitly whitelisted.”

---

## 🐚 Shell/Docker/Config Linters

- Title: ShellCheck Sweep for All .sh Files
  Prompt: “Create a robust command to find and lint all shell scripts safely (find … -print0 | xargs -0 shellcheck). Provide .shellcheckrc defaults (SC2006/2086 rules), guidance for generated scripts, and how to suppress per‑line with a justification.”

- Title: Dockerfile Best Practices with Hadolint
  Prompt: “Provide hadolint commands for local advisory mode (--no-fail) and CI strict mode. Include ignore patterns for multi‑stage false positives, and a minimal Dockerfile best‑practice checklist (non‑root user, pinned digest, no curl | sh).”

- Title: YAML Hygiene with yamllint
  Prompt: “Offer a relaxed yamllint config to start, then show a stricter variant for mature repos. Include folder-specific overrides (e.g., Helm templates) and explain the trade‑off between style strictness and developer velocity.”

---

## ☸️ Kubernetes & Deployment Manifests

- Title: Kube‑linter for K8s/Helm Readiness
  Prompt: “Set up kube‑linter to check for privileged/root containers, image tag pinning, missing readiness/liveness probes, resource requests/limits, and forbidden hostPath. Include a custom checks profile JSON/YAML and helm chart linting example.”

- Title: kubeconform Schema Validation
  Prompt: “Provide kubeconform -strict -summary -ignore-missing-schemas for a repo with CRDs. Include a step to pre‑cache schemas, offline mode tips, and how to handle vendor CRDs with local schema bundles.”

- Title: Double‑Gate: Schema + Best‑Practice
  Prompt: “Combine kubeconform and kube‑linter into a single CI stage with parallel execution, artifacts (JSON + text), and a short ‘fix-it’ guide per common failure (add probes, set runAsNonRoot, pin image digest).”

- Title: Helm Chart Sanity Pack
  Prompt: “Add commands to render Helm templates with helm template and validate with kubeconform + kube‑linter. Provide values schemas, and a checklist for safe defaults.”

---

## 📜 API Specs & JSON/YAML Governance

- Title: Spectral Ruleset for OpenAPI Linting
  Prompt: “Write a .spectral.yaml extending spectral:oas with extra rules for auth headers, error response shapes, versioning in path, and no nullable primitives. Add spectral lint openapi.yaml commands, output to JSON, and CI fail thresholds.”

- Title: Redocly CLI for Validate + Bundle
  Prompt: “Provide redocly lint and redocly bundle examples, include redocly.yaml with style presets, explain when to treat Redocly as source‑of‑truth vs. Spectral, and add a publishing step to docs hosting.”

- Title: Contract Fuzz with Schemathesis
  Prompt: “Configure schemathesis run http://localhost:8000/openapi.json with sensible timeouts, flakiness reduction, data generation constraints, and JUnit output for CI. Include a triage guide for flaky endpoints.”

- Title: Consumer Contract Tests (Pact)
  Prompt: “Outline a minimal Pact setup for consumer‑driven contracts, show a single pact test example, and integrate verification in CI with optional broker.”

---

## 🧪 Frontend Errors, A11y, SEO, Performance

- Title: Lighthouse CI Budget Gate
  Prompt: “Set up LHCI with a lighthouserc that asserts performance, accessibility, best practices, and SEO thresholds; run multiple iterations and use median scoring. Include a note on stable CPU/network throttling in CI and storing HTML reports.”

- Title: Playwright Smoke with Traces on First Retry
  Prompt: “Create a Playwright config to run smoke tests headless, record traces/screenshots only on the first retry, and collect HTML reporters as artifacts. Include selectors best practices to avoid brittle tests.”

- Title: Playwright + axe‑core A11y Checks
  Prompt: “Embed axe-core checks into Playwright tests, fail on serious violations, and log WCAG rule IDs to help fix issues. Include a focused ‘critical routes’ suite for fast PR feedback.”

- Title: Console Error Gate
  Prompt: “Add a Playwright test that fails on uncaught console errors or network 4xx/5xx in critical flows. Provide an allowlist for known noisy third-party SDKs.”

---

## 🚦 Performance & Reliability

- Title: k6 Load Profiles (Spike + Soak)
  Prompt: “Author a minimal k6 script with a spike profile (ramp to N users, short duration) and a brief soak (stable RPS). Add thresholds on p95 latency and error rate that fail CI if exceeded. Include lightweight output for artifacts.”

- Title: Prometheus Bootstrap for p95 & Errors
  Prompt: “Provide an example prometheus.yml that scrapes /metrics, defines recording rules for p95 latency, and alerts for elevated error rates. Include local retention tips and a note on pairing with Uptime Kuma for simple uptime checks.”

- Title: Budgeted Performance Guard
  Prompt: “Combine k6 quick test + LHCI budgets + a tiny SLO gate (p95 under X ms, error rate < Y%) in one job. Print an aggregated summary with pass/fail, deltas vs. previous.”

---

## 🌐 Ultra‑Light Retrieval & Build Checks

- Title: Fast HTTP Verifiers with httpx + aiolimiter
  Prompt: “Write an async Python utility using httpx with 5s timeouts, small concurrency (4), polite retries, and a user agent string. Include graceful backoff, follow_redirects, and a small structured log for failures.”

- Title: Clean Extraction with Trafilatura
  Prompt: “Extend the fetcher to run Trafilatura.extract on HTML; if extraction fails, store raw text and mark as ‘needs JS rendering’. Provide a fallback path with a short-circuit for non‑HTML content types.”

- Title: Disk‑Backed Cache with diskcache
  Prompt: “Wrap fetch/extract steps with diskcache TTL caching, stampede control, and a simple size limit (evict LRU). Include advice on cache location on CI runners and how to persist across workflows.”

- Title: Token Budgeting with tiktoken
  Prompt: “Add a helper that counts tokens for model-specific encodings and clips contexts to 75% of max. Provide a micro‑API: tokenize(text), clip(text), and budget_remaining(history).”

- Title: Link Checker (lychee)
  Prompt: “Integrate lychee to scan Markdown and site output for broken links with retries and rate limits; fail only on true dead links and print a compact report.”

---

## 🧰 Kubernetes/Image Runtime (Optional)

- Title: Trivy‑Operator In‑Cluster Scans
  Prompt: “Document installing Trivy‑Operator via Helm or kubectl apply. Explain RBAC needs, namespace‑scoped reports, how to read vulnerabilities via kubectl, and how to route findings to CI or a dashboard. Add guardrails for cluster resource usage.”

- Title: Admission Control Preview (Policy as Code)
  Prompt: “Sketch a preview path using kube‑linter/checkov locally and Kyverno/OPA Gatekeeper policies for cluster admission. Provide a test harness to validate policies without impacting production.”

---

## 🔗 Minimal CI Wiring Examples

- Title: JS/TS Strict on PRs
  Prompt: “Produce a GitHub Actions job that installs eslint, typescript, @typescript-eslint/*, runs npx eslint . --max-warnings=0 and npx tsc --noEmit, caches node_modules, and stores JSON/HTML reports. Include a 3–5 minute time budget.”

- Title: Python: Ruff + mypy in CI
  Prompt: “Generate a job installing Ruff and mypy from a lock file, running ruff check . && ruff format --check and mypy src/. Fail on any error and upload artifacts. Add caching for pip and mypy .mypy_cache.”

- Title: Supply‑Chain Gates in CI
  Prompt: “Create a CI job that runs gitleaks detect -v --report json, trivy fs . --severity HIGH,CRITICAL --ignore-unfixed, trivy image app:latest with filters, and checkov -d . --quiet. Aggregate to a summary.json and annotate the PR.”

- Title: K8s & API Spec Lint on PR
  Prompt: “Add a job that runs kube‑linter lint manifests/ and spectral lint openapi.yaml. Fail on high‑severity findings, upload reports, and print a short ‘how to fix’ guide per rule.”

- Title: E2E, Perf, and Monitors
  Prompt: “Define Playwright smoke with traces on retry, LHCI with stable throttling, and a short k6 profile. Upload all artifacts and a one‑page summary markdown to the PR.”

- Title: Nightly Deep Scan
  Prompt: “Schedule a nightly workflow that expands k6 duration, runs Schemathesis fuzzing, and performs full Trivy image scans. Post results to a dashboard and open issues automatically for new HIGH/CRITICAL items.”

---

## ⚡ Powerful Combinations

- Title: JS/TS ‘Strict Gate’ Combo
  Prompt: “Compose a PR gate: ESLint (flat) + tsc --noEmit + Playwright smoke + LHCI budgets. Set budgets (Perf ≥ 90, A11y ≥ 90), fail on any TypeScript error, and persist HTML reports.”

- Title: Python ‘Bug Net’ Combo
  Prompt: “Combine Ruff check/format + mypy strict + pytest -q. Add pytest-faulthandler, coverage thresholds (≥ 80%), and a ‘rerun failed with verbose logs’ fallback.”

- Title: Secure Supply Chain Combo
  Prompt: “Chain Trivy fs/image + Checkov + Gitleaks pre‑commit + kube‑linter. Fail only on HIGH/CRITICAL with justification needed to bypass, and maintain an allowlist with expiration dates.”

- Title: API Governance Combo
  Prompt: “Pair Spectral rules + Redocly bundle + Schemathesis property tests to enforce design consistency and contract fidelity. Output a compact CI dashboard (counts, severities, links to lines).”

- Title: Ops Guardrail Combo
  Prompt: “Implement k6 SLO thresholds + Prometheus alerts on p95 and error rates + Playwright trace on UI failure. Provide runbooks for common incidents.”

- Title: Editor‑to‑CI Happy Path
  Prompt: “Describe the flow: local pre‑commit (Ruff/ESLint/ShellCheck) → PR linters and types → PR smoke/perf budgets → nightly deep scans. Include a cheat sheet for common failures.”

---

## 🪄 Low‑RAM & High‑Signal Tactics

- Title: Noise Control & Baselines
  Prompt: “Explain how to create baselines/allowlists for Gitleaks, Trivy, and Checkov; treat them as guardrails against regressions; and rotate entries with expiry. Include ‘first run’ guidance to prevent blocking developers.”

- Title: Concurrency, Timeouts, and Caching
  Prompt: “Set per‑tool concurrency caps (e.g., httpx 4), strict timeouts (HTTP 5s, CLI 3–5m), and caching for package managers and scanner DBs. Recommend runner sizes and parallelization strategies without memory spikes.”

- Title: Run Order for Fast Fail
  Prompt: “Define execution order: static linters and type checks first; then security scans; then E2E/perf smoke; deep fuzz/load tests as nightly. Provide rationale and expected time per stage.”

- Title: Artifact Hygiene and Triage
  Prompt: “Standardize report formats (JSON, JUnit, HTML), store them predictably, and generate a single markdown summary with counts, highest severity, and links to reports. Add triage labels and SLA guidance.”

- Title: Version Drift Protection
  Prompt: “Recommend lockfiles, Renovate/Dependabot policies, and a small ‘tools bump’ CI to detect rule changes. Keep a ‘compat map’ documenting tool interdependencies.”

---

## 🧪 “No Credentials” Only

- Title: Offline‑First Detector Pack
  Prompt: “Assemble a no‑credentials kit: Gitleaks, Trivy fs/image, Checkov, ShellCheck, Spectral, Kube‑linter, Ruff, mypy, Lighthouse CLI, Playwright smoke, and k6. Provide copy‑paste commands, minimal configs, and a 10–15 minute full run budget on a standard CI runner.”

- Title: One‑Shot Local Scan Script
  Prompt: “Generate a single bash script that runs: Ruff, mypy, Gitleaks, Trivy fs/image, ShellCheck, Spectral, Checkov, Kube‑linter, LHCI (against a local build or static artifact), Playwright smoke, and k6. Keep concurrency small, enforce strict timeouts, cache outputs, and print a colorized summary with non‑zero exit on high‑confidence findings.”

- Title: CI‑Free Personal Guard
  Prompt: “Create a developer‑local script that mirrors CI checks with lighter defaults and quick feedback (<5 minutes). Include a ‘–fix’ mode where tools can autofix (Ruff/ESLint/Prettier).”

---

## 📋 Deep-Dive Prompt Variants (Extra Detail)

- Title: Stable Budget Design for LHCI
  Prompt: “Propose Lighthouse budgets per route type: home (Perf ≥ 90, LCP ≤ 2.5s), product page (Perf ≥ 85, CLS ≤ 0.1), dashboard (Perf ≥ 80, TBT ≤ 300ms). Add throttling settings, retries, and acceptance criteria for noisy CI.”

- Title: Playwright Locator Strategy
  Prompt: “Recommend resilient locator strategies (role-based, test IDs), guard against flaky network calls, and provide a template for capturing HAR traces only on failure.”

- Title: Schemathesis Data Strategy
  Prompt: “Define data constraints for Schemathesis to reduce false positives: input ranges, auth headers, allowed methods. Include handling for rate limits and retries.”

- Title: Trivy SBOM Workflow
  Prompt: “Generate SBOMs (CycloneDX/SPDX), cache vulnerability DBs, annotate CVEs with fixed versions, and gate only when fixed versions are available unless risk-accepted with expiry.”

- Title: Checkov Policy Tiers
  Prompt: “Group policies by severity (blocker vs. warn). Provide a path to escalate warns to blockers over time, with examples for S3, IAM, EKS, and GKE.”

- Title: Kube‑linter Custom Profile
  Prompt: “Create a custom profile aligning to your org baselines (non-root, readOnlyRootFilesystem, disallow :latest, required probes, envFrom secrets restrictions), and show how to apply it repo‑wide.”

- Title: Gitleaks Rollout Plan
  Prompt: “Describe a staged rollout: detect‑only in week 1 to build a baseline, then warn‑only for new leaks, then block merges on new leaks by week 3. Include comms and remediation steps.”

- Title: Python Type Adoption Plan
  Prompt: “Outline a three‑phase plan to adopt mypy strict: enable on leaf modules, add stubs for third‑party libs, escalate checks to core modules, and fail on regressions after coverage passes 80% of code paths.”

- Title: Accessibly‑First Frontend Gate
  Prompt: “Draft a targeted a11y gate for critical flows (login, checkout, dashboard): axe‑core in Playwright, color contrast checks, keyboard navigation tests, and a budget for critical violations = 0.”

- Title: Incident‑to‑Fix Loop
  Prompt: “Define how production errors (Sentry/GlitchTip), Prometheus alerts, and CI failures map to issues, labels, and owners. Provide SLAs and a ‘first triage’ template.”

---

## 🧭 Synthesis & How to Apply
- Start with the Offline‑First Detector Pack to establish a reliable baseline without credentials or accounts.
- Add strict language gates (Ruff/mypy for Python; ESLint/tsc for TS) to catch bugs before tests even run.
- Layer supply‑chain and IaC checks to prevent security regressions from landing in main.
- Introduce frontend smoke and LHCI budgets to prevent user‑visible regressions, then add k6/Prometheus for runtime assurance.
- Use the power combos for a one‑button “green bar” across syntax, types, security, runtime, and performance, all within low‑RAM budgets.

If you want, I can generate a ready-to-run “one-shot local scan” script and a set of default config files for immediate use.

////////////////////////////////////////////////////////////////////////////////////
4
# **Complete Guide: Expected Issues & Solutions for Social Media Automation Platform**

---

## **1. AUTHENTICATION & API ACCESS ISSUES**

### **Issue 1.1: Facebook/Instagram API Access Denied**

**Problem:**
```
Error: (#200) Provide valid app ID
Error: This endpoint requires the 'pages_manage_posts' permission
Error: App Not Set Up: This app is still in development mode
```

**Root Causes:**
- App not approved for production
- Missing required permissions
- Business verification not completed
- App in Development Mode

**Solutions:**

**Step 1: Complete Business Verification**
```bash
# Required documents:
1. Business registration certificate
2. Tax ID/EIN
3. Business website with privacy policy
4. Physical business address
5. Business email (not personal Gmail)
```

**Step 2: Request Advanced Access**
```javascript
// Navigate to: Facebook Developer Console > App Review > Permissions and Features

Required Permissions:
✅ pages_read_engagement (Standard Access)
✅ pages_manage_posts (Advanced Access - requires review)
✅ pages_read_user_content (Advanced Access)
✅ instagram_basic (Standard Access)
✅ instagram_content_publish (Advanced Access - requires review)

// Submit for review with:
- Video demonstration of your app
- Step-by-step usage instructions
- Privacy policy URL
- Terms of service URL
```

**Step 3: Handle Development Mode Restrictions**
```typescript
// During development, add test users
interface FacebookConfig {
  appId: string;
  appSecret: string;
  isDevelopment: boolean;
  testUsers: string[]; // Facebook User IDs
}

async function validateUser(userId: string, config: FacebookConfig) {
  if (config.isDevelopment) {
    if (!config.testUsers.includes(userId)) {
      throw new Error(
        'User not authorized. Add them as a test user in Facebook App Dashboard.'
      );
    }
  }
  return true;
}
```

**Workaround for Testing:**
```typescript
// Use Facebook Test Users
async function createTestUser() {
  const response = await axios.post(
    `https://graph.facebook.com/v18.0/${APP_ID}/accounts/test-users`,
    {
      installed: true,
      permissions: 'pages_manage_posts,instagram_content_publish',
      access_token: `${APP_ID}|${APP_SECRET}`
    }
  );
  
  return response.data; // { id, access_token, login_url }
}
```

---

### **Issue 1.2: Twitter API Rate Limits Exceeded**

**Problem:**
```
Error: Rate limit exceeded. Please wait 15 minutes.
Error: 429 Too Many Requests
```

**Rate Limits:**
```
Free Tier:
- 1,500 tweets/month
- 50 tweets/day
- 300 requests/15 minutes

Basic ($100/month):
- 3,000 tweets/month
- 100 tweets/day

Pro ($5,000/month):
- 10,000 tweets/month
- 300 tweets/day
```

**Solutions:**

**Solution 1: Implement Rate Limit Tracking**
```typescript
import { RateLimiterRedis } from 'rate-limiter-flexible';
import Redis from 'ioredis';

const redis = new Redis(process.env.REDIS_URL);

// Track Twitter API calls
const twitterRateLimiter = new RateLimiterRedis({
  storeClient: redis,
  keyPrefix: 'twitter_api',
  points: 300, // Number of requests
  duration: 15 * 60, // Per 15 minutes
  blockDuration: 15 * 60 // Block for 15 minutes if exceeded
});

async function callTwitterAPI(endpoint: string, data: any) {
  try {
    // Consume 1 point
    await twitterRateLimiter.consume('api_calls');
    
    // Make API call
    const response = await twitterClient.post(endpoint, data);
    return response;
    
  } catch (rateLimitError) {
    if (rateLimitError instanceof Error) {
      // Rate limit exceeded
      const retryAfter = Math.ceil(rateLimitError.msBeforeNext / 1000);
      
      throw new Error(
        `Twitter rate limit exceeded. Retry after ${retryAfter} seconds.`
      );
    }
    throw rateLimitError;
  }
}
```

**Solution 2: Queue with Exponential Backoff**
```typescript
import { Queue } from 'bullmq';

const twitterQueue = new Queue('twitter-posts', {
  connection: redis,
  defaultJobOptions: {
    attempts: 5,
    backoff: {
      type: 'exponential',
      delay: 60000 // Start with 1 minute
    },
    removeOnComplete: 100,
    removeOnFail: 50
  }
});

// Add rate limiting to queue
twitterQueue.on('error', async (error) => {
  if (error.message.includes('429')) {
    // Pause queue for 15 minutes
    await twitterQueue.pause();
    
    setTimeout(async () => {
      await twitterQueue.resume();
      console.log('Twitter queue resumed');
    }, 15 * 60 * 1000);
  }
});
```

**Solution 3: Distribute Across Multiple Accounts**
```typescript
interface TwitterAccount {
  id: string;
  credentials: TwitterCredentials;
  dailyPostCount: number;
  lastResetDate: Date;
}

class TwitterAccountPool {
  private accounts: TwitterAccount[] = [];
  
  async getAvailableAccount(): Promise<TwitterAccount> {
    // Reset daily counters
    const today = new Date().toDateString();
    this.accounts.forEach(acc => {
      if (acc.lastResetDate.toDateString() !== today) {
        acc.dailyPostCount = 0;
        acc.lastResetDate = new Date();
      }
    });
    
    // Find account with capacity
    const available = this.accounts.find(acc => acc.dailyPostCount < 50);
    
    if (!available) {
      throw new Error('All Twitter accounts at daily limit');
    }
    
    available.dailyPostCount++;
    return available;
  }
}
```

---

### **Issue 1.3: Instagram API Doesn't Support Personal Accounts**

**Problem:**
```
Error: Instagram API only works with Business or Creator accounts
Error: Invalid Instagram Business Account
```

**Solution:**

**Step 1: Convert to Business Account**
```typescript
// Guide users through conversion process
const conversionSteps = [
  '1. Open Instagram app',
  '2. Go to Settings > Account',
  '3. Tap "Switch to Professional Account"',
  '4. Choose "Business" or "Creator"',
  '5. Connect to Facebook Page',
  '6. Complete business information'
];

// Verify account type
async function verifyInstagramAccount(accessToken: string) {
  const response = await axios.get(
    'https://graph.facebook.com/v18.0/me/accounts',
    { params: { access_token: accessToken } }
  );
  
  const pages = response.data.data;
  
  for (const page of pages) {
    // Check if page has Instagram account
    const igResponse = await axios.get(
      `https://graph.facebook.com/v18.0/${page.id}`,
      {
        params: {
          fields: 'instagram_business_account',
          access_token: page.access_token
        }
      }
    );
    
    if (igResponse.data.instagram_business_account) {
      return {
        pageId: page.id,
        instagramAccountId: igResponse.data.instagram_business_account.id,
        accessToken: page.access_token
      };
    }
  }
  
  throw new Error('No Instagram Business Account found. Please convert your account.');
}
```

**Alternative: Use Unofficial API (Risky)**
```typescript
// ⚠️ WARNING: Against Instagram TOS, high ban risk
import { IgApiClient } from 'instagram-private-api';

const ig = new IgApiClient();

// Login with username/password
await ig.account.login(username, password);

// Post photo (unofficial method)
await ig.publish.photo({
  file: imageBuffer,
  caption: 'Hello world!'
});

// ⚠️ Risks:
// - Account ban
// - IP block
// - Legal issues
// - No support
```

---

## **2. CONTENT POSTING ISSUES**

### **Issue 2.1: Media Upload Failures**

**Problem:**
```
Error: Image file size exceeds limit
Error: Unsupported media format
Error: Failed to download media from URL
Error: Image dimensions not supported
```

**Platform Requirements:**
```javascript
const PLATFORM_MEDIA_REQUIREMENTS = {
  FACEBOOK: {
    image: {
      formats: ['jpg', 'png', 'gif'],
      maxSize: 4 * 1024 * 1024, // 4MB
      minDimensions: { width: 600, height: 600 },
      maxDimensions: { width: 8192, height: 8192 },
      aspectRatio: { min: 1/1.91, max: 1.91/1 }
    },
    video: {
      formats: ['mp4', 'mov'],
      maxSize: 1024 * 1024 * 1024, // 1GB
      maxDuration: 240 * 60, // 240 minutes
      minDimensions: { width: 600, height: 600 }
    }
  },
  INSTAGRAM: {
    image: {
      formats: ['jpg', 'png'],
      maxSize: 8 * 1024 * 1024, // 8MB
      minDimensions: { width: 320, height: 320 },
      maxDimensions: { width: 1440, height: 1800 },
      aspectRatio: { min: 4/5, max: 1.91/1 }
    },
    video: {
      formats: ['mp4'],
      maxSize: 100 * 1024 * 1024, // 100MB
      maxDuration: 60, // 60 seconds (Feed), 15 minutes (IGTV)
      minDimensions: { width: 600, height: 600 }
    }
  },
  TWITTER: {
    image: {
      formats: ['jpg', 'png', 'gif', 'webp'],
      maxSize: 5 * 1024 * 1024, // 5MB
      maxImages: 4
    },
    video: {
      formats: ['mp4', 'mov'],
      maxSize: 512 * 1024 * 1024, // 512MB
      maxDuration: 140 // 140 seconds
    }
  },
  LINKEDIN: {
    image: {
      formats: ['jpg', 'png', 'gif'],
      maxSize: 10 * 1024 * 1024, // 10MB
      maxImages: 9
    },
    video: {
      formats: ['mp4'],
      maxSize: 5 * 1024 * 1024 * 1024, // 5GB
      maxDuration: 10 * 60 // 10 minutes
    }
  }
};
```

**Solution: Media Validation & Processing**
```typescript
import sharp from 'sharp';
import ffmpeg from 'fluent-ffmpeg';
import axios from 'axios';

class MediaProcessor {
  async validateAndProcessImage(
    imageUrl: string,
    platform: Platform
  ): Promise<Buffer> {
    const requirements = PLATFORM_MEDIA_REQUIREMENTS[platform].image;
    
    // Download image
    const response = await axios.get(imageUrl, {
      responseType: 'arraybuffer',
      timeout: 30000,
      maxContentLength: requirements.maxSize * 2 // Allow some overhead
    });
    
    let imageBuffer = Buffer.from(response.data);
    
    // Get metadata
    const metadata = await sharp(imageBuffer).metadata();
    
    // Validate format
    if (!requirements.formats.includes(metadata.format!)) {
      // Convert to JPEG
      imageBuffer = await sharp(imageBuffer)
        .jpeg({ quality: 90 })
        .toBuffer();
    }
    
    // Validate dimensions
    const { width = 0, height = 0 } = metadata;
    
    if (width < requirements.minDimensions.width || 
        height < requirements.minDimensions.height) {
      throw new Error(
        `Image too small. Minimum: ${requirements.minDimensions.width}x${requirements.minDimensions.height}`
      );
    }
    
    // Resize if too large
    if (width > requirements.maxDimensions.width || 
        height > requirements.maxDimensions.height) {
      imageBuffer = await sharp(imageBuffer)
        .resize(
          requirements.maxDimensions.width,
          requirements.maxDimensions.height,
          { fit: 'inside', withoutEnlargement: true }
        )
        .toBuffer();
    }
    
    // Validate aspect ratio (Instagram specific)
    if (platform === 'INSTAGRAM') {
      const aspectRatio = width / height;
      const { min, max } = requirements.aspectRatio;
      
      if (aspectRatio < min || aspectRatio > max) {
        // Crop to fit
        const targetRatio = (min + max) / 2;
        const targetWidth = Math.min(width, height * targetRatio);
        const targetHeight = targetWidth / targetRatio;
        
        imageBuffer = await sharp(imageBuffer)
          .resize(Math.round(targetWidth), Math.round(targetHeight), {
            fit: 'cover',
            position: 'center'
          })
          .toBuffer();
      }
    }
    
    // Compress if still too large
    const currentSize = imageBuffer.length;
    if (currentSize > requirements.maxSize) {
      const quality = Math.floor((requirements.maxSize / currentSize) * 90);
      
      imageBuffer = await sharp(imageBuffer)
        .jpeg({ quality: Math.max(quality, 60) })
        .toBuffer();
      
      // If still too large, resize further
      if (imageBuffer.length > requirements.maxSize) {
        const scaleFactor = Math.sqrt(requirements.maxSize / imageBuffer.length);
        const newMetadata = await sharp(imageBuffer).metadata();
        
        imageBuffer = await sharp(imageBuffer)
          .resize(
            Math.floor((newMetadata.width || 1000) * scaleFactor),
            Math.floor((newMetadata.height || 1000) * scaleFactor)
          )
          .jpeg({ quality: 80 })
          .toBuffer();
      }
    }
    
    return imageBuffer;
  }
  
  async validateAndProcessVideo(
    videoUrl: string,
    platform: Platform
  ): Promise<string> {
    const requirements = PLATFORM_MEDIA_REQUIREMENTS[platform].video;
    const tempPath = `/tmp/video_${Date.now()}.mp4`;
    const outputPath = `/tmp/processed_${Date.now()}.mp4`;
    
    // Download video
    const response = await axios.get(videoUrl, {
      responseType: 'stream',
      timeout: 60000
    });
    
    const writer = fs.createWriteStream(tempPath);
    response.data.pipe(writer);
    
    await new Promise((resolve, reject) => {
      writer.on('finish', resolve);
      writer.on('error', reject);
    });
    
    // Get video metadata
    const metadata = await this.getVideoMetadata(tempPath);
    
    // Validate duration
    if (metadata.duration > requirements.maxDuration) {
      throw new Error(
        `Video too long. Maximum: ${requirements.maxDuration} seconds`
      );
    }
    
    // Validate size
    const stats = fs.statSync(tempPath);
    let needsProcessing = stats.size > requirements.maxSize;
    
    // Validate format
    if (!requirements.formats.includes(metadata.format)) {
      needsProcessing = true;
    }
    
    if (needsProcessing) {
      // Process video
      await this.compressVideo(tempPath, outputPath, requirements);
      fs.unlinkSync(tempPath);
      return outputPath;
    }
    
    return tempPath;
  }
  
  private async getVideoMetadata(filePath: string): Promise<any> {
    return new Promise((resolve, reject) => {
      ffmpeg.ffprobe(filePath, (err, metadata) => {
        if (err) reject(err);
        else resolve({
          duration: metadata.format.duration,
          format: metadata.format.format_name,
          width: metadata.streams[0].width,
          height: metadata.streams[0].height
        });
      });
    });
  }
  
  private async compressVideo(
    inputPath: string,
    outputPath: string,
    requirements: any
  ): Promise<void> {
    return new Promise((resolve, reject) => {
      ffmpeg(inputPath)
        .outputOptions([
          '-c:v libx264',
          '-preset medium',
          '-crf 23',
          '-c:a aac',
          '-b:a 128k',
          '-movflags +faststart'
        ])
        .output(outputPath)
        .on('end', () => resolve())
        .on('error', (err) => reject(err))
        .run();
    });
  }
}
```

**Usage:**
```typescript
const processor = new MediaProcessor();

try {
  const processedImage = await processor.validateAndProcessImage(
    'https://example.com/image.jpg',
    'INSTAGRAM'
  );
  
  // Upload to Cloudflare R2 or S3
  const imageUrl = await uploadToStorage(processedImage);
  
  // Post to Instagram
  await instagramService.post(imageUrl, caption);
  
} catch (error) {
  console.error('Media processing failed:', error.message);
  // Notify user about specific issue
}
```

---

### **Issue 2.2: Character Limit Violations**

**Problem:**
```
Error: Tweet text is too long
Error: Caption exceeds maximum length
```

**Platform Limits:**
```javascript
const CHARACTER_LIMITS = {
  TWITTER: {
    text: 280,
    withMedia: 280,
    withLink: 280 - 23 // Links count as 23 chars
  },
  FACEBOOK: {
    post: 63206,
    comment: 8000
  },
  INSTAGRAM: {
    caption: 2200,
    comment: 2200,
    bio: 150
  },
  LINKEDIN: {
    post: 3000,
    comment: 1250
  },
  TIKTOK: {
    caption: 150
  }
};
```

**Solution: Smart Text Truncation**
```typescript
class TextOptimizer {
  truncateForPlatform(text: string, platform: Platform): string {
    const limit = CHARACTER_LIMITS[platform];
    
    if (text.length <= limit) {
      return text;
    }
    
    // Intelligent truncation
    const truncated = text.substring(0, limit - 3); // Reserve 3 chars for "..."
    
    // Find last complete word
    const lastSpace = truncated.lastIndexOf(' ');
    const result = truncated.substring(0, lastSpace) + '...';
    
    return result;
  }
  
  // Split long content into thread (Twitter)
  splitIntoThread(text: string, limit: number = 280): string[] {
    const words = text.split(' ');
    const tweets: string[] = [];
    let currentTweet = '';
    let tweetNumber = 1;
    
    for (const word of words) {
      const threadIndicator = `(${tweetNumber}/?)`;
      const testTweet = currentTweet + (currentTweet ? ' ' : '') + word;
      
      if (testTweet.length + threadIndicator.length > limit) {
        tweets.push(currentTweet);
        currentTweet = word;
        tweetNumber++;
      } else {
        currentTweet = testTweet;
      }
    }
    
    if (currentTweet) {
      tweets.push(currentTweet);
    }
    
    // Add thread indicators
    const totalTweets = tweets.length;
    return tweets.map((tweet, index) => 
      `${tweet} (${index + 1}/${totalTweets})`
    );
  }
  
  // Extract and shorten URLs
  shortenUrls(text: string): string {
    const urlRegex = /(https?:\/\/[^\s]+)/g;
    
    return text.replace(urlRegex, (url) => {
      // Use URL shortener service
      return this.shortenUrl(url);
    });
  }
  
  private async shortenUrl(longUrl: string): Promise<string> {
    // Use TinyURL, Bitly, or custom shortener
    try {
      const response = await axios.post('https://api.tinyurl.com/create', {
        url: longUrl,
        domain: 'tinyurl.com'
      }, {
        headers: {
          'Authorization': `Bearer ${process.env.TINYURL_API_KEY}`
        }
      });
      
      return response.data.data.tiny_url;
    } catch (error) {
      // Fallback to original URL
      return longUrl;
    }
  }
}
```

---

### **Issue 2.3: Duplicate Content Detection**

**Problem:**
```
Error: Status is a duplicate
Error: This content has already been posted
```

**Solution: Content Fingerprinting**
```typescript
import crypto from 'crypto';

class DuplicateDetector {
  async checkDuplicate(
    content: string,
    platform: Platform,
    userId: string
  ): Promise<boolean> {
    // Generate content hash
    const contentHash = crypto
      .createHash('sha256')
      .update(content.toLowerCase().trim())
      .digest('hex');
    
    // Check in database
    const existing = await prisma.post.findFirst({
      where: {
        userId,
        platform,
        contentHash,
        createdAt: {
          gte: new Date(Date.now() - 24 * 60 * 60 * 1000) // Last 24 hours
        }
      }
    });
    
    return !!existing;
  }
  
  // Add variation to avoid duplicates
  addVariation(content: string): string {
    const variations = [
      (text: string) => `${text} 🚀`,
      (text: string) => `${text} ✨`,
      (text: string) => `${text}\n\n#${new Date().getTime()}`,
      (text: string) => text.replace(/\.$/, '!'),
      (text: string) => `📢 ${text}`
    ];
    
    const randomVariation = variations[Math.floor(Math.random() * variations.length)];
    return randomVariation(content);
  }
  
  // Calculate similarity between two texts
  calculateSimilarity(text1: string, text2: string): number {
    const words1 = new Set(text1.toLowerCase().split(/\s+/));
    const words2 = new Set(text2.toLowerCase().split(/\s+/));
    
    const intersection = new Set([...words1].filter(x => words2.has(x)));
    const union = new Set([...words1, ...words2]);
    
    return intersection.size / union.size; // Jaccard similarity
  }
}
```

---

## **3. QUEUE & SCHEDULING ISSUES**

### **Issue 3.1: Jobs Getting Stuck**

**Problem:**
```
Jobs remain in "active" state forever
Queue stops processing
Worker crashes without completing jobs
```

**Solution: Implement Job Monitoring**
```typescript
import { Queue, Worker, QueueEvents } from 'bullmq';

const postQueue = new Queue('social-posts', {
  connection: redis,
  defaultJobOptions: {
    attempts: 3,
    backoff: {
      type: 'exponential',
      delay: 5000
    },
    removeOnComplete: {
      age: 24 * 3600, // Keep for 24 hours
      count: 1000 // Keep last 1000 jobs
    },
    removeOnFail: {
      age: 7 * 24 * 3600 // Keep failed jobs for 7 days
    }
  },
  settings: {
    stalledInterval: 30000, // Check for stalled jobs every 30 seconds
    maxStalledCount: 2 // Max times a job can be stalled before failed
  }
});

// Monitor queue events
const queueEvents = new QueueEvents('social-posts', { connection: redis });

queueEvents.on('stalled', ({ jobId }) => {
  console.error(`Job ${jobId} has stalled`);
  
  // Send alert
  sendAlert({
    type: 'JOB_STALLED',
    jobId,
    queue: 'social-posts'
  });
});

queueEvents.on('failed', ({ jobId, failedReason }) => {
  console.error(`Job ${jobId} failed:`, failedReason);
  
  // Log to monitoring service
  logger.error('Job failed', {
    jobId,
    reason: failedReason,
    queue: 'social-posts'
  });
});

// Worker with proper error handling
const worker = new Worker('social-posts', async (job) => {
  const { postId, platform, content } = job.data;
  
  try {
    // Update job progress
    await job.updateProgress(10);
    
    // Get platform service
    const service = getPlatformService(platform);
    
    await job.updateProgress(30);
    
    // Post content
    const result = await service.post(content);
    
    await job.updateProgress(80);
    
    // Update database
    await prisma.post.update({
      where: { id: postId },
      data: {
        status: 'PUBLISHED',
        platformPostId: result.postId,
        publishedAt: new Date()
      }
    });
    
    await job.updateProgress(100);
    
    return { success: true, postId: result.postId };
    
  } catch (error) {
    // Log error details
    logger.error('Post failed', {
      postId,
      platform,
      error: error.message,
      stack: error.stack
    });
    
    // Update database
    await prisma.post.update({
      where: { id: postId },
      data: {
        status: 'FAILED',
        errorMessage: error.message
      }
    });
    
    throw error; // Re-throw for retry logic
  }
}, {
  connection: redis,
  concurrency: 5, // Process 5 jobs simultaneously
  limiter: {
    max: 10, // Max 10 jobs
    duration: 1000 // Per second
  }
});

// Graceful shutdown
process.on('SIGTERM', async () => {
  console.log('Shutting down worker...');
  await worker.close();
  await redis.quit();
  process.exit(0);
});
```

**Health Check Endpoint:**
```typescript
app.get('/health/queues', async (req, res) => {
  const queues = ['social-posts', 'analytics', 'emails'];
  const health: any = {};
  
  for (const queueName of queues) {
    const queue = new Queue(queueName, { connection: redis });
    
    const [waiting, active, completed, failed, delayed] = await Promise.all([
      queue.getWaitingCount(),
      queue.getActiveCount(),
      queue.getCompletedCount(),
      queue.getFailedCount(),
      queue.getDelayedCount()
    ]);
    
    health[queueName] = {
      waiting,
      active,
      completed,
      failed,
      delayed,
      status: active > 100 ? 'WARNING' : 'OK'
    };
  }
  
  res.json(health);
});
```

---

### **Issue 3.2: Scheduled Posts Not Publishing**

**Problem:**
```
Posts scheduled for future not executing
Timezone issues causing wrong publish times
Missed scheduled posts
```

**Solution: Robust Scheduling System**
```typescript
import { addMinutes, isBefore, parseISO } from 'date-fns';
import { zonedTimeToUtc, utcToZonedTime } from 'date-fns-tz';

class SchedulingService {
  async schedulePost(
    postData: any,
    scheduledTime: Date,
    userTimezone: string = 'UTC'
  ) {
    // Convert user timezone to UTC
    const utcTime = zonedTimeToUtc(scheduledTime, userTimezone);
    
    // Validate not in past
    if (isBefore(utcTime, new Date())) {
      throw new Error('Cannot schedule posts in the past');
    }
    
    // Calculate delay
    const delay = utcTime.getTime() - Date.now();
    
    // Create post in database
    const post = await prisma.post.create({
      data: {
        ...postData,
        scheduledFor: utcTime,
        status: 'SCHEDULED',
        timezone: userTimezone
      }
    });
    
    // Add to queue with delay
    const job = await postQueue.add(
      'publish-post',
      { postId: post.id },
      {
        delay,
        jobId: `post_${post.id}`, // Unique job ID prevents duplicates
        attempts: 3,
        backoff: {
          type: 'exponential',
          delay: 60000 // 1 minute
        }
      }
    );
    
    // Store job ID for cancellation
    await prisma.post.update({
      where: { id: post.id },
      data: { queueJobId: job.id }
    });
    
    return post;
  }
  
  async cancelScheduledPost(postId: string) {
    const post = await prisma.post.findUnique({
      where: { id: postId }
    });
    
    if (!post || !post.queueJobId) {
      throw new Error('Post not found or not scheduled');
    }
    
    // Remove from queue
    const job = await postQueue.getJob(post.queueJobId);
    if (job) {
      await job.remove();
    }
    
    // Update database
    await prisma.post.update({
      where: { id: postId },
      data: {
        status: 'CANCELLED',
        queueJobId: null
      }
    });
  }
  
  async reschedulePost(postId: string, newTime: Date, userTimezone: string) {
    // Cancel existing schedule
    await this.cancelScheduledPost(postId);
    
    // Get post data
    const post = await prisma.post.findUnique({
      where: { id: postId }
    });
    
    // Reschedule
    return this.schedulePost(post, newTime, userTimezone);
  }
  
  // Recover missed posts (run on startup)
  async recoverMissedPosts() {
    const missedPosts = await prisma.post.findMany({
      where: {
        status: 'SCHEDULED',
        scheduledFor: {
          lte: addMinutes(new Date(), -5) // Missed by 5+ minutes
        }
      }
    });
    
    console.log(`Found ${missedPosts.length} missed posts`);
    
    for (const post of missedPosts) {
      // Publish immediately
      await postQueue.add(
        'publish-post',
        { postId: post.id },
        { priority: 1 } // High priority
      );
    }
  }
}
```

**Cron Job for Monitoring:**
```typescript
import cron from 'node-cron';

// Check for missed posts every 5 minutes
cron.schedule('*/5 * * * *', async () => {
  const schedulingService = new SchedulingService();
  await schedulingService.recoverMissedPosts();
});

// Clean up old completed jobs daily
cron.schedule('0 2 * * *', async () => {
  await postQueue.clean(24 * 3600 * 1000, 1000, 'completed');
  await postQueue.clean(7 * 24 * 3600 * 1000, 1000, 'failed');
  console.log('Queue cleanup completed');
});
```

---

## **4. DATABASE ISSUES**

### **Issue 4.1: Connection Pool Exhaustion**

**Problem:**
```
Error: Can't reach database server
Error: Connection pool timeout
Error: Too many connections
```

**Solution: Proper Connection Management**
```typescript
import { PrismaClient } from '@prisma/client';

// Singleton pattern
let prisma: PrismaClient;

if (process.env.NODE_ENV === 'production') {
  prisma = new PrismaClient({
    datasources: {
      db: {
        url: process.env.DATABASE_URL
      }
    },
    log: ['error', 'warn'],
    errorFormat: 'minimal'
  });
} else {
  // Prevent multiple instances in development
  if (!(global as any).prisma) {
    (global as any).prisma = new PrismaClient({
      log: ['query', 'error', 'warn'],
      errorFormat: 'pretty'
    });
  }
  prisma = (global as any).prisma;
}

// Connection pool configuration
const DATABASE_URL = new URL(process.env.DATABASE_URL!);
DATABASE_URL.searchParams.set('connection_limit', '10');
DATABASE_URL.searchParams.set('pool_timeout', '20');
DATABASE_URL.searchParams.set('connect_timeout', '10');

export default prisma;

// Graceful shutdown
process.on('beforeExit', async () => {
  await prisma.$disconnect();
});
```

**Supabase Connection Pooling:**
```typescript
// Use Supabase connection pooler for serverless
const connectionString = process.env.DATABASE_URL!.replace(
  ':5432',
  ':6543' // Supabase pooler port
);

const prisma = new PrismaClient({
  datasources: {
    db: { url: connectionString }
  }
});
```

---

### **Issue 4.2: Slow Queries**

**Problem:**
```
Queries taking 5+ seconds
Database CPU at 100%
Timeout errors
```

**Solution: Query Optimization**
```typescript
// Add indexes to schema
model Post {
  id              String   @id @default(uuid())
  userId          String
  platform        Platform
  status          PostStatus
  scheduledFor    DateTime?
  createdAt       DateTime @default(now())
  
  @@index([userId, status]) // Composite index
  @@index([platform, status])
  @@index([scheduledFor])
  @@index([createdAt])
  @@index([userId, createdAt(sort: Desc)]) // Sorted index
}

// Use select to fetch only needed fields
const posts = await prisma.post.findMany({
  where: { userId },
  select: {
    id: true,
    content: true,
    status: true,
    createdAt: true
    // Don't fetch large fields like mediaUrls if not needed
  },
  take: 20,
  orderBy: { createdAt: 'desc' }
});

// Use cursor-based pagination for large datasets
async function getPaginatedPosts(cursor?: string, limit: number = 20) {
  const posts = await prisma.post.findMany({
    take: limit + 1, // Fetch one extra to check if there's more
    ...(cursor && {
      skip: 1,
      cursor: { id: cursor }
    }),
    orderBy: { createdAt: 'desc' }
  });
  
  const hasMore = posts.length > limit;
  const results = hasMore ? posts.slice(0, -1) : posts;
  const nextCursor = hasMore ? results[results.length - 1].id : null;
  
  return { posts: results, nextCursor, hasMore };
}

// Use aggregations instead of fetching all records
const stats = await prisma.post.groupBy({
  by: ['platform', 'status'],
  _count: true,
  where: {
    userId,
    createdAt: {
      gte: new Date(Date.now() - 30 * 24 * 60 * 60 * 1000) // Last 30 days
    }
  }
});
```

**Caching Layer:**
```typescript
import { Redis } from 'ioredis';

const redis = new Redis(process.env.REDIS_URL);

class CachedRepository {
  async getUserCampaigns(userId: string) {
    const cacheKey = `user:${userId}:campaigns`;
    
    // Try cache first
    const cached = await redis.get(cacheKey);
    if (cached) {
      return JSON.parse(cached);
    }
    
    // Fetch from database
    const campaigns = await prisma.campaign.findMany({
      where: { userId },
      include: {
        posts: {
          select: { id: true, status: true }
        }
      }
    });
    
    // Cache for 5 minutes
    await redis.setex(cacheKey, 300, JSON.stringify(campaigns));
    
    return campaigns;
  }
  
  async invalidateUserCache(userId: string) {
    const keys = await redis.keys(`user:${userId}:*`);
    if (keys.length > 0) {
      await redis.del(...keys);
    }
  }
}
```

---

## **5. SECURITY ISSUES**

### **Issue 5.1: API Key Exposure**

**Problem:**
```
API keys committed to Git
Keys exposed in frontend code
Unauthorized API access
```

**Solution: Secure Key Management**
```typescript
// Use environment variables
import dotenv from 'dotenv';
dotenv.config();

// Validate required env vars on startup
const requiredEnvVars = [
  'DATABASE_URL',
  'REDIS_URL',
  'JWT_SECRET',
  'FACEBOOK_APP_SECRET',
  'TWITTER_API_SECRET'
];

for (const envVar of requiredEnvVars) {
  if (!process.env[envVar]) {
    throw new Error(`Missing required environment variable: ${envVar}`);
  }
}

// Encrypt sensitive data in database
import crypto from 'crypto';

class Encryption {
  private algorithm = 'aes-256-gcm';
  private key = Buffer.from(process.env.ENCRYPTION_KEY!, 'hex');
  
  encrypt(text: string): string {
    const iv = crypto.randomBytes(16);
    const cipher = crypto.createCipheriv(this.algorithm, this.key, iv);
    
    let encrypted = cipher.update(text, 'utf8', 'hex');
    encrypted += cipher.final('hex');
    
    const authTag = cipher.getAuthTag();
    
    return `${iv.toString('hex')}:${authTag.toString('hex')}:${encrypted}`;
  }
  
  decrypt(encrypted: string): string {
    const [ivHex, authTagHex, encryptedText] = encrypted.split(':');
    
    const iv = Buffer.from(ivHex, 'hex');
    const authTag = Buffer.from(authTagHex, 'hex');
    const decipher = crypto.createDecipheriv(this.algorithm, this.key, iv);
    
    decipher.setAuthTag(authTag);
    
    let decrypted = decipher.update(encryptedText, 'hex', 'utf8');
    decrypted += decipher.final('utf8');
    
    return decrypted;
  }
}

// Store encrypted tokens
const encryption = new Encryption();

await prisma.socialAccount.create({
  data: {
    userId,
    platform: 'TWITTER',
    accessToken: encryption.encrypt(accessToken),
    refreshToken: encryption.encrypt(refreshToken)
  }
});

// Decrypt when needed
const account = await prisma.socialAccount.findFirst({
  where: { userId, platform: 'TWITTER' }
});

const decryptedToken = encryption.decrypt(account.accessToken);
```

**Rotate API Keys:**
```typescript
class KeyRotation {
  async rotateApiKey(userId: string, keyId: string) {
    // Generate new key
    const newKey = crypto.randomBytes(32).toString('hex');
    const hashedKey = crypto
      .createHash('sha256')
      .update(newKey)
      .digest('hex');
    
    // Update database
    await prisma.apiKey.update({
      where: { id: keyId },
      data: {
        key: hashedKey,
        rotatedAt: new Date()
      }
    });
    
    // Notify user
    await sendEmail(userId, {
      subject: 'API Key Rotated',
      body: `Your API key has been rotated. New key: ${newKey}`
    });
    
    return newKey;
  }
  
  // Auto-rotate keys older than 90 days
  async autoRotateExpiredKeys() {
    const expiredKeys = await prisma.apiKey.findMany({
      where: {
        rotatedAt: {
          lte: new Date(Date.now() - 90 * 24 * 60 * 60 * 1000)
        },
        isActive: true
      }
    });
    
    for (const key of expiredKeys) {
      await this.rotateApiKey(key.userId, key.id);
    }
  }
}
```

---

### **Issue 5.2: Rate Limit Bypass Attempts**

**Problem:**
```
Users trying to bypass rate limits
Multiple accounts from same IP
Distributed attacks
```

**Solution: Multi-Layer Rate Limiting**
```typescript
import { RateLimiterRedis, RateLimiterMemory } from 'rate-limiter-flexible';

// IP-based rate limiting
const ipLimiter = new RateLimiterRedis({
  storeClient: redis,
  keyPrefix: 'rate_limit_ip',
  points: 100, // Requests
  duration: 60, // Per minute
  blockDuration: 60 * 15 // Block for 15 minutes
});

// User-based rate limiting
const userLimiter = new RateLimiterRedis({
  storeClient: redis,
  keyPrefix: 'rate_limit_user',
  points: 1000, // Requests
  duration: 60 * 60, // Per hour
  blockDuration: 60 * 60 // Block for 1 hour
});

// Endpoint-specific limiting
const postCreationLimiter = new RateLimiterRedis({
  storeClient: redis,
  keyPrefix: 'rate_limit_post_creation',
  points: 50, // Posts
  duration: 24 * 60 * 60, // Per day
  blockDuration: 24 * 60 * 60
});

// Middleware
export const rateLimitMiddleware = async (
  req: Request,
  res: Response,
  next: NextFunction
) => {
  const ip = req.ip || req.socket.remoteAddress || 'unknown';
  const userId = req.user?.userId;
  
  try {
    // Check IP rate limit
    await ipLimiter.consume(ip);
    
    // Check user rate limit if authenticated
    if (userId) {
      await userLimiter.consume(userId);
      
      // Check endpoint-specific limits
      if (req.path.includes('/campaigns') && req.method === 'POST') {
        await postCreationLimiter.consume(userId);
      }
    }
    
    next();
    
  } catch (rateLimitError: any) {
    const retryAfter = Math.ceil(rateLimitError.msBeforeNext / 1000);
    
    res.set('Retry-After', String(retryAfter));
    res.status(429).json({
      error: 'Too many requests',
      retryAfter,
      message: `Please wait ${retryAfter} seconds before trying again`
    });
  }
};

// Detect suspicious patterns
class AbuseDetector {
  async detectSuspiciousActivity(userId: string, ip: string) {
    const checks = await Promise.all([
      this.checkMultipleAccounts(ip),
      this.checkRapidRequests(userId),
      this.checkFailedAttempts(userId)
    ]);
    
    const suspicious = checks.some(check => check.isSuspicious);
    
    if (suspicious) {
      await this.flagUser(userId, checks);
    }
    
    return suspicious;
  }
  
  private async checkMultipleAccounts(ip: string) {
    const count = await prisma.user.count({
      where: {
        auditLogs: {
          some: {
            ipAddress: ip,
            createdAt: {
              gte: new Date(Date.now() - 24 * 60 * 60 * 1000)
            }
          }
        }
      }
    });
    
    return {
      isSuspicious: count > 5,
      reason: `${count} accounts from same IP`,
      severity: count > 10 ? 'HIGH' : 'MEDIUM'
    };
  }
  
  private async checkRapidRequests(userId: string) {
    const requestCount = await redis.get(`request_count:${userId}`);
    
    return {
      isSuspicious: Number(requestCount) > 1000,
      reason: `${requestCount} requests in last minute`,
      severity: 'HIGH'
    };
  }
  
  private async flagUser(userId: string, checks: any[]) {
    await prisma.user.update({
      where: { id: userId },
      data: {
        isFlagged: true,
        flagReason: JSON.stringify(checks)
      }
    });
    
    // Send alert to admin
    await sendAdminAlert({
      type: 'SUSPICIOUS_ACTIVITY',
      userId,
      checks
    });
  }
}
```

---

## **6. FRONTEND ISSUES**

### **Issue 6.1: Slow Initial Load**

**Problem:**
```
Large bundle size (5MB+)
Slow Time to Interactive
Poor Lighthouse scores
```

**Solution: Performance Optimization**
```typescript
// next.config.js
module.exports = {
  // Enable SWC compiler
  swcMinify: true,
  
  // Image optimization
  images: {
    domains: ['your-cdn.com', 'cloudflare.com'],
    formats: ['image/avif', 'image/webp'],
    deviceSizes: [640, 750, 828, 1080, 1200, 1920, 2048, 3840],
    minimumCacheTTL: 60
  },
  
  // Code splitting
  experimental: {
    optimizeCss: true,
    modern Build: true
  },
  
  // Webpack optimization
  webpack: (config, { dev, isServer }) => {
    if (!dev && !isServer) {
      // Bundle analyzer
      config.optimization.splitChunks = {
        chunks: 'all',
        cacheGroups: {
          default: false,
          vendors: false,
          // Vendor chunk
          vendor: {
            name: 'vendor',
            chunks: 'all',
            test: /node_modules/,
            priority: 20
          },
          // Common chunk
          common: {
            name: 'common',
            minChunks: 2,
            chunks: 'all',
            priority: 10,
            reuseExistingChunk: true,
            enforce: true
          }
        }
      };
    }
    return config;
  }
};

// Dynamic imports
import dynamic from 'next/dynamic';

const CampaignEditor = dynamic(() => import('@/components/CampaignEditor'), {
  loading: () => <Skeleton />,
  ssr: false // Client-side only
});

const AnalyticsDashboard = dynamic(
  () => import('@/components/AnalyticsDashboard'),
  { ssr: false }
);

// Lazy load images
import Image from 'next/image';

<Image
  src="/campaign-image.jpg"
  alt="Campaign"
  width={800}
  height={600}
  loading="lazy"
  placeholder="blur"
  blurDataURL="data:image/jpeg;base64,..."
/>

// Prefetch critical data
import { useEffect } from 'react';
import { useQueryClient } from '@tanstack/react-query';

function App() {
  const queryClient = useQueryClient();
  
  useEffect(() => {
    // Prefetch user data
    queryClient.prefetchQuery({
      queryKey: ['user'],
      queryFn: fetchUser
    });
    
    // Prefetch campaigns
    queryClient.prefetchQuery({
      queryKey: ['campaigns'],
      queryFn: fetchCampaigns
    });
  }, []);
  
  return <Dashboard />;
}
```

---

### **Issue 6.2: Memory Leaks**

**Problem:**
```
Browser tab crashes after extended use
Memory usage keeps increasing
Slow performance over time
```

**Solution: Proper Cleanup**
```typescript
import { useEffect, useRef } from 'react';

function CampaignMonitor() {
  const intervalRef = useRef<NodeJS.Timeout>();
  const wsRef = useRef<WebSocket>();
  
  useEffect(() => {
    // Setup WebSocket
    const ws = new WebSocket('wss://api.example.com/campaigns');
    wsRef.current = ws;
    
    ws.onmessage = (event) => {
      const data = JSON.parse(event.data);
      updateCampaignStatus(data);
    };
    
    // Setup polling
    intervalRef.current = setInterval(() => {
      fetchCampaignUpdates();
    }, 5000);
    
    // Cleanup function
    return () => {
      // Close WebSocket
      if (wsRef.current) {
        wsRef.current.close();
      }
      
      // Clear interval
      if (intervalRef.current) {
        clearInterval(intervalRef.current);
      }
    };
  }, []);
  
  return <div>...</div>;
}

// Abort fetch requests on unmount
function DataFetcher() {
  useEffect(() => {
    const abortController = new AbortController();
    
    fetch('/api/data', {
      signal: abortController.signal
    })
      .then(res => res.json())
      .then(data => setData(data))
      .catch(err => {
        if (err.name !== 'AbortError') {
          console.error(err);
        }
      });
    
    return () => {
      abortController.abort();
    };
  }, []);
}
```

---

## **7. MONITORING & DEBUGGING**

### **Comprehensive Logging System**

```typescript
import winston from 'winston';
import { Logtail } from '@logtail/node';

const logtail = new Logtail(process.env.LOGTAIL_TOKEN!);

const logger = winston.createLogger({
  level: process.env.LOG_LEVEL || 'info',
  format: winston.format.combine(
    winston.format.timestamp(),
    winston.format.errors({ stack: true }),
    winston.format.json()
  ),
  defaultMeta: {
    service: 'social-automation',
    environment: process.env.NODE_ENV
  },
  transports: [
    // Console
    new winston.transports.Console({
      format: winston.format.combine(
        winston.format.colorize(),
        winston.format.simple()
      )
    }),
    
    // File
    new winston.transports.File({
      filename: 'logs/error.log',
      level: 'error'
    }),
    new winston.transports.File({
      filename: 'logs/combined.log'
    })
  ]
});

// Add Logtail transport
logger.add({
  log(info, callback) {
    setImmediate(() => {
      logtail.log(info.message, info.level, info);
    });
    callback();
  }
} as any);

export default logger;

// Usage
logger.info('Campaign created', {
  userId: '123',
  campaignId: '456',
  platforms: ['TWITTER', 'FACEBOOK']
});

logger.error('Failed to post', {
  error: err.message,
  stack: err.stack,
  postId: '789'
});
```

---

This is an extensive guide covering the most common issues. Would you like me to continue with:
1. **More platform-specific issues** (TikTok, LinkedIn, Pinterest)?
2. **Scaling issues** (handling millions of posts)?
3. **Cost optimization strategies**?
4. **Legal compliance implementation**?
5. **Disaster recovery procedures**?

/////////////////////////////////////////////////////////////////////////
