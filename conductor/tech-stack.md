# Technology Stack

## Overview

The ClaimGuardian MVP will be built using a modern and robust technology stack designed for scalability, performance, and developer efficiency. This selection prioritizes serverless deployment, a powerful database with vector capabilities, and a flexible frontend framework.

## Core Technologies

*   **Frontend Framework:** Next.js (App Router) - For building a highly performant and scalable web application with server-side rendering capabilities.
*   **Database:** Neon (PostgreSQL with pgvector) - A serverless PostgreSQL database offering strong relational features combined with vector indexing for efficient similarity search, crucial for RAG-based policy lookups.
*   **Deployment & Hosting:** Vercel - A platform for automatic deployments, scaling, and environment management, seamlessly integrating with Next.js.
*   **Artificial Intelligence:** Gemini 1.5 Pro (API) - Google's advanced AI model for processing natural language, parsing denial letters, and generating appeal content.

## Development & Automation Tools

*   **Database Management:** Prisma - An open-source ORM that simplifies database access, schema migrations, and provides type-safe database queries.
*   **Cloud CLIs:**
    *   `neonctl` - Command-line interface for managing Neon projects and databases.
    *   `vercel` CLI - Command-line interface for deploying and managing Vercel projects and environment variables.
