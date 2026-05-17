# CONTEXT.md — RVM Merchant Platform

## Domain Language
- **RVM** → Reverse Vending Machine (AI recycling kiosk, 10 units deployed)
- **UCO** → Used Cooking Oil (accepted by machines, stored in 40L/60L bins)
- **Submission** → Single recycling event at a machine (weight + material type)
- **Points** → Weight (kg) × 0.2 = Points earned
- **PNC** → Project Name Confidential (pre-announcement deals)
- **DBKL** → Kuala Lumpur City Hall (30,000+ F&B outlets mandatory)
- **KDEBS** → Selangor state waste management arm
- **TELD** → EV charging infrastructure partner (China), JV via ARBB
- **ARBB** → Arbiot Group (NASDAQ-listed), TELD Malaysia JV parent

## Architecture
- **Supabase (PostgreSQL)** → primary data store (users, submissions, withdrawals)
- **Vercel** → Frontend hosting (rvm-merchant-platform-main.vercel.app)
- **AliCloud ECS** (47.250.88.132) → app.mygreenplus.com + nginx reverse proxy
- **Vendor API** (api.autogcm.com) → real machine telemetry (weight, temp, status)
- **Bridgewell Site** (bridgewell-site.vercel.app) → CIRCLE token presale

## Key Systems
| System | Location | Tech |
|--------|----------|------|
| User App | app.mygreenplus.com | Vue.js (patched JS) |
| Admin Dashboard | rvm-merchant-platform-main.vercel.app | Vue + TypeScript |
| CIRCLE Site | bridgewell-site.vercel.app | Vanilla HTML/JS |
| Trading Bot | ~/AI_Trading/combined_trading_bot/ | Python, Hyperliquid |
| Keep Fit Tracker | routines/weight-tracker.md | Markdown |

## Key Decisions
- Balance = SUM(approved submissions - withdrawals via submission_reviews table)
- All withdrawals must be approved by admin before payout
- CIRCLE is BSC BEP-20 (not ERC-20), upgradeable via UUPS proxy
- User profile bug on Vercel: uses eq('id') instead of eq('user_id') — needs source fix

## Pending
- [ ] Synology NAS backup (source code + Supabase pg_dump)
- [ ] User app rebuild from source (current is patched JS on AliCloud)
- [ ] CIRCLE presale — zero investors so far
