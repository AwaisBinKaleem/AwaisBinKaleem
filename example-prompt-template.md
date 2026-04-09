# Project Blueprint: [Project Name] – Professional Implementation Plan

## 1. Project Overview
**Description:** [A brief, high-level summary of the goal, target audience, and core value proposition based on the user's specific requirements.]

### Core Tech Stack (Customizable)
| Category | Selection |
| :--- | :--- |
| **Language** | [e.g., TypeScript / Python / Go] |
| **Runtime/Environment** | [e.g., Bun / Node.js / JVM] |
| **Primary Framework** | [e.g., Next.js / FastAPI / Spring Boot] |
| **Styling/UI** | [e.g., Tailwind CSS / Shadcn UI / Material UI] |
| **Auth** | [e.g., Clerk / NextAuth / Firebase Auth] |
| **Database** | [e.g., Convex / MongoDB / PostgreSQL] |
| **State Management** | [e.g., TanStack Query / Redux / Zustand] |
| **Infrastructure** | [e.g., Docker / AWS / Vercel] |
| **AI-IDE** | [e.g., Cursor / VS-Code] |

---

## 2. System Architecture & Core Features
* **Feature 1:** [Primary functional requirement].
* **Feature 2:** [Secondary functional requirement].
* **Data Strategy:** [How data flows between the user, the server, and the database].
* **Logic Engine:** [Description of any specific algorithms, AI integrations, or complex business logic].

---

## 3. Implementation Phases (Sequential Agent Prompts)

### Phase 1: Environment Initialization & Foundation
**Prompt:**
> "Initialize a new [Framework] project using [Runtime/Language]. Configure [Tailwind/UI Library] for the design system. Set up the foundational folder structure (e.g., /components, /lib, /services, /hooks). Establish the environment variable configuration and connect to [Database/Auth Provider]. Create a basic, responsive layout with a placeholder landing page and navigation."

### Phase 2: Data Modeling & Backend Logic
**Prompt:**
> "Define the data schema/models in [Database Tool] based on the project requirements. Implement the core CRUD operations or serverless functions needed for the primary features. Ensure strict type safety and implement custom hooks or services to interact with this data. Include basic error handling for database connections."

### Phase 3: Core Feature Implementation
**Prompt:**
> "Build the primary functional logic for [Feature 1] and [Feature 2]. Create the necessary API endpoints or server actions. If external APIs (like OpenAI or Stripe) are required, integrate the SDKs now with proper error handling and retry logic. Ensure that the backend logic is modular and unit-testable."

### Phase 4: UI/UX & Frontend Integration
**Prompt:**
> "Develop the user interface for the main application pages (e.g., Dashboard, Forms, Settings). Use [UI Library] components to ensure a modern, clean, and accessible design. Connect the frontend components to the backend logic/hooks created in Phase 3. Implement loading states, skeletons, and toast notifications for user feedback."

### Phase 5: Advanced Logic, Security & Optimization
**Prompt:**
> "Implement advanced requirements: [e.g., Rate limiting, specialized filtering, caching with Redis, or PWA support]. Add request validation using [Zod/Joi] and ensure all routes are protected by the [Auth Provider]. Conduct a performance audit to optimize image loading and API response times."

### Phase 6: Quality Assurance & Deployment Prep
**Prompt:**
> "Write unit and integration tests for the core business logic using [Jest/Vitest/Cypress]. Create a `Dockerfile` if containerization is required. Set up a CI/CD pipeline configuration (e.g., GitHub Actions) for automated testing and deployment to [AWS/Vercel/DigitalOcean]. Generate a final `README.md` with setup instructions and API documentation."

---

## 4. Engineering Standards & Guardrails
* **Code Quality:** No `any` types; maintain 100% TypeScript coverage.
* **Architecture:** Follow the "Separation of Concerns" principle (keep UI logic and Business logic separate).
* **Performance:** All pages must score 90+ on Lighthouse; optimize for Core Web Vitals.
* **Security:** Sanitize all user inputs; implement CSRF protection and secure headers.
