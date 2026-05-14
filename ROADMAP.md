# Square Roadmap

## Current Priority

The current priority is:

```text
Square v0.1
```

Focus only on the basic block canvas engine.

---

## v0.1: Core Block Canvas

Goal:

```text
Book/Page/SubPage/Block structure with editable free-position blocks.
```

Features:

- One default Book
- Multiple Pages
- SubPages
- Page tree
- Page switching
- Block creation
- Block drag movement
- Block resizing
- Block text editing
- Block selection
- Block deletion
- Basic Block style editing
- localStorage save/load
- JSON export/import

Do not include Formula, Graph, Calendar, Document, Google integration, or HTML Module.

---

## v0.2: Basic Bookcase and Navigation

Goal:

```text
Add a simple home dashboard concept.
```

Features:

- Basic Bookcase screen
- Book preview card
- Open Book button
- Recent Page list
- Favorite Page button
- App starts on Bookcase

---

## v0.3: Block Actions

Goal:

```text
Blocks can perform simple actions.
```

Features:

- Click actions
- Go to Page
- Show Block
- Hide Block
- Toggle Block
- Open URL
- Preview Page / Block

Initial formulas:

```text
=GO(@P002)
=SHOW(@B003)
=HIDE(@B003)
=TOGGLE(@B004)
=OPEN_URL("https://example.com")
```

---

## v0.4: Value Blocks

Goal:

```text
Blocks can hold values and other blocks can read them.
```

Features:

- Text input block
- Number input block
- Date picker block
- Time picker block
- Checkbox block
- Selector block
- Scroll selector block
- VALUE reference

Example:

```text
=VALUE(@B010)
```

---

## v0.5: Relation and Formula View

Goal:

```text
User can inspect object relationships as formula/action lists.
```

Features:

- Relation table
- Formula list
- Broken reference detection
- Source/target list
- Selected Block dependency view

---

## v0.6: Graph View

Goal:

```text
Visualize relationships between Book/Page/Block objects.
```

Features:

- Simple node-edge graph
- Structure edges
- Action edges
- Value reference edges
- Selected Block focus view
- Broken reference indicator

No heavy animation required.

---

## v0.7: HTML Module / Web Tool Block

Goal:

```text
Allow small tools to run inside Square.
```

Features:

- Web Tool Block
- HTML Module Block
- iframe sandbox
- External tool launcher
- Firemap shortcut/webview candidate

---

## v0.8: Calendar Block

Goal:

```text
Build a Square-native calendar UI.
```

Features:

- Month view
- Week view
- Day cells as special mini-block-like objects
- Duty status display
- Schedule display
- Linked Page/Block from day cell
- Optional Google Calendar sync later

Recommended principle:

```text
Square Calendar Block = main UI
Google Calendar = sync and notification backend
```

---

## v0.9: Document Block

Goal:

```text
Support document-based work automation.
```

Features:

- Attach document
- Preview document
- Extract text
- Extract tables
- Fill templates
- Generate document

Important formats:

```text
DOCX
XLSX
PPTX
PDF
HWPX
```

Goal is document automation, not full document editing.

---

## v1.0: Personal Work Automation Sandbox

Goal:

```text
Square becomes usable as a personal work automation dashboard.
```

Potential features:

- Bookcase dashboard
- Book/Page/Block structure
- Block actions
- Value blocks
- Formula
- Relation/Graph view
- Calendar
- Document blocks
- HTML modules
- JSON/Drive storage
