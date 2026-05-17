# Smart Squares and Templates

## 0. Purpose

This document preserves an important product direction:

Square must not force the user to build every useful feature from primitive parts.

The user should be able to start from complete Smart Squares and templates.

---

## 1. The Problem

A fully flexible block system can become overwhelming.

Example:

To create a "duty shift progress bar" manually, the user might need:

- Date Square
- Time Square
- Shift start time
- Shift end time
- Current time calculation
- Percentage calculation
- Progress bar
- Remaining time text
- Exception handling
- Color conditions
- Alerts

This becomes visual programming labor.

The user described this as:

```text
Like opening a Lego box and seeing too many parts and a huge manual.
```

This is an important warning.

---

## 2. Core Solution

Square needs two levels of building blocks:

```text
Primitive Square = basic Lego brick
Smart Square     = pre-assembled useful component
```

Also:

```text
Page Template = complete kit
Wizard        = guided setup
Preset        = saved setting/design bundle
```

---

## 3. Primitive Square

Primitive Squares are low-level parts.

Examples:

- Text Square
- Button Square
- Date Square
- Time Square
- Input Square
- Progress Bar Square
- Container Square
- Design Square

These provide maximum flexibility but can be tiring to assemble manually.

---

## 4. Smart Square

Smart Squares are pre-built functional components.

Examples:

- Duty Progress Square
- Today Duty Status Square
- Next Duty Day Square
- Today Schedule Summary Square
- Checklist Square
- Timer Square
- Countdown Square
- Work Routine Square
- Document Template Fill Square
- Firemap Launch Square
- Recent Pages Square
- Favorites Square

The user configures options instead of building all inner logic.

---

## 5. Example: Duty Progress Square

A Smart Square for duty shift progress.

### User Settings

```text
Shift pattern: 당비비
Reference duty date: 2026-05-13
Start time: 09:00
End time: next day 09:00
Show progress percent: yes
Show remaining time: yes
Show current status: yes
Show next duty day: optional
Display style: bar / circle / text
```

### Output Display

```text
당번 근무 중
████████░░ 72%
남은 시간 6시간 43분
퇴근 예정: 내일 09:00
```

The user should not have to manually connect all calculations.

---

## 6. Page Template

A Page Template is a group of preconfigured Squares.

Examples:

- Duty Dashboard Page
- Fire Water Facility Check Page
- Regular Task Checklist Page
- Irregular Task Record Page
- Document Generation Page
- Today Work Summary Page
- Novel Writing Dashboard Page

A template should be usable immediately, then customizable.

---

## 7. Wizard

A Wizard asks the user for required settings and creates the Smart Square or Page Template automatically.

Example:

```text
Create Duty Dashboard

1. What is your team?
2. What is the reference duty date?
3. What is the shift pattern?
4. What time does duty start?
5. What should be displayed?
6. Create page
```

The result is a ready-to-use dashboard.

---

## 8. Preset

A Preset is a saved bundle of settings.

Examples:

- Minimal black-and-white style
- Fire station work dashboard style
- Mobile compact layout
- Large touch button style
- Night mode style
- Duty progress bar style

Presets reduce repetitive configuration.

---

## 9. Editable Internals

Smart Squares should be easy to use, but advanced users may want to inspect or customize them.

Long-term idea:

```text
Smart Square
→ Advanced settings
→ View internal configuration
→ Duplicate as custom version
```

Do not expose this complexity too early.

---

## 10. Product Direction

Old direction:

```text
User builds everything from blocks.
```

Improved direction:

```text
User starts from Smart Squares and templates,
then customizes only when needed.
```

This makes Square less intimidating.

---

## 11. Recommended User Levels

Square should support three user levels.

### Level 1: Use

```text
Choose template
Enter a few settings
Use immediately
```

### Level 2: Customize

```text
Move Squares
Change style
Change visible fields
Connect simple actions
```

### Level 3: Build

```text
Use formulas
Create relations
Build custom automation
Use modules
```

---

## 12. Near-Term Policy

Do not implement Smart Squares immediately if v0.2 is still unstable.

Recommended order:

```text
v0.2: Basic block actions
v0.3: Basic Value Squares
v0.4: Simple Smart Square prototype
v0.5: Page Template prototype
```

First Smart Square candidate:

```text
Duty Progress Square
```

because it directly matches the user's work needs.

---

## 13. Implementation Warning

Do not turn Smart Squares into a huge framework too early.

Start with one hardcoded Smart Square prototype later.

Good first target:

```text
Duty Progress Square
```

Avoid implementing:

- Full plugin marketplace
- Complex template engine
- Nested visual programming editor
- Advanced formula system

until the core app is stable.
