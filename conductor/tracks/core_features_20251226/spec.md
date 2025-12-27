# Track Specification: Core Features - ClaimGuardian MVP

## 1. Overview
This track focuses on building the Minimum Viable Product (MVP) for ClaimGuardian, a HIPAA-aware AI tool for medical claim scrubbing and automated insurance appeals. The goal is to set up the necessary infrastructure, define the database schema, and implement the core scrubbing and appeal generation logic using Next.js, Neon (PostgreSQL + pgvector), and the Gemini API.

## 2. Goals
- **Infrastructure Setup:** Provision a Neon PostgreSQL database with `pgvector` enabled and link it to a Vercel project.
- **Database Schema:** Define and push the Prisma schema for Payers, Policies (with embeddings), and Claims.
- **Core API Development:**
    - Implement `/api/scrub` for RAG-based claim scrubbing.
    - Implement `/api/appeal` for vision-to-text denial letter parsing and appeal generation.
- **Frontend Development:** Create a dashboard for uploading claims and viewing results.
- **Deployment:** Deploy the functional MVP to Vercel.

## 3. Key Features
- **RAG-based Claim Scrubbing:** Analyze claims against policy embeddings to identify denial risks.
- **Automated Appeal Generation:** Parse denial letters and generate Markdown-formatted appeals.
- **Dashboard:** User interface for claim management and appeal review.

## 4. Technical Requirements
- **Framework:** Next.js (App Router)
- **Database:** Neon (PostgreSQL) with `pgvector` extension.
- **ORM:** Prisma
- **AI Model:** Gemini 1.5 Pro via API.
- **Deployment:** Vercel.
- **Styling:** Tailwind CSS + Shadcn/UI.

## 5. Security & Compliance
- **HIPAA Awareness:** De-identify PHI before sending data to external AI APIs.
- **Secure Configuration:** Use encrypted environment variables for API keys and database connections.
