# TaskFlow — Kanban Task Manager

## Overview
TaskFlow is a full-stack Kanban board application for managing tasks across status columns (todo, in-progress, done).

## Tech Stack
- **Backend:** Express.js (Node.js) with in-memory data storage
- **Frontend:** React 18 with Vite as the build tool
- **Module format:** ESM (`"type": "module"`) throughout

## Project Structure
- `backend/` — Express API server
- `frontend/` — React + Vite single-page app
- Root `package.json` uses npm workspaces to manage both packages

## Conventions
- **API prefix:** All backend routes are under `/api` (e.g., `/api/tasks`)
- **Backend port:** 3001
- **Frontend port:** 5173 (Vite dev server), with a proxy forwarding `/api` requests to the backend
- **Running the app:** `npm run dev` from the root starts both backend and frontend concurrently
- **Backend dev:** Uses `node --watch` for auto-reload (no nodemon needed)
- **Dependencies:** `uuid` for generating task IDs, `cors` for cross-origin support
- **No database:** Tasks are stored in-memory (array) for simplicity
