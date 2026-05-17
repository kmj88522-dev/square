# Square Naming and Square Types

## 0. Purpose

This document preserves future design ideas for Square.

This is **not** an immediate implementation task. Do not rewrite the current app only because this document exists.

Use this as a long-term design reference after Square v0.2 Block Actions are stable.

---

## 1. Naming Direction

The app name is **Square**.

The basic object currently called `Block` may be shown to the user as **Square**.

### Recommended Naming Policy

```text
User-facing UI term: Square
Internal code term: SquareBlock or Block
```

Examples:

```text
Add Block       -> Add Square
Text Block      -> Text Square
Button Block    -> Button Square
Content Block   -> Content Square
```

Using "Square" as the user-facing term gives the product a stronger identity.

---

## 2. Caution About Renaming

Do not immediately rename every internal type.

Internal code may keep using:

```ts
SquareBlock
Block
BlockAction
```

Changing all internal names too early can cause bugs.

Recommended migration:

```text
Step 1: Keep internal types as Block/SquareBlock.
Step 2: Change visible UI labels from Block to Square.
Step 3: Later consider code reference migration from B001 to S001.
```

---

## 3. Object Code Direction

Current code style may be:

```text
B001 = Block
```

Long-term user-facing code may become:

```text
S001 = Square
```

Recommended long-term code system:

```text
BC001 = Bookcase
BK001 = Book
P001  = Page
S001  = Square
```

### Migration Policy

Do not force this migration in the middle of active feature work.

If existing data already uses `B001`, keep supporting it.

Future migration should be backward-compatible.

---

## 4. Square Categories

Square objects should eventually be organized into categories.

Recommended categories:

```text
1. Design Square
2. Content Square
3. Control Square
4. Navigation Square
5. Collection Square
6. Time Square
7. Tool Square
8. Value Square
```

---

## 5. Design Square

Design Squares are for visual layout and decoration.

Examples:

- Rectangle
- Line
- Divider
- Background panel
- Card frame
- Section box
- Icon box
- Shadow box
- Decorative button shape

Purpose:

```text
Make the page visually structured.
```

---

## 6. Content Square

Content Squares hold information.

Examples:

- Text
- Image
- Sound
- Video
- YouTube embed
- Google Map view
- Document preview
- Memo
- Web page embed
- File preview

Purpose:

```text
Show or store content inside the page.
```

---

## 7. Control Square

Control Squares execute actions.

Examples:

- Button
- Show Square
- Hide Square
- Toggle Square
- Save
- Copy
- Reset
- Run
- Preview
- Close
- Collapse / Expand

Purpose:

```text
Trigger behavior.
```

---

## 8. Navigation Square

Navigation Squares move the user to another place.

Examples:

- Open Page
- Open Book
- Open Bookcase
- Open URL
- Open Google Drive file
- Open Firemap
- Open recent page
- Open favorite page

Purpose:

```text
Move between places or open resources.
```

Navigation Square can be considered a subcategory of Control Square, but it may deserve separate UI because it will be used often.

---

## 9. Collection Square

Collection Squares show lists of other objects.

Examples:

- Page list
- Square list
- Favorite list
- Recent items
- To-do list
- Routine list
- Document template list
- Fire water facility list
- Book list
- Bookcase list

Purpose:

```text
Show a group of related objects.
```

---

## 10. Time Square

Time Squares show or calculate time-related information.

Examples:

- Current time
- Today date
- Day of week
- Digital clock
- Time bar
- Countdown
- Timer
- Stopwatch
- Work progress
- Duty shift remaining time
- Schedule progress

Purpose:

```text
Show time, duration, progress, and schedule context.
```

---

## 11. Tool Square

Tool Squares run mini tools.

Examples:

- Calculator
- QR generator
- Firemap
- Duty allowance calculator
- Document template generator
- Google Map tool
- Voice recording tool
- Text converter
- Prompt builder
- Timer
- Checklist tool

Purpose:

```text
Run a small app/tool inside or from Square.
```

Implementation may later use:

```text
HTML Module Square
Web Tool Square
External Tool Launcher
```

---

## 12. Value Square

Value Squares store input values.

Examples:

- Text input
- Number input
- Date picker
- Time picker
- Date range picker
- Checkbox
- Dropdown
- Slider
- File picker
- Page picker
- Square picker

Purpose:

```text
Hold values that other Squares can read.
```

Future formula example:

```text
=VALUE(@S001)
```

---

## 13. First Practical Type Priorities

Do not build all Square types at once.

Recommended order:

```text
1. Text Square
2. Button Square
3. Design Square
4. Navigation Square
5. Value Square
6. Collection Square
7. Time Square
8. Tool Square
```

---

## 14. Implementation Warning

This document describes future taxonomy.

Do not use this document to:

- Rewrite the current app
- Remove working features
- Rename internal types prematurely
- Break existing B001 code references
- Implement all Square types at once
