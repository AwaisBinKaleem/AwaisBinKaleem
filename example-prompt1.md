# EffortTrack PRD: Recruitment Integrity SaaS

## 1. Project Overview
**EffortTrack** is a professional SaaS MVP designed for recruiters to verify the "effort" behind job applications. By tracking active time-on-page and clipboard events, the tool identifies candidates who are mass-applying with low intent (extreme speed or high copy-paste ratios).

### Core Tech Stack
| Category | Selection |
| :--- | :--- |
| **Language** | TypeScript (Strict Mode) |
| **Runtime** | Bun |
| **Framework** | Next.js 14+ (App Router) |
| **Styling** | Tailwind CSS |
| **Component Library** | Shadcn UI (Radix) |
| **Auth** | Clerk (Google Social Login) |
| **Database** | Convex DB (Real-time) |
| **Monorepo** | No (Standard Next.js Structure) |
| **PWA** | Yes (using `next-pwa`) |
| **Modern Design** | Yes (Bento-style / Minimalist) |
| **Project Type** | Dashboard / SaaS |
| **AI-IDE** | Cursor / VS-Code |

---

## 2. System Architecture
* **Tracking Script:** A lightweight JS logic snippet to be embedded on application forms.
* **Data Points:** `start_time`, `end_time`, `paste_count`, `blur_count` (tab switching), and `field_focus_events`.
* **The Flagging Engine:** A serverless logic block (Convex Action) that runs scoring:
    * **Flag Logic:** If `TotalTime < (GlobalAvgTime * 0.3)` or `PasteCount > Threshold`.
* **Recruiter Dashboard:** A real-time interface with filtering, sorting, and "Shortlist" state management.

---

## 3. Implementation Phases (Agent Prompts)

### Phase 1: Foundation & Auth Setup
**Prompt:**
> "Initialize a Next.js 14+ project using Bun and TypeScript. Set up Tailwind CSS and Shadcn UI. Integrate Clerk Auth with Google Social Login as the primary provider. Configure the Convex DB client and hooks. Create a basic layout with a protected `/dashboard` route and a public landing page. Ensure the folder structure follows professional standards: `/components`, `/hooks`, `/lib`, and `/convex` for backend functions."

### Phase 2: Schema Design & Convex Functions
**Prompt:**
> "Define the Convex schema in `convex/schema.ts`. We need a `submissions` table containing: `jobId`, `candidateEmail`, `candidateName`, `completionTime` (seconds), `pasteCount`, `isFlagged` (boolean), `status` (pending/shortlisted/rejected), and `metadata` (JSON). Create a mutation to handle incoming tracking data and a query to fetch all submissions for the authenticated recruiter."

### Phase 3: The Tracking Script & API Endpoint
**Prompt:**
> "Build a client-side tracking script as a React hook (`useTrackSubmission`). It must:
> 1. Start a timer on mount.
> 2. Listen for `paste` events and increment a counter.
> 3. Capture `visibilitychange` to pause/resume the timer when the user switches tabs.
> 4. On form submission, send the data to the Convex mutation.
> Create a 'Demo Application Form' page at `/demo-job` that uses this hook to simulate a real-world application."

### Phase 4: Recruiter Dashboard UI (The Modern Look)
**Prompt:**
> "Build the main dashboard at `/dashboard`. Use a Shadcn `DataTable`. 
> 1. Display: Candidate Name, Time Spent, Paste Count, and a Flag Badge (Red if flagged).
> 2. Add 'Bento Box' style stats cards at the top: 'Avg. Effort Time', 'Total Flagged', and 'Success Rate'.
> 3. Implement real-time updates using Convex `useQuery`.
> 4. Ensure the design is clean/modern using a Zinc/Slate color palette with subtle borders and soft shadows."

### Phase 5: Filtering & Shortlisting Logic
**Prompt:**
> "Enhance the dashboard with functional filters:
> 1. Toggle for 'Hide Flagged Applicants'.
> 2. Slider for 'Minimum Time Spent' (seconds).
> 3. Add a 'Shortlist' button on each row that updates the candidate status in Convex.
> 4. Create a separate 'Shortlist' tab. Implement a simple flagging algorithm: if time spent is 50% below the average for that job ID, automatically set `isFlagged` to true."

### Phase 6: PWA & Final Polishing
**Prompt:**
> "Convert the application into a PWA using `next-pwa`. Configure the manifest and service workers. Add 'Empty State' illustrations for the dashboard and loading skeletons using Shadcn Skeleton. Conduct a final review of the TypeScript types for the tracking payload to ensure no 'any' types are used. Optimize the layout for both Desktop and Tablet views."

---

## 4. Coding Standards & Requirements
* **Clean Code:** Use Early Returns and descriptive variable names.
* **UI/UX:** Use `lucide-react` for icons. Ensure all buttons have hover/active states.
* **Security:** Ensure Convex functions use `ctx.auth.getUserIdentity()` to verify the recruiter.
* **Performance:** The tracking script must be lightweight and should not cause re-renders on the main form fields.
