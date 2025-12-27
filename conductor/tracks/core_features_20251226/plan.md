# Plan: Core Features - ClaimGuardian MVP

## Phase 1: Project Initialization & Infrastructure Setup
- [x] Task: Initialize Next.js project with TypeScript, Tailwind CSS, and Shadcn/UI. 1788bfc
- [x] Task: Set up Vercel deployment and link the project. f977011
- [x] Task: Provision Neon PostgreSQL database with `pgvector` extension via `neonctl` (or manual setup if CLI unavailable). e2154fd
- [x] Task: Configure environment variables for database connection (`DATABASE_URL`) and Gemini API (`GEMINI_API_KEY`) in Vercel and locally. acb6a0f
- [x] Task: Conductor - User Manual Verification 'Phase 1: Project Initialization & Infrastructure Setup' (Protocol in workflow.md) 5b5bf29

## Phase 2: Database Schema & Management
- [x] Task: Initialize Prisma and define the schema for `Payer`, `Policy` (with `vector` type), and `Claim` models. d66ffe1
- [ ] Task: Create a migration to apply the schema to the Neon database.
- [ ] Task: Create a seed script to populate initial `Payer` data and sample `Policy` embeddings (using a dummy embedding function for now or a real one if feasible).
- [ ] Task: Conductor - User Manual Verification 'Phase 2: Database Schema & Management' (Protocol in workflow.md)

## Phase 3: Core API Development - Claim Scrubbing
- [ ] Task: Implement a utility function to generate text embeddings using Gemini API.
- [ ] Task: Write tests for the embedding utility (mocking the API response).
- [ ] Task: Implement the `/api/scrub` route handler.
    - Subtask: Write tests for `/api/scrub` (mocking database and AI service).
    - Subtask: Implement logic to receive claim data, generate embeddings for relevant codes, query `Policy` table using `pgvector`, and use Gemini to analyze denial risk.
- [ ] Task: Conductor - User Manual Verification 'Phase 3: Core API Development - Claim Scrubbing' (Protocol in workflow.md)

## Phase 4: Core API Development - Automated Appeals
- [ ] Task: Implement the `/api/appeal` route handler.
    - Subtask: Write tests for `/api/appeal`.
    - Subtask: Implement logic to accept a denial letter (text/image), use Gemini to parse it, map to policies, and generate an appeal letter.
- [ ] Task: Conductor - User Manual Verification 'Phase 4: Core API Development - Automated Appeals' (Protocol in workflow.md)

## Phase 5: Frontend Dashboard
- [ ] Task: Create a layout with a sidebar and navigation.
- [ ] Task: Build the "Claim Scrubbing" page with a form to input claim details (CPT codes, diagnosis, etc.).
- [ ] Task: Build the "Appeal Generator" page with a file upload (or text input) for denial letters.
- [ ] Task: Display results from the scrubbing and appeal APIs in a clear, user-friendly format.
- [ ] Task: Conductor - User Manual Verification 'Phase 5: Frontend Dashboard' (Protocol in workflow.md)

## Phase 6: Final Polish & Deployment
- [ ] Task: Perform end-to-end testing of the scrub and appeal flows.
- [ ] Task: Optimize UI/UX based on "Clinical & Minimalist" guidelines.
- [ ] Task: Deploy the final MVP to Vercel production.
- [ ] Task: Conductor - User Manual Verification 'Phase 6: Final Polish & Deployment' (Protocol in workflow.md)
