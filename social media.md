social media.md

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

Please let me know which aspects you'd like me to expand on further!