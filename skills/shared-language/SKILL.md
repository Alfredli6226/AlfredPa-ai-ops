---
name: shared-language
description: Per-project domain glossary and architectural context. When you read CONTEXT.md before each session, you work faster and make fewer wrong assumptions.
---

# Shared Language / CONTEXT.md

## Purpose

Every project accumulates jargon, abbreviations, architectural decisions, and unwritten rules. Without a shared language doc, agents waste tokens guessing terms and make mistakes that a 30-second read would have prevented.

This skill ensures that before working on any project, you either read its existing CONTEXT.md or create one.

## Workflow

### Before starting work on any project

1. Check if `CONTEXT.md` exists in the project root
2. If yes → **read it first**
3. If no → offer to create one (see below)

### What goes in CONTEXT.md

Keep it tight. Aim for 1-2 pages max. These sections:

```
# CONTEXT.md — [Project Name]

## Domain Language
- Term → Definition
- Abbreviation → What it means
- Avoid → Words that mean something else

## Architecture
- High-level structure
- Key data flow
- Where to find things

## Key Decisions (ADRs)
- Decision → Why
- Date → What changed
```

### When to create/update

**Create** when working on a project that lacks one and you spot jargon or confusion.

**Update** when:
- The team agrees on new terminology
- An architectural change is made
- A decision is reversed

### Example

```
# CONTEXT.md — RVM Merchant Platform

## Domain Language
- RVM → Reverse Vending Machine (AI recycling kiosk)
- UCO → Used Cooking Oil (a waste type accepted by machines)
- Points → Weight × 0.2 (earned per kg recycled)
- Submission → A single recycling event at a machine
- PNC → Project Name Confidential (pre-announcement deals)
- DBKL → Kuala Lumpur City Hall
- KDEBS → Selangor state waste management

## Architecture
- Supabase (PostgreSQL) → primary data store
- Vercel → frontend hosting
- AliCloud ECS → backend server (app.mygreenplus.com)
- Vendor API (api.autogcm.com) → real machine data

## Key Decisions
- All recycling weighting and pricing decisions go through submission_reviews table (not direct)
- User balance = SUM(approved submissions) - SUM(withdrawals)
- CIRCLE token is BSC BEP-20, not ERC-20
```

## Integration

This skill works with:
- **handoff** — include relevant CONTEXT.md points in handoff documents
- **zoom-out** — read CONTEXT.md as part of the zoom-out step
- **feature-dev** — read CONTEXT.md during the understand phase
