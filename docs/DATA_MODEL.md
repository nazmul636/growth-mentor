# Growth Mentor — Data Model

## visions
| field | type |
|---|---|
| id | uuid pk |
| user_id | uuid nullable |
| title | text not null |
| description | text |
| horizon_years | int default 10 |
| created_at | timestamptz default now() |

## pillars
| field | type |
|---|---|
| id | uuid pk |
| name | text not null |
| slug | text unique not null |
| created_at | timestamptz default now() |

## goals
| field | type |
|---|---|
| id | uuid pk |
| user_id | uuid nullable |
| vision_id | uuid fk→visions |
| pillar_id | uuid fk→pillars |
| title | text not null |
| description | text |
| term | text check in ('short','long') |
| target_date | date |
| status | text default 'active' check in ('active','completed','paused') |
| created_at | timestamptz default now() |

## weekly_scorecards
| field | type |
|---|---|
| id | uuid pk |
| user_id | uuid nullable |
| goal_id | uuid fk→goals |
| week_start_date | date not null |
| effort_rating | int check 1–5 |
| progress_note | text |
| self_assessment | text |
| created_at | timestamptz default now() |

## weekly_insights (AI-generated)
| field | type |
|---|---|
| id | uuid pk |
| user_id | uuid nullable |
| scorecard_week | date not null |
| insight_text | text |
| source | text |
| confidence | numeric |
| review_status | text default 'unreviewed' check in ('unreviewed','accepted','rejected') |
| created_at | timestamptz default now() |

## Relationships
- Goal → Vision (many-to-one), Goal → Pillar (many-to-one)
- WeeklyScorecard → Goal (many-to-one)
- WeeklyInsight → referenced by scorecard_week (one insight per week)

## RLS Notes
- v1: all tables open read/write (permissive policies) for demo.
- Lock-down: owner-scoped via `auth.uid() = user_id`.
- pillars table is shared/reference — read-only for all.