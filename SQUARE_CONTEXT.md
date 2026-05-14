# Square Project Context

## 0. Purpose

This document is the canonical context for **Square**.

Use it to prevent development drift when working with Codex, ChatGPT, or other AI coding tools.

---

## 1. Project Name

**Square**

Previous spelling `Sqaure` was a typo.  
The correct project name is **Square**.

---

## 2. One-Line Definition

**Square is a personal block-based sandbox app where the user builds dashboards, tools, workflows, and automation pages by arranging and connecting blocks.**

---

## 3. Core Hierarchy

```text
Bookcase > Book > Page/SubPage > Block
```

### Meaning

```text
Bookcase = Home dashboard / bookshelf
Book     = Project
Page     = One screen inside a Book
SubPage  = Page with parentPageId
Block    = Basic object, content unit, value holder, and action unit
```

---

## 4. Bookcase

**Bookcase** is the home dashboard shown when the app opens.

The app should not open into an empty screen by default.  
Instead, it should show a user-configured Bookcase.

Bookcase is like a bookshelf and dashboard combined.

It can show:

- Book preview cards
- Recently used Books
- Recently used Pages
- Favorite Pages
- Favorite Blocks
- Quick action buttons
- Calendar preview
- Today summary
- Work status summary
- Info graphics
- Mini dashboards
- External tool launch buttons

Bookcase is not a replacement for Book.  
It is a higher-level dashboard that references multiple Books.

### Future Structure

Technically, Bookcase may also contain Blocks, but these are dashboard-level blocks.

Example:

```text
Bookcase
├─ Work Book Preview
├─ Calendar Widget
├─ Firemap Quick Launch
├─ Today Duty Status
├─ Recent Pages
└─ Favorite Action Buttons
```

### MVP Policy

Bookcase is important, but it does **not** need to be fully implemented in v0.1.

Suggested roadmap:

```text
v0.1: Book/Page/Block core engine
v0.2: Basic Bookcase screen
v0.3: Book preview blocks and quick action blocks
```

---

## 5. Book

A **Book** is a project.

Examples:

- Work Assistant Book
- Personal Dashboard Book
- Finance Book
- Novel Writing Book
- Firemap / Fire Water Facility Book

Book manages:

- Pages
- SubPages
- Project-level metadata
- Book-level counters
- Project settings

Book should not directly execute actions.

---

## 6. Page and SubPage

A **Page** is one screen where Blocks are placed.

A Page represents a bounded canvas.  
The user edits within the visible screen area rather than an infinite canvas.

A **SubPage** is not a separate type.  
It is a Page with `parentPageId`.

```text
Page
└─ SubPage
   └─ SubPage
```

Page manages:

- Canvas background
- Grid settings
- Blocks on that Page
- Parent-child page hierarchy

Page should not directly execute actions.

---

## 7. Block

A **Block** is the basic unit of Square.

A Block can be:

- Visual object
- Text container
- Image container
- Button
- Value holder
- Input field
- Selector
- Calendar-related unit
- Document reference
- HTML module container
- External tool launcher
- Automation trigger

### Core Principle

**Only Blocks can be action subjects.**

Book and Page are structure/management objects.  
Block is the object that performs actions.

```text
Action subject: Block only
Action target: Block, Page, Book, Bookcase, URL, external tool
```

---

## 8. Object Code System

All main objects need both:

```text
id   = internal system identifier
code = user-facing stable reference code
```

### Code Examples

```text
Bookcase = BC001
Book     = BK001
Page     = P001
Block    = B001
```

### Rules

- `id` is for internal use.
- `code` is for user reference.
- Codes are used later in Formula and Relation systems.
- Deleted codes should not be reused.
- Codes should remain stable even if the object title changes.
- Moving a Block to another Page should not change its code.

---

## 9. Formula Concept

Square will eventually use simple formulas inspired by Excel.

Formula examples:

```text
=GO(@P002)
=SHOW(@B003)
=HIDE(@B004)
=TOGGLE(@B005)
=OPEN_URL("https://example.com")
=VALUE(@B010)
```

Formula is **not required in v0.1**.

---

## 10. Relation Concept

Relations describe object-to-object connections.

Examples:

```text
B002 click -> GO -> P003
B005 click -> HIDE -> B004
B010 value -> used by -> B011
```

Future relation structure:

```ts
type Relation = {
  id: string;
  sourceType: "block";
  sourceCode: string;
  event: "click" | "doubleClick" | "hover" | "load" | "change";
  formula: string;
};
```

Relation system is **not required in v0.1**.

---

## 11. Graph View

Square should eventually have a simple relationship graph view.

Purpose:

- Visualize Book/Page/Block relationships
- Show Formula connections
- Show dependencies
- Help the user understand logic visually
- Detect broken references

This does not need heavy animation or fancy graph effects.

Initial Graph View can be very simple:

```text
B002 --GO--> P003
B005 --HIDE--> B004
B010 --VALUE--> B011
```

Graph View is **not required in v0.1**.

---

## 12. Block Types: Long-Term Vision

### Content Blocks

- Text Block
- Image Block
- Video Block
- Audio Block
- Link Block
- Document Block

### Input / Value Blocks

- Text Input Block
- Number Input Block
- Date Picker Block
- Time Picker Block
- Date Range Block
- Checkbox Block
- Selector Block
- Scroll Selector Block

### Calendar Blocks

- Calendar Block
- Current Date Block
- Current Time Block
- Day Cell inside Calendar Block
- Duty Status Cell
- Schedule Cell

### Control Blocks

- Button Block
- Close Block
- Toggle Block
- Preview Block
- Save Block
- Run Block
- Open Page Block
- Open Book Block

### Module Blocks

- HTML Module Block
- Web Tool Block
- External App Launcher
- Firemap Tool Block
- Calculator
- Timer
- QR tool

### Document Blocks

- Office Document Block
- PDF Block
- HWPX Block
- Spreadsheet Block
- Template Fill Block

---

## 13. Calendar Direction

Square should eventually have its own Calendar Block.

Recommended approach:

```text
Square Calendar Block = main UI
Google Calendar = sync and notification backend
```

Calendar date cells should behave like special mini-blocks, but should not necessarily be stored as normal Blocks.

A Day Cell may contain:

- Date
- Day of week
- Duty status
- Schedule list
- Linked Page
- Linked Blocks
- Memo
- Display color
- Click action

Calendar is **not required in v0.1**.

---

## 14. Document Direction

Square may eventually support Office/PDF/HWPX-related workflow.

Goal is **not** to become a full document editor.

Correct direction:

```text
Document automation engine, not full word processor.
```

Possible functions:

- Attach document
- Preview document
- Extract text
- Extract tables
- Fill templates
- Generate new document
- Connect document fields to Block values

Important formats:

```text
DOCX
XLSX
PPTX
PDF
HWPX
```

Legacy HWP should preferably be converted to HWPX before processing.

Document processing is **not required in v0.1**.

---

## 15. HTML Module / Web Tool Direction

Square should eventually support small tools inside Blocks.

Examples:

- Firemap
- Calculator
- Timer
- QR generator
- Duty allowance calculator
- Mini dashboard
- Prompt builder

Recommended approach:

```text
HTML Module Block
iframe sandbox
limited message API
```

HTML Module is **not required in v0.1**.

---

## 16. Storage Direction

Recommended storage evolution:

```text
v0.1: localStorage
v0.2: JSON export/import
v0.3: IndexedDB if needed
v0.4+: Google Drive file storage
v0.5+: Google Sheets as index/relation table
v0.6+: Google Docs for long text documents
```

Long-term Google Drive folder concept:

```text
Google Drive/
└─ Square/
   ├─ Books/
   ├─ Assets/
   ├─ Modules/
   └─ Backups/
```

---

## 17. v0.1 Scope

Square v0.1 should be intentionally minimal.

### Required Features

- One default Book
- Multiple Pages
- SubPages through `parentPageId`
- Page tree
- Page switching
- Block creation
- Block selection
- Block drag movement
- Block resizing
- Block text editing
- Basic Block style editing
  - background color
  - text color
  - font size
  - border radius
  - shadow on/off
- Block deletion
- localStorage save/load
- JSON export/import

### Suggested UI

```text
Top Bar
├─ App title
├─ Save
├─ Load
├─ Export JSON
└─ Import JSON

Left Sidebar
├─ Book title
├─ Page tree
├─ Add Page
└─ Add SubPage

Center
└─ Current Page Canvas

Right Sidebar
└─ Selected Block Properties
```

---

## 18. v0.1 Explicit Exclusions

Do **not** implement these in v0.1:

- Formula
- Relation system
- Graph View
- Calendar Block
- Document Block
- Google Drive integration
- Google Sheets integration
- Google Calendar integration
- HTML Module Block
- PDF/HWPX/DOCX processing
- Code execution Block
- Backend server
- Login/account system
- Complex animation
- External UI framework unless absolutely necessary

---

## 19. Suggested v0.1 Data Types

```ts
type SquareBookcase = {
  id: string;
  code: string;
  title: string;
  blockIds: string[];
  createdAt: string;
  updatedAt: string;
};

type SquareBook = {
  id: string;
  code: string;
  title: string;
  pageIds: string[];
  counters: {
    nextPageNumber: number;
    nextBlockNumber: number;
  };
  createdAt: string;
  updatedAt: string;
};

type SquarePage = {
  id: string;
  code: string;
  bookId: string;
  parentPageId?: string;
  title: string;
  blockIds: string[];
  backgroundColor: string;
  gridEnabled: boolean;
  gridSize: number;
  createdAt: string;
  updatedAt: string;
};

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
    textColor: string;
    fontSize: number;
    borderRadius: number;
    shadow: boolean;
  };
  visible: boolean;
  locked: boolean;
  createdAt: string;
  updatedAt: string;
};

type SquareState = {
  app: "Square";
  version: "0.1";
  bookcase?: SquareBookcase;
  book: SquareBook;
  pages: Record<string, SquarePage>;
  blocks: Record<string, SquareBlock>;
  currentPageId: string;
  selectedBlockId?: string;
};
```

---

## 20. Development Style Preference

The user prefers complete file replacement over small patch instructions.

When modifying code:

- Provide full file contents.
- Avoid unnecessary refactoring.
- Do not change UI direction without explicit request.
- Keep scope narrow.
- Implement one feature group at a time.
- Do not add many libraries early.
- Prefer simple, understandable code.

---

## 21. Recommended Tech Stack

Initial:

```text
React
TypeScript
Vite
CSS
localStorage
JSON export/import
```

Later:

```text
IndexedDB
Google Drive
Google Sheets
Google Calendar
Python/FastAPI helper engine for document processing
Tauri or Electron for desktop packaging
```

---

## 22. Current Build Priority

The first coding task should be:

```text
Create Square v0.1 as a simple React + TypeScript + Vite app centered on src/App.tsx.
```

Do not start with:

- Calendar
- Document handling
- Google integrations
- HTML module execution
- Graph View
- Formula engine

The first goal is:

```text
A working block canvas with Book/Page/Block structure.
```

---

## 23. Codex Working Rule

When using Codex, always start by telling it:

```text
Implement only Square v0.1.
Do not implement future roadmap features.
Keep the code simple and provide full file contents.
```
