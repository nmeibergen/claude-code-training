# Welcome to the TaskFlow Challenge!

Build a Kanban task management app using Claude Code. This challenge teaches you how to leverage Claude's code generation, iteration, debugging, and full-stack capabilities — and a live scoreboard tracks your progress as you complete each step.

## Getting Started

1. **Install dependencies:**
   ```bash
   npm install
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

### Step 1: Set Up CLAUDE.md (10 points)

**Goal:** Fill in the CLAUDE.md file so Claude Code understands your project.

**Why it matters:** CLAUDE.md is a reference document that helps Claude Code understand your project — what frameworks you're using, which ports they run on, your coding style, and any conventions to follow. An empty CLAUDE.md means Claude Code knows nothing about your project. A good one makes every future prompt more effective.

**Hints:**
- Look at the project structure first — explore what's already here (backend, frontend, package.json, etc.)
- Then tell Claude Code about the project in your own words: "This is a Node.js/Express + React (Vite) monorepo. The backend runs on port 3001, frontend on 5173. We use ESM imports, functional React components with hooks, and all API routes are prefixed with /api/. Please write a CLAUDE.md that captures these conventions."
- Review what Claude Code writes — does it match the project? Ask it to add anything it missed.

**When done:** Run `/verify 1` to verify.

---

### Step 2: Git Setup & /commit Command (10 points)

**Goal:** Create your own custom Claude Code slash command that you'll use for the rest of the session.

**Why it matters:** You've already used `/verify` — but did you know it's just a markdown file in `.claude/commands/`? You can write your own. In this step you'll build a `/commit` command that makes git commits effortless. Check out this post for inspiration:

👉 https://www.reddit.com/r/ClaudeAI/comments/1pbhoyr/still_writing_commit_messages_by_hand_try_claude/

**What your /commit command must do:**
- Review all uncommitted changes and understand what was changed
- Group changes into **multiple logical commits** if they span different areas (e.g. backend work and frontend work should be separate commits — not one big blob)
- **Never push** to any remote

**Hints:**
- Ask Claude Code to create the file `.claude/commands/commit.md` based on the article above, with your two requirements baked in
- Once the file exists, try running `/commit` — this is your first real commit (the CLAUDE.md you wrote in step 1)
- From now on, run `/commit` after every step. You'll end up with a clean git history that tells your whole learning story.

**When done:** Run `/verify 2` to verify.

---

### Step 3: Build the Task API (10 points)

**Goal:** Create CRUD endpoints for task management.

**Why it matters:** This step teaches you how to be specific in prompts. The more detail you give Claude Code about what endpoints you need and what they should do, the better the result.

**Hints:**
- Be specific: Tell Claude Code exactly what endpoints you need (GET /api/tasks, POST /api/tasks, PATCH /api/tasks/:id, DELETE /api/tasks/:id)
- Describe the request/response shapes: What fields does a task have? What does the payload look like?
- Suggest a simple in-memory data structure to start (an array of tasks with id, title, status, etc.)

**When done:** Run `/verify 3` to verify. Then run `/commit`.

---

### Step 4: Build the Kanban Board UI (10 points)

**Goal:** Create a three-column board (To Do, In Progress, Done) that displays and creates tasks.

**Why it matters:** Now Claude Code has to understand *both* the backend and the frontend. If the first result isn't perfect, don't start over — iterate!

**Hints:**
- Start with a clear description: "Create a Kanban board with three columns: To Do, In Progress, and Done"
- If the styling or layout isn't quite right, tell Claude Code what's wrong and let it fix it
- Ask it to fetch tasks from the backend and display them
- Add a form to create new tasks

**When done:** Run `/verify 4` to verify. Then run `/commit`.

---

### Step 5: Add Drag & Drop (10 points)

**Goal:** Make tasks draggable between columns.

**Why it matters:** This step teaches you Claude Code's **plan mode** — a dedicated mode where Claude Code can read and explore your codebase but *cannot make any changes*. It only discusses, analyzes, and proposes an approach. This is powerful for complex features where you want to agree on a plan before any code is written.

**How to use plan mode:**
1. Press `Shift+Tab` to cycle through modes until you see **"plan mode on"** in the status bar
2. Ask Claude Code: "I want to add drag and drop so users can move tasks between columns. What approach would you recommend? What are the trade-offs between native HTML5 drag/drop and a library like @dnd-kit?"
3. Discuss and refine the plan together — Claude Code will explore your code and propose an approach, but won't change anything
4. Once you're happy with the plan, press `Shift+Tab` again to switch back to normal mode
5. Then tell Claude Code to implement the plan

**Hints:**
- In plan mode, Claude Code can read your files and run commands to understand your codebase — use this to get a thorough analysis
- You could end up with native HTML5 drag/drop, `react-beautiful-dnd`, or `@dnd-kit` — let Claude Code reason about the trade-offs
- When a task is dropped, it should call PATCH /api/tasks/:id with the new status

**When done:** Run `/verify 5` to verify. Then run `/commit`.

---

### Step 6: Fix the Bugs (10 points)

**Goal:** Find and fix two bugs in your application.

**Why it matters:** This teaches you debugging with Claude Code. Instead of pointing at specific lines of code, you describe *what's wrong* and let Claude Code trace the cause across your codebase.

**What to do:**
1. Open your Kanban board in the browser (http://localhost:5173)
2. Create a few tasks and test the app thoroughly:
   - Try **deleting** a task — does it actually disappear?
   - Try **moving** a task between columns (drag & drop) — does the board update?
3. You should notice two things aren't working correctly. Describe what you observe to Claude Code and ask it to find and fix the issues.

**Hints:**
- Tell Claude Code what you *observe* (e.g., "When I delete a task, the API says it succeeded, but the task is still there when I refresh") rather than where you think the bug is
- Let Claude Code search your codebase and reason about what could cause each symptom
- There are two separate bugs — one in the backend, one in the frontend

**When done:** Run `/verify 6` to verify. Then run `/commit`.

---

### Step 7: Visual Polish with Screenshots (10 points)

**Goal:** Make your app look polished and professional.

**Why it matters:** Claude Code can see! Take a screenshot of your app, paste it in, and ask it to improve the design. This teaches you to iterate visually.

**Hints:**
- Open your running app in the browser
- Take a screenshot (with your OS screenshot tool)
- Paste it into Claude Code and ask for design improvements
- Ask for better spacing, colors, typography, or interactive feedback
- Claude Code can suggest and implement improvements based on what it sees

**When done:** Run `/verify 7` to verify. (Make sure you've also updated CLAUDE.md with any new information about your project.) Then run `/commit`.

---

### Step 8: Write Tests (10 points)

**Goal:** Write automated tests for your backend API.

**Why it matters:** Watch Claude Code's autonomous loop in action. It picks a test framework, installs it, writes tests, runs them, sees failures, and fixes them — all in one go.

**Hints:**
- Ask Claude Code: "Write tests for the task API endpoints (GET, POST, PATCH, DELETE). Pick a test framework and run the tests until they all pass."
- Claude Code will choose something like Jest or Vitest
- It'll write tests, run them, see if any fail, and iterate until green
- You might need to install dependencies with `npm install` in the backend workspace

**When done:** Run `/verify 8` to verify. Then run `/commit`.

---

### Step 9: Freestyle Feature (15 points)

**Goal:** Build any feature you want in a single comprehensive prompt.

**Why it matters:** This is your chance to put everything together. The challenge is giving Claude Code enough context to build a complete feature end-to-end.

**Hints:**
- Pick a feature: filtering tasks by status, editing task titles, due dates, priority levels, task search, dark mode, etc.
- Write one prompt that gives full context: what the feature is, what it should do, where it goes in the UI, what endpoints it needs, etc.
- The more specific and complete your prompt, the better the result
- Iterate if the first version needs tweaks

**When done:** Run `/verify 9` to verify. Then run `/commit` one last time — your git log tells your whole story!

---

## Tips

**Be Specific:** Vague prompts get vague results. Instead of "make the UI better," say "add a card layout with shadows and rounded corners, make the buttons blue with white text, add padding to the columns."

**Iterate, Don't Restart:** If Claude Code's first attempt isn't quite right, tell it what's wrong and let it fix it. This is much faster than asking it to start over.

**Use Plan Mode:** For complex features, press `Shift+Tab` to enter plan mode. Claude Code will explore your codebase and discuss the approach without making any changes. Once you agree on a plan, switch back to normal mode and tell it to implement.

**Keep Context Fresh:** Between steps, run `/compact` in Claude Code to clean up your chat history and free up context for the next task.

**Commit Often:** After each step verification, run `/commit` — your custom command will group the changes into clean, logical commits. By the end you'll have a git history that reads like a story.

**Update CLAUDE.md:** As your project evolves, ask Claude Code to update CLAUDE.md. This keeps the reference document current and helps with future iterations.

**Run `/verify` Regularly:** Don't wait until you think you're done. Verification gives you clear feedback on what's actually working.

Good luck!
