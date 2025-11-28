prompts index part2:

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

/////////////////////////////////////////////////////////////////////
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

/////////////////////////////////////////////////////////////////////////

### Comprehensive Database Error Collection & Solutions - Extended Natural Language Prompts

---

## **PostgreSQL Database Errors & Comprehensive Solutions**

### **1. Connection Timeout Errors in PostgreSQL**
**Primary Question:** How can I comprehensively diagnose and fix the "Connection Timeout Expired" error in PostgreSQL when my applications cannot connect to the database server?

**Detailed Sub-questions:**
- What are the root causes of connection timeout errors in PostgreSQL, including network issues, server configuration problems, and client-side limitations?
- How do I systematically check the PostgreSQL service status using `systemctl` commands and interpret the output to identify service-related issues?
- What specific timeout parameters should I modify in the `postgresql.conf` file, including `statement_timeout`, `idle_in_transaction_session_timeout`, and their optimal values for different workload scenarios?
- How can I use network diagnostic tools like `telnet` and `nc` (netcat) to verify network connectivity between the client and PostgreSQL server on port 5432?
- What modifications should I make to the `pg_hba.conf` file to properly configure client authentication and access control for different IP ranges and authentication methods?
- What is the correct procedure for restarting the PostgreSQL service after configuration changes, and how can I verify that the changes have been applied successfully?
- How do I troubleshoot connection pool exhaustion issues that might be causing timeout errors in high-traffic applications?

### **2. Disk Space Management Issues in PostgreSQL**
**Primary Question:** What comprehensive steps should I take when PostgreSQL reports "could not extend file: No space left on device" errors, and how can I prevent future disk space issues?

**Detailed Sub-questions:**
- How do I use system commands like `df -h` and `du -sh` to identify disk space usage patterns and locate the largest files in the PostgreSQL data directory?
- What is the procedure for safely moving WAL (Write-Ahead Log) files to a different disk partition to free up space on the primary data disk?
- How can I implement an automated log rotation and cleanup strategy for PostgreSQL log files to prevent them from consuming excessive disk space?
- What are the best practices for using `pg_dump` to archive old tables and data that are no longer actively used but need to be retained for compliance or historical purposes?
- How do I configure PostgreSQL's autovacuum settings to prevent table bloat and efficiently reclaim disk space from deleted rows?
- What monitoring strategies should I implement to receive early warnings about disk space issues before they become critical?
- How can I use table partitioning to manage large tables more effectively and improve disk space utilization?

### **3. Replication Failure Resolution in PostgreSQL**
**Primary Question:** How can I diagnose and resolve complex replication failures in PostgreSQL when the error "database system identifier differs between primary and standby" occurs?

**Detailed Sub-questions:**
- What are the common causes of replication failures in PostgreSQL, including WAL segment issues, network problems, and configuration mismatches?
- How do I perform a fresh base backup using `pg_basebackup` with proper parameters for compression, progress reporting, and checkpoint handling?
- What WAL-related settings in `postgresql.conf` need to be adjusted for reliable replication, including `wal_keep_segments`, `max_wal_senders`, `archive_mode`, and `archive_command`?
- How should I properly configure the `recovery.conf` file (or recovery settings in newer PostgreSQL versions) on standby servers to maintain synchronization with the primary?
- What monitoring queries and tools can I use to track replication lag and identify potential issues before they cause complete replication failure?
- How do I implement cascading replication for multi-tier standby configurations?
- What is the procedure for promoting a standby server to primary in case of primary server failure, and how do I reconfigure the old primary as a new standby?

### **4. Permission and Access Control Issues in PostgreSQL**
**Primary Question:** What is the comprehensive approach to resolving "Permission Denied" errors in PostgreSQL and implementing a robust access control strategy?

**Detailed Sub-questions:**
- How do I use the `GRANT` command to assign specific privileges (CONNECT, USAGE, SELECT, INSERT, UPDATE, DELETE) at different levels (database, schema, table, column)?
- What is the difference between database-level, schema-level, and table-level permissions, and how do they interact in PostgreSQL's permission hierarchy?
- How can I create roles and users with appropriate default privileges that automatically apply to newly created objects?
- What are the best practices for implementing row-level security (RLS) policies to provide fine-grained access control?
- How do I audit and review existing permissions to identify security issues or unnecessary access rights?
- What is the procedure for revoking permissions and ensuring that privilege escalation vulnerabilities are prevented?
- How can I use PostgreSQL's built-in roles and predefined permissions to simplify access management?

---

## **MySQL Database Errors & Advanced Solutions**

### **1. Connection Timeout and Lock Wait Issues in MySQL**
**Primary Question:** How can I comprehensively troubleshoot and resolve various timeout-related errors in MySQL, including connection timeouts and lock wait timeout exceeded errors?

**Detailed Sub-questions:**
- What are the different types of timeout errors in MySQL (connection timeout, wait timeout, interactive timeout, lock wait timeout) and their specific meanings?
- How do I diagnose whether the timeout issue is caused by network problems, server overload, or long-running queries blocking other operations?
- What specific timeout parameters should I configure in the `my.cnf` file, and what are the recommended values for different application scenarios (OLTP vs. OLAP workloads)?
- How can I fix socket connection issues when MySQL reports "Can't connect to local MySQL server through socket" errors?
- What queries should I use to identify and analyze blocking transactions using `SHOW PROCESSLIST` and `INFORMATION_SCHEMA.INNODB_LOCKS` tables?
- How do I implement query timeout mechanisms at the application level to prevent runaway queries from causing system-wide issues?
- What monitoring tools and techniques can help predict and prevent timeout issues before they impact production systems?

### **2. Connection Pool Exhaustion and "Too Many Connections" Errors**
**Primary Question:** What comprehensive strategies should I implement to resolve "Too Many Connections" errors in MySQL and optimize connection management?

**Detailed Sub-questions:**
- How do I calculate the optimal `max_connections` and `max_user_connections` values based on available system resources and expected workload?
- What are the best practices for implementing connection pooling at the application level, including pool size, timeout settings, and connection validation?
- How can I identify and terminate idle or long-running connections that are consuming connection slots unnecessarily?
- What monitoring queries and tools should I use to track connection usage patterns and identify connection leaks in applications?
- How do I implement connection throttling and rate limiting to prevent connection storms during traffic spikes?
- What are the implications of increasing max_connections on MySQL memory usage, and how can I calculate the memory requirements?
- How can I use MySQL proxy solutions or connection poolers like ProxySQL to manage connections more efficiently?

### **3. Disk Space and Temporary Storage Management in MySQL**
**Primary Question:** How do I comprehensively address disk space issues in MySQL, including temporary file management and table optimization?

**Detailed Sub-questions:**
- What are the different types of temporary files created by MySQL, and where are they stored (tmpdir, innodb_tmpdir, slave_load_tmpdir)?
- How can I configure MySQL to use alternative locations for temporary files when the default `/tmp` directory is full?
- What is the procedure for using the `OPTIMIZE TABLE` command to reclaim space from fragmented tables, and when should it be used?
- How do I identify tables with excessive fragmentation or wasted space using INFORMATION_SCHEMA queries?
- What are the best practices for managing binary logs, relay logs, and slow query logs to prevent them from consuming excessive disk space?
- How can I implement automated purging of old binary logs while ensuring replication safety?
- What strategies should I use for partitioning large tables to improve manageability and disk space utilization?

---

## **MongoDB NoSQL Database Errors & Solutions**

### **1. Replica Set and Replication Failures in MongoDB**
**Primary Question:** How can I diagnose and resolve complex replication issues in MongoDB replica sets, including "not master and slaveOk=false" errors?

**Detailed Sub-questions:**
- What are the common causes of replica set failures in MongoDB, including network partitions, oplog size issues, and election problems?
- How do I use `rs.status()` and `rs.config()` commands to diagnose the current state of the replica set and identify problematic members?
- What is the procedure for forcing a primary election using `rs.stepDown()`, and when should this be used?
- How can I reconfigure a replica set using `rs.reconfig()` with the force option to recover from configuration issues?
- What are the steps to resize the oplog using `replSetResizeOplog` when replication lag is caused by insufficient oplog size?
- How do I implement proper read preferences and write concerns to handle replication-related errors gracefully in applications?
- What monitoring metrics should I track to predict and prevent replication issues before they impact availability?

### **2. Memory Management and Performance Issues in MongoDB**
**Primary Question:** How do I resolve memory-related errors in MongoDB, such as "Sort exceeded memory limit" and optimize memory usage for better performance?

**Detailed Sub-questions:**
- What are the different memory consumers in MongoDB (WiredTiger cache, sort operations, aggregation pipelines) and how do they interact?
- How do I create appropriate indexes to support sorting operations and avoid in-memory sort limitations?
- What is the procedure for increasing the sort buffer size using `internalQueryExecMaxBlockingSortBytes` parameter?
- How can I use the `allowDiskUse` option in aggregation pipelines to handle large data processing operations?
- What are the best practices for configuring WiredTiger cache size based on available system memory?
- How do I monitor memory usage patterns using MongoDB's built-in metrics and diagnostic commands?
- What query optimization techniques can reduce memory consumption while maintaining performance?

### **3. Connection Management and Network Issues in MongoDB**
**Primary Question:** How can I troubleshoot and resolve MongoDB connection issues, including timeout errors and connection pool problems?

**Detailed Sub-questions:**
- What are the common causes of "MongoNetworkError: connection timed out" errors, and how do I systematically diagnose them?
- How do I configure MongoDB's network settings in `mongod.conf`, including bindIp, port, and maxIncomingConnections?
- What firewall rules and network security configurations are required for MongoDB clusters to communicate properly?
- How can I implement connection pooling best practices in MongoDB drivers to optimize connection usage?
- What monitoring tools and commands should I use to track active connections and identify connection leaks?
- How do I configure MongoDB for high availability with proper timeout and retry settings?
- What are the implications of different read and write concern levels on connection behavior and error handling?

---

## **Redis In-Memory Database Errors & Solutions**

### **1. Memory Management and OOM (Out of Memory) Issues in Redis**
**Primary Question:** How do I comprehensively address memory issues in Redis when encountering "OOM command not allowed when used memory > 'maxmemory'" errors?

**Detailed Sub-questions:**
- What are the different memory eviction policies in Redis (allkeys-lru, volatile-lru, allkeys-random, etc.) and when should each be used?
- How do I properly configure the `maxmemory` setting based on available system resources and expected data size?
- What monitoring commands and tools should I use to track memory usage patterns and identify memory leaks?
- How can I implement data expiration strategies using TTL (Time To Live) to automatically remove old data?
- What are the trade-offs between different Redis persistence mechanisms (RDB snapshots vs. AOF) in terms of memory usage?
- How do I optimize Redis data structures and encoding to reduce memory footprint?
- What are the best practices for implementing memory-efficient caching strategies in Redis?

### **2. Replication and High Availability Issues in Redis**
**Primary Question:** How can I diagnose and resolve replication issues in Redis when seeing "Master link down, reconnecting..." errors?

**Detailed Sub-questions:**
- What are the common causes of Redis replication failures, including network issues, authentication problems, and configuration mismatches?
- How do I properly configure master-slave replication in Redis using the `replicaof` directive and related settings?
- What monitoring commands like `INFO replication` should I use to track replication status and lag?
- How can I implement Redis Sentinel for automatic failover and high availability?
- What are the best practices for handling split-brain scenarios in Redis clusters?
- How do I configure proper persistence settings to minimize data loss during failover events?
- What network diagnostic tools should I use to troubleshoot connectivity between Redis instances?

---

## **SQLite Embedded Database Errors & Solutions**

### **1. Database Locking and Concurrency Issues in SQLite**
**Primary Question:** How do I resolve "database is locked" errors in SQLite and implement proper concurrency control for multi-user applications?

**Detailed Sub-questions:**
- What are the different locking modes in SQLite, and how do they affect concurrent access?
- How does enabling WAL (Write-Ahead Logging) mode improve concurrency, and what are the configuration options?
- What is the proper way to set busy timeout values to handle temporary lock conflicts gracefully?
- How can I use the `lsof` command and other tools to identify processes holding locks on the database file?
- What are the best practices for transaction management to minimize lock contention?
- How do I implement retry logic in applications to handle transient locking issues?
- What are the limitations of SQLite for concurrent write operations, and when should I consider migrating to a client-server database?

### **2. Database Corruption and Recovery in SQLite**
**Primary Question:** What comprehensive steps should I take to diagnose and recover from SQLite database corruption when encountering "database disk image is malformed" errors?

**Detailed Sub-questions:**
- What are the common causes of SQLite database corruption, including hardware failures, application bugs, and improper shutdown?
- How do I use the `PRAGMA integrity_check` command to diagnose corruption issues and interpret the results?
- What is the step-by-step procedure for recovering data from a corrupted database using the `.dump` command?
- How can I use the `VACUUM` command to rebuild database files and reclaim unused space?
- What preventive measures should I implement to reduce the risk of database corruption?
- How do I implement proper backup strategies for SQLite databases to ensure data recovery capabilities?
- What are the best practices for handling SQLite databases in networked or shared storage environments?

---

## **Comprehensive SSL/TLS Certificate Setup Guide**

### **1. Let's Encrypt SSL Certificate Implementation with Certbot**
**Primary Question:** How do I implement a complete SSL/TLS solution using Let's Encrypt and Certbot, from initial server setup to automatic renewal configuration?

**Detailed Sub-questions on Server Preparation:**
- What are the prerequisite system requirements and dependencies for installing Certbot on different Linux distributions?
- How do I properly update system packages and install snap package manager for Certbot installation?
- What are the differences between installing Certbot via snap, apt, yum, or other package managers, and which method is recommended?
- How do I verify that the web server (Nginx or Apache) is properly installed and configured before requesting certificates?

**Detailed Sub-questions on Domain Configuration:**
- What DNS records (A, AAAA, CNAME) need to be configured before requesting SSL certificates?
- How do I create and configure virtual hosts in Nginx or Apache for the domains that need SSL certificates?
- What are the best practices for organizing website files and directory structures for SSL-enabled sites?
- How can I test domain resolution and ensure proper DNS propagation before certificate generation?

**Detailed Sub-questions on Certificate Acquisition:**
- What are the different Certbot plugins (nginx, apache, standalone, webroot) and when should each be used?
- How do I use Certbot's automatic Nginx configuration versus manual certificate generation?
- What are the rate limits imposed by Let's Encrypt, and how can I avoid hitting them?
- How do I request wildcard certificates for subdomains using DNS validation?
- What troubleshooting steps should I follow if certificate generation fails?

**Detailed Sub-questions on Auto-Renewal Configuration:**
- How do I configure and test automatic certificate renewal using Certbot's built-in timer?
- What are the best practices for setting up cron jobs for certificate renewal as a backup mechanism?
- How can I configure pre and post-renewal hooks to restart services or perform custom actions?
- What monitoring and alerting should I implement to ensure certificates are renewed before expiration?
- How do I handle renewal failures and implement proper error notification systems?

### **2. ZeroSSL Alternative SSL Implementation**
**Primary Question:** How do I implement ZeroSSL as a comprehensive alternative to Let's Encrypt, including account setup, certificate generation, and management?

**Detailed Sub-questions:**
- What are the advantages and limitations of ZeroSSL compared to Let's Encrypt?
- How do I create and configure a ZeroSSL account with API credentials for automated certificate management?
- What is the complete procedure for installing and configuring the acme.sh client for ZeroSSL?
- How do I generate single-domain, multi-domain, and wildcard certificates using ZeroSSL?
- What are the steps for installing ZeroSSL certificates on different web servers (Nginx, Apache, IIS)?
- How do I configure automatic renewal for ZeroSSL certificates using acme.sh?
- What backup and recovery procedures should I implement for ZeroSSL certificates?

### **3. CloudFlare Free SSL/TLS Implementation**
**Primary Question:** How do I leverage CloudFlare's free SSL/TLS services for website security, including both flexible and full SSL modes?

**Detailed Sub-questions:**
- What are the different SSL/TLS modes offered by CloudFlare (Off, Flexible, Full, Full Strict) and their security implications?
- How do I properly migrate domain nameservers to CloudFlare while minimizing downtime?
- What is the procedure for generating and installing CloudFlare Origin Certificates for end-to-end encryption?
- How do I configure Page Rules and SSL/TLS settings for optimal security and performance?
- What are the best practices for handling mixed content issues when enabling SSL through CloudFlare?
- How can I implement additional security features like HSTS, TLS 1.3, and automatic HTTPS rewrites?
- What monitoring and analytics tools does CloudFlare provide for SSL/TLS traffic analysis?

### **4. Universal Nginx SSL/TLS Configuration Best Practices**
**Primary Question:** What is the comprehensive Nginx configuration for implementing secure SSL/TLS with optimal performance and security headers?

**Detailed Sub-questions:**
- How do I configure Nginx to properly redirect all HTTP traffic to HTTPS with proper status codes?
- What are the recommended SSL/TLS protocol versions and cipher suites for maximum security and compatibility?
- How should I implement security headers (HSTS, X-Frame-Options, CSP, etc.) for defense against common attacks?
- What are the best practices for SSL session caching and timeout configuration for performance optimization?
- How do I implement OCSP stapling for improved certificate validation performance?
- What is the proper configuration for HTTP/2 and HTTP/3 support with SSL/TLS?
- How can I implement proper logging and monitoring for SSL/TLS-related events and errors?

### **5. SSL/TLS Testing and Validation Procedures**
**Primary Question:** How do I comprehensively test and validate SSL/TLS configurations to ensure proper implementation and security?

**Detailed Sub-questions:**
- What command-line tools (curl, openssl, nmap) should I use to test SSL/TLS connectivity and certificate details?
- How do I interpret the output from OpenSSL s_client commands for certificate chain validation?
- What online tools (SSL Labs, Observatory, Hardenize) provide comprehensive SSL/TLS security analysis?
- How can I test for common SSL/TLS vulnerabilities (Heartbleed, POODLE, BEAST, etc.)?
- What are the procedures for testing certificate renewal processes without affecting production systems?
- How do I implement automated SSL/TLS monitoring to detect certificate expiration and configuration issues?
- What performance testing should I conduct to ensure SSL/TLS doesn't negatively impact site speed?

---

This extensively detailed prompt list provides comprehensive coverage of all database error scenarios and SSL/TLS setup procedures, with multiple layers of depth for each topic. Each section includes primary questions followed by detailed sub-questions that explore specific technical aspects, troubleshooting procedures, best practices, and preventive measures. This format allows for thorough exploration of each topic while maintaining clear organization and structure.

//////////////////////////////////////////////////////////////////////

### Title: **Detecting No Credentials**

#### Prompt 1: Tools That Require Credentials or Registration  
Provide a thorough explanation of tools that require credentials, accounts, or additional setup to function. For each tool, include its purpose, the type of credentials it requires, and the scenarios in which it is typically used. Examples include:  
- **hCaptcha**: This tool requires a site key and server-side secret, which must be obtained from the hCaptcha dashboard. Explain how these credentials are used for token verification and why hCaptcha is essential for production environments to prevent spam and abuse. However, highlight why it may not be suitable for development environments where quick testing without external dependencies is preferred.  
- **Plausible Cloud Analytics**: This tool requires an account and, in the case of self-hosting, a server setup. Discuss how it provides analytics solutions but requires DNS configuration and at least 2GB of RAM for ClickHouse, making it less ideal for developers who want lightweight, quick solutions.  
- **LiteLLM**: While LiteLLM is a local tool, it requires API keys and sometimes region/project settings to connect to external providers like OpenAI or Anthropic. Explain how these API keys are necessary for routing requests to external models and why this may not be ideal for developers working offline or in environments where credentials cannot be securely stored.  
- **GrowthBook**: This open-source experiment platform allows developers to manage feature flags and experiments but requires the setup of a service (e.g., via Docker Compose) and user sign-in to function. Discuss how this can be useful for production environments but may be overkill for simple projects or early-stage development.  

Conclude by explaining why credentials and accounts are often necessary for these tools, such as ensuring security, enabling advanced features, or tracking usage. Provide examples of when developers should avoid such tools, such as during early development, when working offline, or when prioritizing simplicity and speed.

---

#### Prompt 2: No-Credential Detectors (Install → Run)  
Create an extensive list of tools that require no credentials, accounts, or complex setup. For each tool, provide a detailed explanation of its purpose, installation method, and example command to run it immediately. Examples include:  
- **Gitleaks**: Detects hardcoded secrets in repositories. Explain how it works locally or in CI without requiring any login. Provide the command `gitleaks detect -v` as an example and describe the type of secrets it can find (e.g., API keys, private tokens).  
- **Trivy**: Scans filesystems, dependencies, and container images for vulnerabilities. Provide commands like `trivy fs .` and `trivy image app:latest` to demonstrate its use. Explain how Trivy can be used to identify CVEs (Common Vulnerabilities and Exposures) and misconfigurations in containerized environments.  
- **Checkov**: Scans Infrastructure-as-Code (IaC) for misconfigurations in Terraform, Kubernetes, and other platforms. Provide the command `checkov -d .` and explain how it can identify risks related to security, compliance, and best practices in cloud infrastructure.  
- **ShellCheck**: Performs static analysis for shell scripts to catch quoting, test, and pipe errors. Include the command `shellcheck script.sh` and explain how it helps improve script reliability and portability.  
- **KubeLinter**: Checks Kubernetes and Helm manifests for best practices and common issues. Provide the command `kube-linter lint manifests/` and explain how it ensures Kubernetes configurations follow security and operational guidelines.  
- **Spectral**: Lints OpenAPI, JSON, and YAML files using built-in rulesets. Include the command `spectral lint openapi.yaml`. Explain how Spectral helps developers ensure API specifications are well-formed and compliant with standards.  
- **Bandit**: A Python security linter that catches common vulnerabilities using AST-based analysis. Demonstrate its use with `bandit -r .` and explain how it identifies insecure code patterns, such as the use of `eval` or hardcoded passwords.  
- **Ruff**: A fast Python linter and formatter that works out of the box. Provide commands like `ruff check .` and `ruff format`. Highlight how Ruff combines multiple functionalities (e.g., linting, formatting, and import sorting) into one tool.  
- **mypy**: A Python static type checker that identifies type errors. Include the command `mypy src/` and explain how it ensures type safety in Python projects, reducing runtime errors.  
- **lychee**: Checks for broken links in Markdown, HTML, or websites. Provide the command `lychee README.md` and explain how it can be integrated into CI pipelines to ensure documentation quality.  
- **Semgrep Community Edition**: A static analysis tool with community rules that runs offline. Include the command `semgrep --config=auto` and explain how it provides powerful pattern-based code analysis for multiple languages.  

Explain how these tools are designed for simplicity and efficiency, allowing developers to integrate them into their workflows instantly without worrying about external dependencies or accounts.

---

#### Prompt 3: Minimal “Just Run” Bundles  
Request a detailed explanation of how to combine no-credential tools into efficient workflows for specific use cases. For each workflow, include the tools involved, their purpose, and the commands to execute them together. Examples include:  
- **Local Security Sweep**: Combine Gitleaks, Trivy, and Checkov to check for hardcoded secrets, vulnerabilities, and IaC misconfigurations. Provide a command like:  
  ```bash
  gitleaks detect -v && trivy fs . && checkov -d .
  ```  
  Explain how this workflow ensures that codebases are free from sensitive information, high-severity vulnerabilities, and misconfigured infrastructure.  
- **Scripts and Containers**: Use ShellCheck and KubeLinter to analyze shell scripts and Kubernetes manifests. Provide a command like:  
  ```bash
  find . -name "*.sh" -print0 | xargs -0 -n1 shellcheck && kube-linter lint manifests/
  ```  
  Explain how this workflow helps ensure the correctness and security of both scripts and container orchestration files.  
- **Python Repositories**: Combine Ruff, Bandit, and mypy to perform linting, security checks, and type validation. Provide a command like:  
  ```bash
  ruff check . && bandit -r . && mypy src/
  ```  
  Explain how this workflow improves Python code quality, catches security vulnerabilities, and ensures type safety.  
- **Documentation and Links**: Use lychee to catch broken URLs in Markdown or HTML files. Provide a command like:  
  ```bash
  lychee README.md
  ```  
  Explain how this workflow ensures the quality and reliability of project documentation.  

Discuss how these workflows can be customized for different programming languages, frameworks, and project requirements.

---

#### Prompt 4: When to Avoid Credentials  
Request an in-depth discussion on scenarios where developers should avoid using tools that require credentials. Include examples such as:  
- **CAPTCHA Features**: Explain why CAPTCHA features like hCaptcha, which require a site key and secret, should be avoided during development to reduce complexity and dependency on external services. Suggest using detection flows or mock services instead and only integrating hCaptcha in production.  
- **Local Analytics and Linting**: Emphasize the benefits of using local tools like Trivy, Checkov, ShellCheck, Spectral, and KubeLinter during the build process to avoid relying on external accounts or cloud services. Highlight how these tools can surface real defects offline, ensuring a secure and efficient development process.  
- **Model Routing**: Explain how LiteLLM requires upstream provider API keys to call external models. Recommend keeping this separate from local error detection workflows and only integrating it when external model calls are necessary.  

Provide additional examples of how avoiding credentials can simplify workflows, improve security, and reduce reliance on external services.

---

#### Prompt 5: Minimal One-Shot Scan Script  
Request a consolidated bash script that installs and runs multiple no-credential tools in sequence for a comprehensive scan. The script should include:  
1. **Python Checks**: Use Ruff for linting and formatting, mypy for type checking, and Bandit for security analysis.  
2. **Secrets and Dependencies**: Use Gitleaks for detecting hardcoded secrets and Trivy for scanning filesystems, dependencies, and container images.  
3. **Shell Scripts**: Use ShellCheck for static analysis of shell scripts.  
4. **APIs and IaC**: Use Spectral for OpenAPI/JSON/YAML linting, Checkov for IaC misconfigurations, and KubeLinter for Kubernetes manifest checks.  
5. **Frontend/E2E/Performance**: Use Lighthouse for performance audits, Playwright for end-to-end testing, and k6 for load testing.  

Provide step-by-step instructions for executing the script, explain how each tool contributes to the overall error detection process, and describe how the output can be interpreted to identify and fix issues.

---

#### Prompt 6: Zero-Configuration Error Detection Tools  
Request a categorized list of error detection tools that require no credentials or setup. For each category, provide detailed descriptions of the tools and their use cases. Categories should include:  
- **Standalone Single-Executable Tools**: Tools like Cppcheck, PVS-Studio, and Detect It Easy for C/C++ analysis.  
- **JavaScript/Node.js Tools**: Tools like ESLint and JSHint for linting and code quality checks.  
- **Portable Windows Debugging Tools**: Tools like Windows Debugging Tools, DebugView Portable, and ESET SysInspector for system analysis.  
- **Browser-Based Tools**: Tools like LT Debug, Web Developer Extension, and Kiwi Browser for debugging web pages.  
- **Command-Line Static Analyzers**: Tools like Codacy CLI, Semgrep, and language-specific tools for multi-language and platform analysis.  
- **Online Tools**: Tools like JSFiddle, CodePen, and Compiler Explorer for browser-based error detection.  

For each tool, explain how it can be installed, configured (if necessary), and used immediately to detect errors or improve code quality.

---

#### Prompt 7: Minimal Workflow for Common Languages  
Request a comprehensive guide to error detection workflows in popular programming languages. Include detailed examples for:  
- **JavaScript/TypeScript**: Install and run ESLint and Prettier for linting and formatting. Provide commands for initializing ESLint with zero configuration and running it on the codebase.  
- **Python**: Use Ruff, mypy, and Bandit for linting, type checking, and security analysis. Include commands for installing and running each tool.  
- **Go**: Use golangci-lint to aggregate multiple linters and run them with optimized defaults. Provide installation and usage commands.  
- **C/C++**: Use Cppcheck and clang-tidy for static analysis. Include commands for running these tools with recommended configurations.  

Explain how these workflows can be integrated into daily development practices to ensure high-quality code and minimize errors.

---

#### Prompt 8: Pre-Commit Quality Gates  
Request a detailed explanation of how to create pre-commit sequences that integrate multiple tools into a single command to ensure code quality before committing. Include examples for Python and JavaScript/TypeScript, such as:  
- **Python**: Use Ruff for formatting and linting, then stage the corrected code for commit. Provide a command sequence like:  
  ```bash
  ruff format . && \
  ruff check . --fix && \
  git add .
  ```  
- **JavaScript/TypeScript**: Use Prettier and ESLint sequentially to format and fix code before committing. Provide a command sequence like:  
  ```bash
  prettier . --write && \
  eslint --fix "**/*.js" && \
  git add .
  ```  

Explain how these sequences can be automated using pre-commit hooks with tools like Husky or lint-staged to enforce consistent code quality and prevent errors from reaching production.

---

#### Prompt 9: Pro-Tips for Maximizing Detection Without Credentials  
Request a list of advanced tips for maximizing error detection using tools that require no accounts or credentials. Include advice such as:  
- Running linters and type checkers before running tests to fail fast and save time.  
- Using severity filters and baseline files (e.g., Trivy, Gitleaks, Checkov) to reduce noise in large projects.  
- Pairing domain-specific linters (e.g., Hadolint, ShellCheck, Spectral) to catch non-code issues like Dockerfile errors or OpenAPI specification problems.  
- Using Lighthouse CI as a gate for performance, accessibility, and SEO, and Playwright for functional regression testing.  
- Running local tools offline to improve security and reduce reliance on external services.  

Provide examples of how to integrate these tips into daily development workflows and explain how they can help developers identify and fix issues more efficiently.

---

#### Prompt 10: One-Shot Local Scanner  
Request a single, comprehensive bash script that installs and runs all recommended no-credential tools in sequence. The script should:  
1. Install necessary tools (e.g., Ruff, Bandit, Trivy, Checkov, etc.).  
2. Run linting, type checking, security scanning, API validation, Kubernetes manifest analysis, and performance testing.  
3. Provide clear, summarized output for each tool.  

Explain how this script can be executed with minimal setup and how it integrates all the tools into a single, efficient workflow to save time and improve code quality. Suggest ways to modify the script for specific use cases or programming languages.