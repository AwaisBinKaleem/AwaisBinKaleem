# Project Blueprint: "GenAI-Engine" – Enterprise AI Content Integration

## 1. Project Overview
**GenAI-Engine** is a robust, production-ready integration of OpenAI's GPT-4 into a SaaS ecosystem. This project focuses on moving beyond simple API calls by implementing professional prompt engineering, cost-optimization caching, rate-limiting, and enterprise-grade deployment (Docker/AWS).

### Core Tech Stack
| Category | Selection |
| :--- | :--- |
| **Language** | TypeScript (Strict Mode) |
| **Runtime** | Node.js (Latest LTS) |
| **Framework** | Next.js 14+ (App Router) |
| **Styling** | Tailwind CSS |
| **Component Library** | Shadcn UI |
| **Auth** | Clerk (Google Social Login) |
| **Database** | MongoDB (Atlas) |
| **Cache** | Redis (Upstash) |
| **Testing** | Jest + Supertest |
| **DevOps** | Docker + AWS (EC2/Lambda) |
| **AI-IDE** | Cursor / VS-Code |

---

## 2. System Architecture
* **AI Service Layer:** A dedicated service to manage OpenAI streams, retry logic (Exponential Backoff), and token counting.
* **Prompt Registry:** A structured system to manage system prompts and versioning for consistent outputs.
* **Cost Optimizer:** A caching layer using Redis to prevent redundant API calls for identical requests.
* **Security Layer:** Middleware for request sanitization and rate-limiting to prevent API abuse.

---

## 3. Implementation Phases (Agent Prompts)

### Phase 1: Environment & Base Infrastructure
**Prompt:**
> "Initialize a Next.js 14 project with TypeScript and Bun. Set up a MongoDB connection using Mongoose. Configure a Redis (Upstash) client for caching. Create a project structure that separates 'services', 'models', and 'api' routes. Add Clerk for authentication. Create a basic UI page with a text area and a 'Generate' button to act as our testbed."

### Phase 2: OpenAI Integration & Prompt Engineering
**Prompt:**
> "Integrate the OpenAI SDK. Create a service in `lib/openai.ts` that uses GPT-4. Implement:
> 1. A Prompt Registry: Store system prompts in a separate config file for different use cases (e.g., 'Blog Post', 'Code Review').
> 2. Error Handling: Build a wrapper for the OpenAI call that handles 429 (Rate Limit) and 500 errors.
> 3. Retry Logic: Use an exponential backoff strategy for failed requests."

### Phase 3: Backend Logic & Caching
**Prompt:**
> "Develop a POST endpoint `/api/generate`. It should:
> 1. Validate the user session via Clerk.
> 2. Sanitize and validate the input using Zod.
> 3. Check Redis cache: If a hashed version of the prompt exists, return the cached response.
> 4. If not cached, call the OpenAI service, store the result in MongoDB (including token usage metrics), and save it to Redis for 24 hours."

### Phase 4: API Robustness (Rate Limiting & Security)
**Prompt:**
> "Implement rate limiting using `@upstash/ratelimit` to restrict users to 10 generations per minute. Add request sanitization to prevent prompt injection. Write Jest unit tests for the `/api/generate` endpoint, mocking the OpenAI and MongoDB responses to ensure the logic handles failures gracefully."

### Phase 5: Containerization & CI/CD
**Prompt:**
> "Create a `Dockerfile` and `docker-compose.yml` for the application. Set up a GitHub Action workflow (.yml) that:
> 1. Runs linting and Jest tests.
> 2. Builds the Docker image.
> 3. Deploys to AWS (provide placeholders for EC2 or Lambda environment variables). Include a `documentation.md` file explaining the architecture and maintenance steps."

### Phase 6: Monitoring & UI Finalization
**Prompt:**
> "Build a 'History' dashboard in the UI using Shadcn cards that fetches previous generations from MongoDB. Add a 'Usage' tracker showing how many tokens the user has consumed. Implement a 'Copy to Clipboard' feature and a 'Regenerate' button that clears the cache for that specific prompt."

---

## 4. Coding Standards & Requirements
* **Type Safety:** No `any` types. Use Zod for all API request/response schemas.
* **Resilience:** All external API calls must be wrapped in try/catch with proper logging.
* **Efficiency:** Use Vercel Edge Runtime for the generation API if possible to reduce latency.
* **Documentation:** All functions should have JSDoc comments explaining parameters and expected errors.
