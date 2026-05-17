# Codex Safe Start Prompt for Square v0.2

Copy this into Codex.

---

Read all attached markdown files first.

Important:

The previous markdown task caused UI regression because the v0.1 scope was interpreted as permission to simplify the app.

Do not do that.

The markdown files are guidance.  
They must not be used to delete, downgrade, or simplify existing working UI/features.

## Current Task

Implement **Square v0.2 Block Actions** only.

Use:

- `DO_NOT_REGRESS.md`
- `SQUARE_INTERACTION_MODEL.md`
- `BLOCK_FUNCTIONS_SPEC.md`
- `CODEX_TASK_v0.2_BLOCK_ACTIONS.md`

## Preserve Existing Features

Do not break or remove:

- Current mobile UI
- Current PC UI
- Existing block creation
- Existing drag/resize
- Existing style editing
- Existing Page/SubPage system
- Existing save/load/export/import
- Existing responsive behavior
- Existing logo handling
- Existing grid snapping fixes if present

## Implement Only

- Edit Mode / Run Mode
- Block actions data
- Action builder UI for selected block
- go_page
- show_block
- hide_block
- toggle_block
- open_url

## Do Not Implement

- Formula parser
- Conditionals
- Multi-step workflows
- Graph View
- Calendar
- Document processing
- Google integration
- HTML module
- Backend/login

## Before Changing Code

First inspect current files and summarize what currently exists.

Then make the smallest safe changes.

## Output

Provide full file contents for changed files.
