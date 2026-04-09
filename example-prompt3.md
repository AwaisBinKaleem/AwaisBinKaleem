# Project Blueprint: "RecruitFlow AI" – AI-First Transformation for Recruiting NOW

## 1. Project Overview
**Description:** A comprehensive AI-first ecosystem for Recruiting NOW GmbH. The project replaces traditional, manual recruiting workflows with autonomous AI agents and internal dashboards. The goal is to automate job ad generation, candidate sourcing, and churn detection while integrating seamlessly with ATS systems and Google Workspace.

### Core Tech Stack
| Category | Selection |
| :--- | :--- |
| **Language** | TypeScript (Strict Mode) |
| **Runtime** | Bun |
| **Framework** | Next.js 14+ (App Router) |
| **Bundler** | Vite |
| **Styling/UI** | Tailwind CSS / Shadcn UI |
| **Auth** | Clerk (Google Workspace SSO) |
| **Database** | Convex DB (for real-time dashboard sync) |
| **AI Integration** | OpenAI GPT-4 / Vercel AI-SDK  (for Agentic Workflows) |
| **Integrations** | OpenClaw with telegram, Google Workspace API, ATS Webhooks with Chat GPT4 |
| **Infrastructure** | Vercel AI-SDK / AWS |
| **AI-IDE** | Cursor | antigravity |
| **PWA** | Yes |

---

## 2. System Architecture & Core Features
* **Agentic Workflows:** Autonomous agents for job ad creation (OpenClaw extension) and automated candidate sourcing/matching.
* **Recruiting Dashboard:** A "Control Center" for internal teams to monitor AI-generated job distributions and client reports.
* **Success Signals (ML/Logic):** A churn detection engine that monitors client engagement and flags at-risk subscription accounts.
* **Integration Layer:** A middleware to sync data between Google Workspace, job boards, and third-party Applicant Tracking Systems (ATS).

---

## 3. Implementation Phases (Sequential Agent Prompts)

### Phase 1: Foundation & Integration Setup
**Task:**
> "Initialize a vite Next.js 14+ project with TypeScript and Bun. Set up Shadcn UI and Tailwind CSS. Integrate Clerk for google authentication, specifically configured for Google Workspace SSO. Establish a connection to Convex DB. Create a basic internal layout with a sidebar for 'Recruiting Agents', 'Client Success', and 'Integrations'. Ensure the folder structure is optimized for a modular multi-agent system."

### Phase 2: OpenClaw Integration & Job Ad Agents
**Task:**
> "Integrate the 'OpenClaw' pilot project with telegram logic. Build an AI Agent service that:
> 1. Takes a raw job description and uses GPT-4 to generate optimized job ads.
> 2. Automates distribution via API to job boards.
> 3. Creates a 'Draft Review' UI where recruiters can approve or edit AI-generated content before it goes live. Store all distribution logs in Convex."

### Phase 3: Sourcing & Matching Engine
**Task:**
> "Implement the 'Sourcing Agent'. Develop logic to:
> 1. Parse candidate data from ATS webhooks or file uploads.
> 2. Use vector embeddings (OpenAI Embeddings) or structured LLM comparisons to match candidates against active job ads.
> 3. Build a 'Matching Score' component in the UI that explains *why* a candidate was flagged as a high-intent match."

### Phase 4: Internal Tools & Client Reporting
**Task:**
> "Build a 'Client Reporting' dashboard. This tool should aggregate data from the agents to create automated weekly reports (PDF or Web-view) for clients, using vercel-ai-sdk with open ai gpt4 and openclaw with telegram highlighting:
> 1. Positions filled vs. open.
> 2. Sourcing volume and AI-matching efficiency.
> 3. Integrate Google Workspace API to automatically draft these reports into Google Docs or send via Gmail."

### Phase 5: Churn Detection & Success Signals
**Task:**
> "Create the 'Customer Success Engine'. 
> 1. Define a schema to track client login frequency, job ad activity, and 'Success Signals'.
> 2. Implement a background job (Convex Action) that flags accounts as 'At-Risk' if activity drops below a certain threshold (Churn Detection).
> 3. Create a 'Proactive Alerts' dashboard view for the internal team to act on these signals."

### Phase 6: PWA, Optimization & Documentation
**Task:**
> "Finalize the tool as a PWA for internal team mobile use. Add loading skeletons for all real-time data tables. Write unit tests for the churn detection logic and matching algorithms. Generate a `SYSTEM.md` documentation file detailing the agentic prompts used and the integration flow with Google Workspace and OpenClaw."

---

## 4. Engineering Standards & Guardrails
* **AI Reliability:** All AI-generated job ads must pass through a human-in-the-loop (HITL) approval step.
* **Data Privacy:** Ensure strict German/GDPR compliance for candidate and client data handling.
* **Performance:** All dashboard data must be real-time (using Convex subscriptions) to avoid manual refreshes.
* **Modular Design:** Each AI agent (Sourcing, Distribution, Reporting) must be an independent service to allow for individual scaling.
