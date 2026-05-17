# Future Ideas Start Prompt for Codex

Use this only after Square v0.2 is stable.

---

Read these future idea documents:

- `SQUARE_NAMING_AND_TYPES.md`
- `SMART_SQUARES_AND_TEMPLATES.md`

Important:

These documents are **not immediate implementation tasks**.

They are design references.

Do not rewrite the app.  
Do not rename all internal code immediately.  
Do not implement all Square categories.  
Do not build Smart Square framework yet.

Your task is only to understand and preserve the direction.

If asked to implement something from these documents, implement one small feature at a time while preserving existing UI and behavior.

Key ideas to remember:

1. User-facing term may become "Square" instead of "Block".
2. Internal code may still use `Block` or `SquareBlock`.
3. Long-term code may use S001 instead of B001, but migration must be backward-compatible.
4. Square types should eventually be categorized:
   - Design
   - Content
   - Control
   - Navigation
   - Collection
   - Time
   - Tool
   - Value
5. Users should not have to build every feature from primitive parts.
6. Square needs Smart Squares, Templates, Wizards, and Presets later.
7. First Smart Square candidate may be Duty Progress Square.
8. Do not use these ideas to delete or downgrade current features.
