# 🧭 Guide: setting up GitHub Projects for Nido

First time using GitHub Projects, so this is step by step. 📸 marks the moments worth capturing for the portfolio and LinkedIn.

## 1. Create the Project
1. Your profile → **Projects** tab → **New project** → template **Board**.
2. Name it `Nido — Roadmap`.
3. Inside the Project: **⋯ → Settings → Manage access** and link it to the `nido` repo (**Link a repository**).

## 2. Custom fields (Settings → Custom fields)
| Field | Type | Values |
|---|---|---|
| Status | Single select (already exists) | Backlog · Ready · In progress · In review · Done |
| Priority | Single select | P0 · P1 · P2 |
| Size | Single select | XS · S · M · L · XL |
| Sprint | **Iteration** | 2 weeks, starting on Monday |
| Epic | Single select | EPIC-0 … EPIC-6 |

> 💡 The **Iteration** field is what turns the board into real sprints.

## 3. Views
1. **Board**, grouped by Status and filtered by `sprint:@current` → the current sprint board.
2. **Backlog**, as a Table grouped by Epic and sorted by Priority.
3. **Roadmap**, as a Roadmap view using the Sprint field → the timeline. 📸 This screenshot works really well on LinkedIn.

## 4. Repo labels
`type:story` · `type:spike` · `type:bug` · `type:chore` · `security` · `ai` · `docs`

## 5. Issue templates
`.github/ISSUE_TEMPLATE/user-story.yml` and `spike.yml` (we'll create them together).

## 6. Automations (Project → ⋯ → Workflows)
- *Item added to project* → Status = Backlog
- *Pull request merged* → Status = Done
- *Item closed* → Status = Done

## 7. Sprint routine
| Moment | What to do | 📸 |
|---|---|---|
| Planning (Monday) | Move stories from Backlog to Ready, assign the sprint, write or review the **specs** | Board at sprint start |
| During the sprint | One branch per issue (`feat/US-2.3-rent-ratio`), one PR with `Closes #N` | — |
| Review (Friday, week 2) | Demo plus a GIF of what works | Feature GIF |
| Retro | What went well, what to improve, what I learned → [process log](process-log.md) | Board at sprint end |
