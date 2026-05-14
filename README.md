# Square

Square is a personal block-based sandbox app.

It uses this hierarchy:

```text
Bookcase > Book > Page/SubPage > Block
```

## What Square Is

Square is designed to let the user build personal dashboards, work automation pages, document helper pages, and mini tool panels by arranging and connecting blocks.

It combines ideas from:

- Notion-style blocks
- PowerPoint-style free placement
- Excel-style references and formulas
- Obsidian-style relationship graph
- Personal dashboard / launcher tools

## Current Target

Current development target:

```text
Square v0.1
```

## v0.1 Goal

Build the basic block canvas engine.

Required features:

- One default Book
- Multiple Pages
- SubPages
- Page tree
- Page switching
- Block creation
- Block movement
- Block resizing
- Block text editing
- Block deletion
- Basic Block style editing
- localStorage save/load
- JSON export/import

## Not in v0.1

Do not implement yet:

- Formula
- Relation
- Graph View
- Calendar
- Document processing
- Google integration
- HTML Module
- Backend
- Login

## Tech Stack

Initial stack:

```text
React
TypeScript
Vite
CSS
localStorage
JSON export/import
```

## Development Context

Read these files before coding:

```text
SQUARE_CONTEXT.md
CODEX_TASK_v0.1.md
DEVELOPMENT_RULES.md
ROADMAP.md
```

## Development Style

The user prefers full-file replacement.

When modifying code, provide full file contents instead of small patch fragments.
