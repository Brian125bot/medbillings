# ClaimGuardian MVP

**Status:** Phase 2 (In Progress)
**URL:** [Vercel Deployment Link - TBD]

ClaimGuardian MVP is a HIPAA-aware AI tool designed to automate medical claim scrubbing and insurance appeals. It leverages advanced AI (Gemini 1.5 Pro) and a vector database (Neon + pgvector) to reduce claim denial rates and improve revenue cycle efficiency for healthcare providers.

## Project Goals

1.  **Automated Claim Scrubbing:** Analyze medical claims using a RAG (Retrieval-Augmented Generation) system to identify potential denial risks based on payer-specific policies.
2.  **Automated Appeals:** Parse denial letters using Vision-to-Text AI and automatically generate appeal letters grounded in payer policies.
3.  **Modern Infrastructure:** Build on a robust, scalable stack with Next.js, Neon PostgreSQL, and Vercel.
4.  **HIPAA Compliance:** Ensure all PHI is de-identified before being processed by external AI services.

## Architecture & Tech Stack

*   **Frontend:** Next.js 14+ (App Router), Tailwind CSS, Shadcn/UI
*   **Backend:** Next.js API Routes (Serverless Functions)
*   **Database:** Neon Serverless PostgreSQL with `pgvector` extension
*   **ORM:** Prisma
*   **AI Model:** Gemini 1.5 Pro (via Google AI Studio)
*   **Deployment:** Vercel

## Current Status & Progress

The project is currently in **Phase 2: Database Schema & Management**.

### Completed
*   [x] **Project Scaffolding:** Initialized Next.js app with TypeScript, Tailwind, and Shadcn/UI.
*   [x] **Infrastructure:** Linked to Vercel, provisioned Neon Postgres DB, and enabled `pgvector` extension.
*   [x] **Configuration:** Environment variables (`DATABASE_URL`, `GEMINI_API_KEY`) configured locally and on Vercel.
*   [x] **Database Schema:** Defined Prisma schema for `Payer`, `Policy` (with vector embeddings), and `Claim` models.
*   [x] **Migrations:** Applied initial migration to the Neon database.

### In Progress / Pending
*   [ ] **Seeding:** A seed script (`prisma/seed.js`) has been created to populate initial data, but execution is currently **halted due to a WebSocket connectivity issue** with the `@neondatabase/serverless` driver in the development environment.
*   [ ] **Core API Development:** Implementation of `/api/scrub` and `/api/appeal` endpoints.
*   [ ] **Frontend Dashboard:** UI for claim submission and appeal review.

## Known Issues

*   **Database Seeding Blocked:** The `@neondatabase/serverless` driver throws `TypeError: fetch failed` when attempting to connect to Neon via WebSocket from the current development environment. This has paused the seeding task.
    *   *Workaround:* Pending environment fix or manual SQL import.

## Getting Started (for Developers)

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/Brian125bot/medbillings.git
    cd medbillings
    ```

2.  **Install dependencies:**
    ```bash
    npm install
    ```

3.  **Environment Setup:**
    Create a `.env` file in the root directory with the following keys:
    ```env
    DATABASE_URL="your_neon_postgres_connection_string"
    GEMINI_API_KEY="your_gemini_api_key"
    ```

4.  **Run Migrations:**
    ```bash
    npx prisma migrate dev
    ```

5.  **Run Development Server:**
    ```bash
    npm run dev
    ```
    Open [http://localhost:3000](http://localhost:3000) to view the app.

## Project Structure

*   `src/app`: Next.js App Router pages and API routes.
*   `src/components`: React components (Shadcn/UI).
*   `src/lib`: Utility functions.
*   `prisma`: Database schema and seed scripts.
*   `conductor`: Project management and planning documents (Spec-Driven Development artifacts).

## Conductor Context

This project uses the **Conductor** framework for spec-driven development.
*   `conductor/product.md`: High-level product vision and requirements.
*   `conductor/tracks/`: Detailed plans for each development track.
*   Current Track: `conductor/tracks/core_features_20251226/plan.md`