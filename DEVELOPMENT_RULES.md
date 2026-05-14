# Square Development Rules

## 1. Scope Discipline

Square must be developed step by step.

Do not implement future roadmap features during v0.1.

The current build target is:

```text
Square v0.1 = basic Book/Page/Block canvas engine
```

---

## 2. User Preference

The user prefers **complete file replacement** over line-by-line patch instructions.

When providing code:

- Give the full file contents.
- Avoid “change this line” style instructions.
- Keep changes easy to copy and replace.

---

## 3. Early Architecture Rule

At the beginning, keep implementation simple.

Recommended initial style:

```text
src/App.tsx 중심 구현
필요 시 App.css
불필요한 파일 분리 금지
```

Later, after the prototype works, split into:

```text
src/types/
src/components/
src/store/
src/utils/
```

---

## 4. No Unrequested Refactoring

Do not perform major refactoring unless explicitly requested.

When fixing bugs:

- Fix only the bug.
- Preserve UI direction.
- Preserve data model unless necessary.
- Do not add new features.

---

## 5. No Scope Creep

Do not add these until requested:

- Formula
- Relation
- Graph View
- Calendar
- Document processing
- Google integration
- HTML module
- Backend
- Login

---

## 6. Code Style

Prefer:

- Clear TypeScript types
- Simple React state
- Understandable functions
- Minimal dependencies
- Readable CSS
- Stable localStorage format

Avoid:

- Premature abstraction
- Heavy external libraries
- Clever but unreadable code
- Large unrequested framework changes

---

## 7. Data Integrity

Important rules:

- Internal `id` and user-facing `code` must be separate.
- Codes should remain stable.
- Deleted codes should not be reused.
- Moving a Block should not change its code.
- Page/SubPage hierarchy should use `parentPageId`.

---

## 8. v0.1 Storage

Use:

```ts
localStorage key = "square:v0.1:state"
```

Also support JSON export/import.

---

## 9. Testing Checklist

Before saying the task is done, verify:

- App runs without TypeScript errors.
- A Page can be created.
- A SubPage can be created.
- A Page can be selected.
- A Block can be created.
- A Block can be dragged.
- A Block can be resized.
- A Block text can be edited.
- A Block can be selected and deleted.
- Style panel changes apply.
- Save/load works.
- JSON export/import works.

---

## 10. Answer Format for Codex

When completing a task, respond with:

```text
Changed files
Implementation summary
How to run
Manual test checklist
Known limitations
Next step
```
