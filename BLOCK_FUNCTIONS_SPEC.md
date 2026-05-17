# Square Block Functions Spec

## 0. Purpose

This document defines the first practical block functions for Square.

The goal is to make Blocks useful without making the system too complex.

---

## 1. Block Roles

Initial roles:

```ts
type BlockRole = "content" | "control" | "module";
```

### content

Displays information.

Examples:

- Text Block
- Image Block
- Memo Block

### control

Triggers actions.

Examples:

- Button Block
- Open Page Block
- Toggle Block
- Close Block

### module

Runs or embeds tools.

Not required in v0.2.

---

## 2. Initial Block Types

v0.2 should support or prepare:

```ts
type BlockType =
  | "text"
  | "button"
  | "container";
```

Recommended behavior:

### text

- Displays and edits text.
- Can still have actions later.

### button

- Looks like a button.
- Best default type for actions.

### container

- Visual grouping block.
- Child block behavior can be added later.

---

## 3. Essential Block Properties

Each block should have:

```ts
type SquareBlock = {
  id: string;
  code: string;
  bookId: string;
  pageId: string;
  parentBlockId?: string;

  type: "text" | "button" | "container";
  role: "content" | "control" | "module";

  x: number;
  y: number;
  width: number;
  height: number;

  content: {
    text?: string;
  };

  value?: string | number | boolean | null;

  style: {
    backgroundColor: string;
    backgroundTransparent?: boolean;
    textColor: string;
    fontSize: number;
    borderRadius: number;
    shadow: boolean;
  };

  actions?: BlockAction[];

  visible: boolean;
  locked: boolean;
  createdAt: string;
  updatedAt: string;
};
```

---

## 4. First Useful Functions

### 1. Open Page Button

Purpose:

```text
Click block -> go to target Page
```

Action:

```json
{
  "event": "click",
  "type": "go_page",
  "targetCode": "P002",
  "enabled": true
}
```

### 2. Toggle Block Button

Purpose:

```text
Click block -> show/hide target Block
```

Action:

```json
{
  "event": "click",
  "type": "toggle_block",
  "targetCode": "B005",
  "enabled": true
}
```

### 3. Show Block Button

```json
{
  "event": "click",
  "type": "show_block",
  "targetCode": "B005",
  "enabled": true
}
```

### 4. Hide Block Button

```json
{
  "event": "click",
  "type": "hide_block",
  "targetCode": "B005",
  "enabled": true
}
```

### 5. Open URL Button

```json
{
  "event": "click",
  "type": "open_url",
  "url": "https://example.com",
  "enabled": true
}
```

---

## 5. Edit Mode vs Run Mode

Block actions should not interfere with editing.

Required modes:

```ts
type AppMode = "edit" | "run";
```

### Edit Mode

Clicking a block selects it.

### Run Mode

Clicking a block executes its click actions.

---

## 6. Mobile UX

Mobile should encourage Run Mode.

Recommended mobile UI:

```text
Default: Run/View mode
Edit button: opens editing controls
```

This keeps the page area large.

---

## 7. Broken References

If an action references a missing target:

- Do not crash.
- Show warning in property panel.
- Later show warning in Relation/Graph View.

Example:

```text
Target @B099 not found
```

---

## 8. Do Not Add Yet

Do not add these until the basic action system works:

- Formula parser
- Conditionals
- Multi-action chains
- Variables
- Data tables
- Calendar action automation
- Document generation
- Google integrations
