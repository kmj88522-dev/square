# Square Do Not Regress Rules

## Critical Rule

Never use planning documents as permission to delete existing working features.

If the current code already has working UI or functionality beyond the written task scope, preserve it unless the user explicitly asks to remove it.

The scope means:

```text
Do not add unnecessary new features.
```

It does not mean:

```text
Delete existing features.
```

---

## Before Editing

Before changing code:

1. Inspect current files.
2. Identify existing working features.
3. Preserve them.
4. Make the smallest change needed for the task.

---

## High-Risk Areas

Be careful not to regress:

- Mobile layout
- PC layout
- Page tree
- Block canvas
- Dragging
- Resizing
- Text editing
- Style panel
- localStorage
- JSON export/import
- Asset/logo paths
- Grid snapping
- Responsive layout

---

## Safe Coding Rule

When adding a feature:

- Add new types without removing old fields.
- Maintain backward compatibility.
- Do not replace the entire app with a smaller example.
- Do not remove existing UI panels unless explicitly requested.
- Do not rename major concepts without instruction.

---

## Recovery Rule

If a change causes regression:

1. Stop adding features.
2. Restore the last working behavior.
3. Explain what caused regression.
4. Reapply the task in smaller steps.
