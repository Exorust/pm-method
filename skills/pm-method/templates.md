# Templates

Copy these shapes. Keep them this short.

## pm/FEATURES.md

```markdown
# Features — <project>
As of: <date>. Approved by user: <yes/no>.

## User types
- <type>: <one line on what they want>

## Features
| id | feature | user type | state | source of intent |
|---|---|---|---|---|
| F1 | <name> | <type> | built / partial / missing | README §2 / issue #14 / interview |

## Out of scope
- <thing the user said no to>

## Unplanned (found in code, in no intent source — keep or delete?)
- <thing>
```

## pm/flows/<id>.md

```markdown
# F1 — <feature name>

## Flow F1.1 — <task>
Preconditions: <state the software must be in>
| step | action | expected result (observable) |
|---|---|---|
| 1 | open /signup | form with fields email, password is visible |
| 2 | submit valid email | text "Check your inbox" is visible |
| 3 | enter wrong code | text "Code not recognised" is visible; still on /verify |

## Flow F1.2 — <error path>
...
```

## pm/journeys.md

```markdown
# Journeys

## J1 — <user type>: <goal in one line>
Crosses: F1, F3, F4
| step | action | expected result (observable) |
|---|---|---|
| 1 | ... | ... |
```

## pm/STATUS.md

```markdown
# Status — run <date>

| id | status | attempts | evidence | files changed |
|---|---|---|---|---|
| F1.1 | solved | 1 | evidence/2026-10-17/F1.1/ | src/auth.ts |
| F2.1 | blocked | 3 | evidence/2026-10-17/F2.1/ | src/import.ts |
| F3.1 | reviewed-not-verified | 0 | — | — |
| J1 | solved | 0 | evidence/2026-10-17/J1/ | — |

## Blocked
- F2.1: step 3 — expected "Import complete", observed 500 from /api/import. Last error: <one line>.

## Reviewed, not verified — why
- F3.1: Android launcher, no emulator in this environment.
```

## pm/FRICTION.md

```markdown
# Friction — advisory, never blocks a pass

| journey | step | note |
|---|---|---|
| J1 | 4 | three confirmations to invite one teammate; one would do |
```

## Builder brief (what the PM sends)

```
You are the builder agent for the PM Method. The PM agent has walked a user
flow and it failed (or the feature is not built yet).

FLOW (verbatim):
<flow file>

FAILING STEP: <n>. Expected: <text>. Observed: <text>.
EVIDENCE: <path>

RULES
- Edit application code only. Never touch anything under pm/.
- Never weaken, skip, or delete a check. If you believe the expected result
  is wrong, stop and say so; do not change it.
- Leave all changes uncommitted.
- One fix attempt, then report: what you changed, every file touched, what
  you expect the walk to show now.
```
