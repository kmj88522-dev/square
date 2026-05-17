# Codex Task: Square v0.2 Block Actions

## Read First

Before coding, read:

1. `SQUARE_CONTEXT.md`
2. `DEVELOPMENT_RULES.md`
3. `ROADMAP.md`
4. `DO_NOT_REGRESS.md`
5. `SQUARE_INTERACTION_MODEL.md`
6. `BLOCK_FUNCTIONS_SPEC.md`

Important:

The existing UI and features must not regress.

---

## Task Goal

Add the first safe block interaction system to Square.

Implement:

```text
Edit Mode / Run Mode
Block click actions
Action builder UI
Page navigation action
Block show/hide/toggle actions
Open URL action
```

Do not implement full Formula yet.

---

## Required Features

### 1. App Mode

Add:

```ts
type AppMode = "edit" | "run";
```

UI:

```text
[Edit Mode] [Run Mode]
```

Behavior:

- Edit Mode: clicking block selects it.
- Run Mode: clicking block executes its click actions.

Default:

```text
Desktop: edit
Mobile: allow toggle
```

If automatic mobile detection is risky, just provide mode toggle for now.

---

### 2. Block Actions Data

Add optional `actions` to Block.

```ts
type BlockAction = {
  id: string;
  event: "click";
  type: "go_page" | "show_block" | "hide_block" | "toggle_block" | "open_url";
  targetCode?: string;
  url?: string;
  enabled: boolean;
};
```

Do not remove existing block fields.

---

### 3. Action Builder UI

In selected Block property panel, add an "Actions" section.

It should allow:

- Add action
- Remove action
- Select action type
- Select target Page or Block by code/title
- Enter URL for open_url
- Enable/disable action

Keep UI simple.

---

### 4. Action Execution

When in Run Mode and a block is clicked:

- Find enabled click actions.
- Execute them in order.

Supported behavior:

```text
go_page      -> set currentPageId to target Page
show_block   -> target.visible = true
hide_block   -> target.visible = false
toggle_block -> target.visible = !target.visible
open_url     -> window.open(url, "_blank")
```

If target is missing:

- Do not crash.
- Show console warning or UI warning.

---

### 5. Preserve Existing Behavior

Do not break:

- Page creation
- SubPage creation
- Block creation
- Block drag
- Block resize
- Block text editing
- Style editing
- localStorage save/load
- JSON export/import
- Mobile UI improvements
- Responsive layout improvements

---

## Explicitly Do Not Implement

Do not implement:

- Formula parser
- IF / AND / OR logic
- Multi-step automation editor
- Graph View
- Calendar
- Document processing
- Google integration
- HTML Module
- External code execution
- Backend

---

## Manual Test Checklist

After implementation, verify:

1. In Edit Mode, clicking a block selects it.
2. In Edit Mode, clicking a block does not navigate.
3. Add a button block.
4. Add `go_page` action to it.
5. Switch to Run Mode.
6. Click button block.
7. App navigates to target Page.
8. Add `toggle_block` action.
9. Click in Run Mode toggles target block visibility.
10. Add `open_url` action.
11. URL opens in new tab.
12. Save/load preserves actions.
13. JSON export/import preserves actions.

---

## Output Format

Respond with:

1. Changed file list
2. Summary
3. Full contents of changed files
4. How to test
5. Known limitations
6. Next recommended task
