# Square Interaction Model

## 0. Purpose

This document defines the first interaction model for Square.

Square must not jump directly into complex automation.  
First, implement a small, safe, understandable block interaction system.

---

## 1. Core Rule

Only **Block** can be an action subject.

```text
Block = action subject
Bookcase / Book / Page = action targets or containers
```

Examples:

```text
Block click -> open Page
Block click -> toggle another Block
Block click -> open URL
Block click -> show preview
```

Do not make Book or Page execute actions directly in early versions.

---

## 2. Interaction Structure

Every block interaction should follow this pattern:

```text
Event -> Action -> Target
```

Example:

```text
click -> TOGGLE -> B005
click -> GO_PAGE -> P002
click -> OPEN_URL -> https://example.com
```

---

## 3. Events

Initial supported events:

```ts
type BlockEventType =
  | "click"
  | "doubleClick"
  | "longPress"
  | "change";
```

### v0.2 Recommendation

Implement only:

```text
click
```

Other events are future-ready only.

---

## 4. Actions

Initial supported actions:

```ts
type BlockActionType =
  | "go_page"
  | "show_block"
  | "hide_block"
  | "toggle_block"
  | "open_url"
  | "set_text";
```

### v0.2 Recommendation

Implement only:

```text
go_page
show_block
hide_block
toggle_block
open_url
```

`set_text` can be reserved for later.

---

## 5. Targets

Action targets may be:

```text
Block
Page
URL
```

Book and Bookcase targets can be added later.

---

## 6. Block Action Type

Recommended type:

```ts
type BlockAction = {
  id: string;
  event: "click" | "doubleClick" | "longPress" | "change";
  type: "go_page" | "show_block" | "hide_block" | "toggle_block" | "open_url" | "set_text";
  targetCode?: string;
  url?: string;
  value?: string;
  enabled: boolean;
};
```

Rules:

- `targetCode` uses user-facing codes such as `B005` or `P002`.
- The system must resolve `targetCode` to internal ids.
- If target is missing, do not crash.
- Broken references should be shown as warnings later.

---

## 7. Formula vs Action Builder

Square will eventually support formulas like:

```text
=GO(@P002)
=TOGGLE(@B005)
```

But early versions should use an Action Builder UI first.

User-friendly UI:

```text
When: click
Do: toggle block
Target: B005 / Memo Panel
```

Internal action data:

```json
{
  "event": "click",
  "type": "toggle_block",
  "targetCode": "B005",
  "enabled": true
}
```

Formula can be generated later from this structured action.

---

## 8. Initial Action Builder UI

For selected Block, show an Action section in the right property panel or mobile bottom sheet.

Fields:

```text
Event: click
Action: go_page / show_block / hide_block / toggle_block / open_url
Target: selectable Page or Block
URL: shown only for open_url
Add action
Remove action
Enable/disable action
```

---

## 9. Execution Rules

When a block is clicked:

1. Select the block.
2. If user is in edit mode, do not execute action immediately unless action-run mode is enabled.
3. If user is in run/preview mode, execute the block's click actions.

Early simple policy:

```text
Edit mode: clicking selects block.
Run mode: clicking executes action.
```

This avoids accidental navigation while editing.

---

## 10. Modes

Square needs at least two modes:

```text
Edit Mode
Run Mode
```

### Edit Mode

- Select blocks
- Drag blocks
- Resize blocks
- Edit properties
- Configure actions

### Run Mode

- Blocks behave like buttons/tools
- Click actions execute
- Editing UI is hidden or minimized

This is important for mobile.

---

## 11. Do Not Implement Yet

Do not implement in v0.2:

- Multi-step workflows
- IF conditions
- Loops
- Variables
- Full Formula parser
- Graph View editing
- External API calls
- Document automation
- Google integration
- Code execution
