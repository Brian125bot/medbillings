# Initial Concept

**Product:** Medical claim scrubbing and automated insurance appeals.

# Product Overview

This product, **ClaimGuardian MVP**, is a HIPAA-aware AI tool designed to revolutionize the medical billing process. It leverages advanced AI to perform end-to-end medical claim scrubbing and automated insurance appeals. By proactively identifying potential issues in claims before submission and streamlining the appeals process, ClaimGuardian significantly reduces denial rates and improves revenue cycle efficiency for healthcare providers. The goal is to perform an automated setup of infrastructure, database, and hosting to get the MVP up and running quickly.

# Target Audience

The primary target audience for this product is **Healthcare Providers**, including hospitals, clinics, and individual practitioners. This encompasses a wide range of medical professionals who frequently interact with health insurance payers and are impacted by the complexities of medical billing and claims processing.

# Key Goals & Problem Solved

The core objective of this product is to **reduce claim denial rates and improve revenue cycle efficiency** for healthcare providers. This addresses a critical pain point in the healthcare industry, where claim denials lead to significant administrative burdens, delayed payments, and lost revenue.

### PROJECT GOAL:
Build and deploy "ClaimGuardian MVP"—a HIPAA-aware AI tool for medical claim scrubbing and automated appeals. Perform an end-to-end automated setup of infrastructure, database, and hosting.

### TECH STACK & TOOLS:
- **Framework:** Next.js (App Router)
- **Database:** Neon (PostgreSQL + pgvector)
- **Deployment:** Vercel
- **AI:** Gemini 1.5 Pro (API)
- **Automation CLIs:** `neonctl`, `vercel`, `prisma`

### KEY FEATURES & IMPLEMENTATION STEPS:

#### 1. INFRASTRUCTURE AUTOMATION (CLI)
Automate the setup using system CLIs:
- **Neon Provisioning:** Initialize a new project named "claim-guardian" using `neonctl`.
- **Database Config:** Enable vector extension (`CREATE EXTENSION IF NOT EXISTS vector;`) via `neonctl`.
- **Connection String:** Retrieve and save the connection string to `.env.local`.
- **Vercel Linking:** Initialize a new Vercel project and push the `DATABASE_URL` environment variable.

#### 2. DATABASE SCHEMA (PRISMA)
Scaffold a schema supporting:
- `Table Payers`: Metadata and appeal windows.
- `Table Policies`: Use `vector(1536)` for policy embeddings.
- `Table Claims`: Relational link to payers + risk score.
- **Action:** Sync schema to Neon instance via `npx prisma db push`.

#### 3. CORE APPLICATION LOGIC
- **API `/api/scrub`:** A RAG-based scrubbing route that uses `pgvector` to find relevant policies, de-identifies PHI, and returns denial risk with suggested edits using Gemini.
- **API `/api/appeal`:** A Vision-to-Text route that parses denial letters using Gemini 1.5 Pro, maps CARC codes to internal policies, and generates Markdown-formatted appeal letters.

#### 4. UI & DEPLOYMENT
- **Frontend:** A dashboard built with Tailwind and Shadcn/UI for uploading claims and viewing appeal drafts.
- **Deployment:** Automated production deployment via `vercel deploy --prod`.

### CONSTRAINTS:
- Use Vercel's encrypted environment variables for `GEMINI_API_KEY`.
- All database interactions must be typed and secure.
- Ensure the folder structure follows Next.js App Router best practices.
