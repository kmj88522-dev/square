# Codex Task: Build Square v0.1

## Read First

Before coding, read these files in the repository root:

1. `SQUARE_CONTEXT.md`
2. `DEVELOPMENT_RULES.md`
3. `ROADMAP.md`
4. `README.md`

Follow those documents.  
Do not expand the project scope beyond v0.1.

---

## Task Summary

Build **Square v0.1**, a minimal React + TypeScript + Vite app.

Square v0.1 is a basic block canvas engine with:

```text
Book > Page/SubPage > Block
```

Bookcase is a future concept and may be represented in data, but a full Bookcase dashboard is not required in v0.1.

---

## Required v0.1 Features

Implement these only:

1. One default Book
2. Multiple Pages
3. SubPages using `parentPageId`
4. Page tree in left sidebar
5. Page switching
6. Block creation
7. Block drag movement
8. Block resizing
9. Block selection
10. Block text editing
11. Block deletion
12. Basic Block style editing:
   - background color
   - text color
   - font size
   - border radius
   - shadow on/off
13. localStorage save/load
14. JSON export/import

---

## UI Layout

Use a simple 4-part layout:

```text
Top Bar
Left Sidebar | Center Canvas | Right Property Panel
```

### Top Bar

Include:

- App name: Square
- Save button
- Load button
- Export JSON button
- Import JSON button

### Left Sidebar

Include:

- Book title
- Page tree
- Add Page button
- Add SubPage button

### Center Canvas

Include:

- Current Page title/code
- Add Block button
- Free-position block canvas

### Right Property Panel

Show selected Block information and editable style fields.

If no block is selected, show a simple empty state.

---

## Block Behavior

- Clicking a block selects it.
- Dragging a block moves it.
- Resizing handle at the bottom-right resizes it.
- Double-clicking a block edits its text.
- Delete button removes the selected block.
- Selected block should have a visible outline.

---

## Data Rules

Use both internal id and user-facing code.

Examples:

```text
Book = BK001
Page = P001, P002...
Block = B001, B002...
```

Do not reuse deleted codes.

Use localStorage key:

```ts
"square:v0.1:state"
```

---

## Technical Rules

- React
- TypeScript
- Vite
- Avoid external UI libraries.
- Prefer a simple single-file implementation in `src/App.tsx` for v0.1.
- CSS may be inside `App.tsx` or `src/App.css`.
- Keep code understandable.
- Do not over-engineer.

---

## Explicitly Do Not Implement

Do not implement:

- Formula system
- Relation system
- Graph View
- Calendar Block
- Document Block
- Google Drive integration
- Google Sheets integration
- Google Calendar integration
- HTML Module Block
- PDF/HWPX/DOCX processing
- Code execution block
- Backend server
- Login/account system
- Complex animations
- External UI framework unless absolutely necessary

---

## Expected Output

After implementation, provide:

1. Changed file list
2. Full contents of changed files
3. How to run
4. What works
5. Known limitations
6. Next recommended task
