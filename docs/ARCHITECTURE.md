# Growth Mentor — Architecture

## Stack
Next.js (App Router) + Supabase (Postgres + RLS) + Vercel. Tailwind for styling. AI via server-side module calling an LLM API.

## Build Sequence
**Now (v1):** Vision + Goals CRUD → Weekly Scorecard CRUD → Scorecard summary view → AI insight on scorecards.
**Next:** Scorecard history charts, streaks, goal completion flow, insight refinement.
**Later:** Auth + per-user RLS, mentor-student relationships, reminders, export.

## Key User Flow (Weekly Scorecard)
1. User opens the current-week scorecard page.
2. Picks a goal from the list.
3. Enters effort (1–5), writes a progress note, self-assesses.
4. Saves → persisted to `weekly_scorecards` table.
5. Scorecard appears in the week summary grid.
6. User clicks "Generate Insight" → server calls AI module → insight stored in `weekly_insights` with source/confidence/review_status.
7. User can accept, reject, or regenerate the insight.

## Responsive Nav Shell
Left sidebar on desktop (Vision, Goals, Weekly Scorecard, History) collapsing to a hamburger menu on mobile. Current section highlighted.

## Layer Plan
1. **Data layer** — Supabase tables, RLS policies, data-access module (`lib/data/`) — all reads/writes go through here.
2. **App logic** — Server actions for scorecard CRUD, goal CRUD, vision CRUD (`lib/actions/`).
3. **Intelligence** — AI insight generation in its own module (`lib/ai/`), called by server actions, never inline in UI.

## Why Core Works Without AI
Vision, goals, and scorecards are pure CRUD + display. The AI insight is an add-on button; the scorecard summary and history render fully without it.

## Repo Structure
```
app/                    # routes + UI components
  vision/
  goals/
  scorecard/
  history/
  components/
lib/data/                # all Supabase queries/mutations
lib/actions/             # server-side logic
lib/ai/                  # insight generation
__tests__/               # tests beside code
```