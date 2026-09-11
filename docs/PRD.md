# Growth Mentor — PRD

## Problem
Personal-growth coaching is expensive and inconsistent. People optimize for marginal improvements and get stuck in safe, linear cycles instead of aiming for exponential potential.

## Target User
A builder and their students — individuals who want to track goals, health, soft-skill development, and education against a 10-year vision and hold themselves accountable weekly.

## Core Objects
- **Vision** — a 10-year aspirational statement that constrains all goals.
- **Goal** — short-term or long-term, linked to a vision, with a target date and status.
- **Pillar** — category: Health, Soft Skills, Education, Career/Growth.
- **Weekly Scorecard** — a week-scoped check-in per goal: effort rating (1–5), progress note, self-assessment, and AI-generated insight.
- **WeeklyInsight** — AI-generated summary of the week's scorecards (value + source + confidence + review_status).

## MVP (v1) — Checklist
- [ ] Create/edit a 10-year Vision statement.
- [ ] Create/edit Goals (short-term/long-term) assigned to a Pillar and Vision.
- [ ] Log a Weekly Scorecard per goal: effort (1–5), progress note, self-assessment.
- [ ] View the current week's scorecard summary across all goals.
- [ ] AI insight on the weekly scorecard (generated, reviewable, can regenerate).
- [ ] Scorecard history view (past weeks).

## Non-Goals (v1)
- Human check-ins / coach intervention.
- Social or multi-user collaboration.
- Notifications / reminders.
- Billing or subscriptions.
- Custom pillar creation.

## Success Criteria
**End-to-end scenario:** A user opens the app (no login), sees the seeded vision and goals, creates a new weekly scorecard for one goal with effort 4 and a progress note, saves it, sees the scorecard appear in the current-week summary, triggers an AI insight, and reviews it — all persisted to the database and visible on refresh.