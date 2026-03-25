# Welcome to the TaskFlow Challenge!

Build a Kanban task management app using Claude Code. This challenge teaches you how to leverage Claude's code generation, iteration, debugging, and full-stack capabilities — and a live scoreboard tracks your progress as you complete each step.

## Getting Started

1. **Install dependencies:**
   ```bash
   npm install
   npm install --workspace=backend
   npm install --workspace=frontend
   ```

2. **Start the development servers:**
   ```bash
   npm run dev
   ```
   This starts both the backend (port 3001) and frontend (port 5173) in watch mode.

3. **Verify everything works:**
   - Backend: `curl http://localhost:3001/health` should return `{"status":"ok","message":"TaskFlow API is running"}`
   - Frontend: Open `http://localhost:5173` in your browser — you should see "TaskFlow" and the welcome message

## How Verification Works

After completing each step, run `/verify <step-number>` in Claude Code to check your work. The verification command will:
- Inspect your code
- Run tests or make API calls
- Report what's missing (if anything)
- Register your progress on the scoreboard

**Important:** Always register first before attempting verification steps.

## Step 0: Register

Run this command in Claude Code to register with your nickname:

```
/verify register YOUR-NICKNAME-HERE
```

Replace `YOUR-NICKNAME-HERE` with any nickname you'd like (must be unique on the scoreboard). Once registered, your progress will be tracked automatically.

## The Steps

### Step 1: Project Init & CLAUDE.md (10 points)

**Goal:** Create a CLAUDE.md file that describes your project setup.

**Why it matters:** CLAUDE.md is a reference document that helps Claude Code understand your project — what frameworks you're using, which ports they run on, your coding style, and any conventions to follow.

**Hints:**
- Use `/init` in Claude Code to generate an initial CLAUDE.md, then refine it with feedback
- Tell Claude Code about your project's framework, ports (3001 for backend, 5173 for frontend), and coding conventions (ESM imports, etc.)

**When done:** Run `/verify 1` to verify.

---

### Step 2: Build the Task API (10 points)

**Goal:** Create CRUD endpoints for task management.

**Why it matters:** This step teaches you how to be specific in prompts. The more detail you give Claude Code about what endpoints you need and what they should do, the better the result.

**Hints:**
- Be specific: Tell Claude Code exactly what endpoints you need (GET /api/tasks, POST /api/tasks, PATCH /api/tasks/:id, DELETE /api/tasks/:id)
- Describe the request/response shapes: What fields does a task have? What does the payload look like?
- Suggest a simple in-memory data structure to start (an array of tasks with id, title, status, etc.)

**When done:** Run `/verify 2` to verify.

---

### Step 3: Build the Kanban Board UI (10 points)

**Goal:** Create a three-column board (To Do, In Progress, Done) that displays and creates tasks.

**Why it matters:** Now Claude Code has to understand *both* the backend and the frontend. If the first result isn't perfect, don't start over — iterate!

**Hints:**
- Start with a clear description: "Create a Kanban board with three columns: To Do, In Progress, and Done"
- If the styling or layout isn't quite right, tell Claude Code what's wrong and let it fix it
- Ask it to fetch tasks from the backend and display them
- Add a form to create new tasks

**When done:** Run `/verify 3` to verify.

---

### Step 4: Add Drag & Drop (10 points)

**Goal:** Make tasks draggable between columns.

**Why it matters:** This step is about planning. Before diving into code, ask Claude Code to think through the approach first. You'll see it reason about trade-offs (native HTML5 vs a DnD library) before writing anything.

**Hints:**
- Ask Claude Code: "Think step by step about the best approach for drag & drop, then implement it"
- You could use native HTML5 drag/drop, `react-beautiful-dnd`, or `@dnd-kit` — let Claude Code recommend
- When a task is dropped, it should call PATCH /api/tasks/:id with the new status
- The UI should update to reflect the new status

**When done:** Run `/verify 4` to verify.

---

### Step 5: Fix the Bugs (10 points)

**Goal:** Debug and fix two bugs that I'll introduce when you verify.

**Why it matters:** This teaches you debugging with Claude Code. Instead of pointing at specific lines, describe *what's wrong* and let Claude Code find and fix it.

**What happens:**
- When you run `/verify 5`, I'll inject two bugs into your code
- I'll tell you what the symptoms are (e.g., "deleted tasks reappear", "the board doesn't refresh when you move a task")
- Your job is to describe the issue to Claude Code and ask it to find and fix it

**Hints:**
- Tell Claude Code what you *observe* (e.g., "When I delete a task, the API says it succeeded, but the task is still there") rather than where you think the bug is
- Ask Claude Code to check the backend delete logic and the frontend refresh logic
- Let Claude Code search your codebase and reason about what could cause the symptom

**When done:** Run `/verify 5` to verify.

---

### Step 6: Visual Polish with Screenshots (10 points)

**Goal:** Make your app look polished and professional.

**Why it matters:** Claude Code can see! Take a screenshot of your app, paste it in, and ask it to improve the design. This teaches you to iterate visually.

**Hints:**
- Open your running app in the browser
- Take a screenshot (with your OS screenshot tool)
- Paste it into Claude Code and ask for design improvements
- Ask for better spacing, colors, typography, or interactive feedback
- Claude Code can suggest and implement improvements based on what it sees

**When done:** Run `/verify 6` to verify. (Make sure you've also updated CLAUDE.md with any new information about your project.)

---

### Step 7: Write Tests (10 points)

**Goal:** Write automated tests for your backend API.

**Why it matters:** Watch Claude Code's autonomous loop in action. It picks a test framework, installs it, writes tests, runs them, sees failures, and fixes them — all in one go.

**Hints:**
- Ask Claude Code: "Write tests for the task API endpoints (GET, POST, PATCH, DELETE). Pick a test framework and run the tests until they all pass."
- Claude Code will choose something like Jest or Vitest
- It'll write tests, run them, see if any fail, and iterate until green
- You might need to install dependencies with `npm install` in the backend workspace

**When done:** Run `/verify 7` to verify.

---

### Step 8: Git Workflow (10 points)

**Goal:** Review all your work and create well-organized git commits.

**Why it matters:** This is one of the most-used Claude Code features in real development. It understands diffs, groups logical changes, and writes clear commit messages.

**Hints:**
- Ask Claude Code: "Review everything I've built and create well-organized git commits with descriptive messages"
- It'll see your full diff, reason about how to split it logically (e.g., "API endpoints", "UI components", "tests"), and commit each group
- Commit messages should reference specific features, not just "fix" or "update"

**When done:** Run `/verify 8` to verify.

---

### Step 9: Freestyle Feature (15 points)

**Goal:** Build any feature you want in a single comprehensive prompt.

**Why it matters:** This is your chance to put everything together. The challenge is giving Claude Code enough context to build a complete feature end-to-end.

**Hints:**
- Pick a feature: filtering tasks by status, editing task titles, due dates, priority levels, task search, dark mode, etc.
- Write one prompt that gives full context: what the feature is, what it should do, where it goes in the UI, what endpoints it needs, etc.
- The more specific and complete your prompt, the better the result
- Iterate if the first version needs tweaks

**When done:** Run `/verify 9` to verify.

---

## Tips

**Be Specific:** Vague prompts get vague results. Instead of "make the UI better," say "add a card layout with shadows and rounded corners, make the buttons blue with white text, add padding to the columns."

**Iterate, Don't Restart:** If Claude Code's first attempt isn't quite right, tell it what's wrong and let it fix it. This is much faster than asking it to start over.

**Think Before Coding:** For complex features, ask Claude Code to "think step by step about the approach first, then implement it." You'll see it reason through trade-offs before writing code.

**Keep Context Fresh:** Between steps, run `/compact` in Claude Code to clean up your chat history and free up context for the next task.

**Update CLAUDE.md:** As your project evolves, ask Claude Code to update CLAUDE.md. This keeps the reference document current and helps with future iterations.

**Run `/verify` Regularly:** Don't wait until you think you're done. Verification gives you clear feedback on what's actually working.

Good luck!
