---
name: zoom-out
description: Before diving into unfamiliar code or making changes, zoom out first — inspect the project structure, read key files, and understand the big picture.
---

# Zoom Out

## Purpose

The most common coding mistake is diving straight into changes on unfamiliar code — wrong file, wrong approach, wrong assumptions. Zooming out first takes 2 minutes and prevents 30-minute detours.

## Workflow

Trigger this before making changes to any codebase you haven't worked on in the last 7 days.

### Step 1: Inspect Project Structure

```bash
ls <project-root>              # Top-level layout
```

Identify:
- What framework? (Next.js, Vue, Express, etc.)
- Where's the entry point? (main.py, index.js, server.js, etc.)
- Where are routes/API handlers?
- Where's the schema/model layer?
- What build system? (package.json, requirements.txt, etc.)

### Step 2: Read Key Config Files

Check at least:
- `package.json` / `requirements.txt` / `pyproject.toml` — dependencies + scripts
- `tsconfig.json` / `next.config.js` / `vite.config.ts` — build config
- `docker-compose.yml` / `Dockerfile` — deployment setup (if exists)
- `.env.example` — environment variables

### Step 3: Read CONTEXT.md (if exists)

If the project has a `CONTEXT.md` (see shared-language skill), read it now.

### Step 4: Summarize Understanding

Before writing any code, articulate the answer to:

1. What is this project doing?
2. What file(s) do I need to change?
3. What's the approach?

If you can't answer all 3 clearly — you're not ready yet. Read more.

## When to Skip

- Projects you worked on yesterday or today — context is fresh
- Trivial changes (typo fix, single-line config change)
- The project already has a CONTEXT.md you read this session

## Integration

- Works with **shared-language** (reads CONTEXT.md)
- Precedes **feature-dev** understand phase
- Complements **handoff** — if receiving a handoff, zoom-out may not be needed
