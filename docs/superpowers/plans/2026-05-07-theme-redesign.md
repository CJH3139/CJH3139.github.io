# Theme Redesign Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Restyle `index.html` from green + circles to electric blue + blocky/angular with no circular shapes.

**Architecture:** All changes are in a single file (`index.html`) — inline `<style>` block and the HTML body. No new files. Tasks group changes by logical section of the file to minimize jumping around.

**Tech Stack:** Plain HTML, CSS (inline `<style>` block), Font Awesome icons, Google Fonts (Inter + VT323)

---

## Files

- Modify: `index.html` — CSS variables, shape styles, card styles, button styles, hero HTML

---

### Task 1: Update CSS variables and ambient background colors

**Files:**
- Modify: `index.html` (`:root` block, `body::before`, `body::after`)

- [ ] **Step 1: Replace the `:root` block**

Find:
```css
    :root {
      --green: #4ade80;
      --green-dim: #16a34a;
      --green-glow: rgba(74, 222, 128, 0.25);
      --bg: #090c10;
      --bg-card: rgba(255,255,255,0.035);
      --border: rgba(255,255,255,0.07);
      --text: #e8edf3;
      --muted: #64748b;
    }
```

Replace with:
```css
    :root {
      --blue: #38bdf8;
      --blue-dim: #0284c7;
      --blue-glow: rgba(56,189,248,0.25);
      --bg: #080c14;
      --bg-card: rgba(56,189,248,0.04);
      --border: rgba(56,189,248,0.12);
      --text: #e8edf3;
      --muted: #64748b;
    }
```

- [ ] **Step 2: Replace ambient glow colors in `body::before`**

Find:
```css
      background:
        radial-gradient(ellipse 70% 55% at 15% -10%, rgba(74,222,128,0.07) 0%, transparent 60%),
        radial-gradient(ellipse 55% 45% at 85% 105%, rgba(34,197,94,0.05) 0%, transparent 55%);
```

Replace with:
```css
      background:
        radial-gradient(ellipse 70% 55% at 15% -10%, rgba(56,189,248,0.07) 0%, transparent 60%),
        radial-gradient(ellipse 55% 45% at 85% 105%, rgba(14,165,233,0.05) 0%, transparent 55%);
```

- [ ] **Step 3: Replace pixel grid colors in `body::after`**

Find:
```css
      background-image:
        linear-gradient(rgba(74,222,128,0.025) 1px, transparent 1px),
        linear-gradient(90deg, rgba(74,222,128,0.025) 1px, transparent 1px);
```

Replace with:
```css
      background-image:
        linear-gradient(rgba(56,189,248,0.025) 1px, transparent 1px),
        linear-gradient(90deg, rgba(56,189,248,0.025) 1px, transparent 1px);
```

- [ ] **Step 4: Commit**

```bash
git add index.html
git commit -m "style: switch CSS variables and background accents from green to electric blue"
```

---

### Task 2: Remove avatar CSS and delete spinning ring animation

**Files:**
- Modify: `index.html` (CSS block — remove `.avatar-wrap`, `.avatar`, `.avatar-ring`, `@keyframes spin`)

- [ ] **Step 1: Delete the avatar CSS block**

Find and delete this entire block (lines covering `.avatar-wrap` through `@keyframes spin`):
```css
    .avatar-wrap {
      position: relative;
      width: 110px;
      height: 110px;
    }

    .avatar {
      width: 110px;
      height: 110px;
      border-radius: 50%;
      background: linear-gradient(135deg, #052e16, #14532d);
      border: 2px solid var(--green);
      box-shadow: 0 0 28px var(--green-glow), 0 0 70px rgba(74,222,128,0.07);
      display: flex;
      align-items: center;
      justify-content: center;
      font-family: 'VT323', monospace;
      font-size: 2.4rem;
      color: var(--green);
      letter-spacing: 1px;
    }

    .avatar-ring {
      position: absolute;
      inset: -8px;
      border-radius: 50%;
      border: 1px solid rgba(74,222,128,0.15);
      animation: spin 12s linear infinite;
    }

    .avatar-ring::after {
      content: '';
      position: absolute;
      top: -3px;
      left: 50%;
      transform: translateX(-50%);
      width: 6px;
      height: 6px;
      background: var(--green);
      border-radius: 50%;
      box-shadow: 0 0 8px var(--green);
    }

    @keyframes spin {
      from { transform: rotate(0deg); }
      to   { transform: rotate(360deg); }
    }
```

- [ ] **Step 2: Remove the avatar HTML element**

Find:
```html
    <div class="avatar-wrap">
      <div class="avatar">CJH</div>
      <div class="avatar-ring"></div>
    </div>
```

Delete it entirely.

- [ ] **Step 3: Commit**

```bash
git add index.html
git commit -m "style: remove circular avatar and spinning ring from hero"
```

---

### Task 3: Update badge to green "available" with square dot

**Files:**
- Modify: `index.html` (`.badge` CSS, `.badge-dot` CSS, badge HTML)

- [ ] **Step 1: Update `.badge` CSS**

Find:
```css
    .badge {
      display: inline-flex;
      align-items: center;
      gap: 7px;
      background: rgba(74,222,128,0.08);
      border: 1px solid rgba(74,222,128,0.25);
      border-radius: 999px;
      padding: 5px 16px;
      font-size: 0.75rem;
      color: var(--green);
      font-weight: 500;
    }
```

Replace with:
```css
    .badge {
      display: inline-flex;
      align-items: center;
      gap: 7px;
      background: rgba(74,222,128,0.08);
      border: 1px solid rgba(74,222,128,0.25);
      border-radius: 0;
      padding: 5px 16px;
      font-size: 0.75rem;
      color: #4ade80;
      font-weight: 600;
      letter-spacing: 1px;
    }
```

- [ ] **Step 2: Update `.badge-dot` CSS — square, stays green**

Find:
```css
    .badge-dot {
      width: 6px;
      height: 6px;
      border-radius: 50%;
      background: var(--green);
      animation: blink 2s infinite;
    }
```

Replace with:
```css
    .badge-dot {
      width: 6px;
      height: 6px;
      border-radius: 0;
      background: #4ade80;
      animation: blink 2s infinite;
    }
```

- [ ] **Step 3: Update badge HTML text**

Find:
```html
    <div class="badge">
      <span class="badge-dot"></span>
      Available for hire
    </div>
```

Replace with:
```html
    <div class="badge">
      <span class="badge-dot"></span>
      available
    </div>
```

- [ ] **Step 4: Commit**

```bash
git add index.html
git commit -m "style: update badge to green 'available' with square dot"
```

---

### Task 4: Update hero text and quote colors

**Files:**
- Modify: `index.html` (`.hero h1`, `.hero-sub strong`, `.hero-quote`, hero HTML)

- [ ] **Step 1: Update hero h1 gradient**

Find:
```css
      background: linear-gradient(135deg, #ffffff 30%, var(--green) 100%);
```

Replace with:
```css
      background: linear-gradient(135deg, #ffffff 30%, var(--blue) 100%);
```

- [ ] **Step 2: Update hero-sub strong color**

Find:
```css
    .hero-sub strong { color: var(--green); font-weight: 600; }
```

Replace with:
```css
    .hero-sub strong { color: var(--blue); font-weight: 600; }
```

- [ ] **Step 3: Update hero-quote color**

Find:
```css
      color: rgba(74,222,128,0.65);
```

Replace with:
```css
      color: rgba(56,189,248,0.65);
```

- [ ] **Step 4: Remove subtitle line from hero HTML**

Find:
```html
    <p class="hero-sub">
      <strong>Minecraft Java &amp; Skript Developer</strong> · Server Owner<br>
      Building scripts and systems to power Minecraft communities.
    </p>
```

Replace with:
```html
    <p class="hero-sub">
      <strong>Minecraft Java &amp; Skript Developer</strong> · Server Owner
    </p>
```

- [ ] **Step 5: Commit**

```bash
git add index.html
git commit -m "style: update hero text colors to blue, remove subtitle line"
```

---

### Task 5: Make buttons sharp and blue

**Files:**
- Modify: `index.html` (`.btn`, `.btn-green`, `.btn-green:hover`, `.btn-ghost`, `.btn-ghost:hover`, all HTML `btn-green` references)

- [ ] **Step 1: Update `.btn` — remove border-radius**

Find:
```css
    .btn {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      padding: 11px 22px;
      border-radius: 8px;
      font-size: 0.875rem;
      font-weight: 600;
      text-decoration: none;
      border: none;
      cursor: pointer;
      transition: all 0.2s ease;
    }
```

Replace with:
```css
    .btn {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      padding: 11px 22px;
      border-radius: 0;
      font-size: 0.875rem;
      font-weight: 600;
      text-decoration: none;
      border: none;
      cursor: pointer;
      transition: all 0.2s ease;
    }
```

- [ ] **Step 2: Replace `.btn-green` and `.btn-green:hover` with blue equivalents**

Find:
```css
    .btn-green {
      background: var(--green);
      color: #000;
    }

    .btn-green:hover {
      background: #86efac;
      transform: translateY(-2px);
      box-shadow: 0 8px 28px var(--green-glow);
    }
```

Replace with:
```css
    .btn-blue {
      background: var(--blue);
      color: #000;
      border-bottom: 3px solid var(--blue-dim);
    }

    .btn-blue:hover {
      background: #7dd3fc;
      transform: translateY(-2px);
      box-shadow: 0 8px 28px var(--blue-glow);
    }
```

- [ ] **Step 3: Update `.btn-ghost` and `.btn-ghost:hover`**

Find:
```css
    .btn-ghost {
      background: var(--bg-card);
      color: var(--text);
      border: 1px solid var(--border);
    }

    .btn-ghost:hover {
      border-color: rgba(74,222,128,0.35);
      background: rgba(74,222,128,0.05);
      transform: translateY(-2px);
    }
```

Replace with:
```css
    .btn-ghost {
      background: var(--bg-card);
      color: var(--text);
      border: 1px solid var(--border);
    }

    .btn-ghost:hover {
      border-color: rgba(56,189,248,0.35);
      background: rgba(56,189,248,0.05);
      transform: translateY(-2px);
    }
```

- [ ] **Step 4: Update all `btn-green` class references in HTML to `btn-blue`**

There are two occurrences. Find and replace both:

First occurrence (hero CTA):
```html
      <a href="#work" class="btn btn-green">
```
→
```html
      <a href="#work" class="btn btn-blue">
```

Second occurrence (contact section):
```html
      <a href="https://discord.gg/m4H55rQJzC" target="_blank" class="btn btn-green">
```
→
```html
      <a href="https://discord.gg/m4H55rQJzC" target="_blank" class="btn btn-blue">
```

- [ ] **Step 5: Commit**

```bash
git add index.html
git commit -m "style: replace green rounded buttons with sharp blue blocky buttons"
```

---

### Task 6: Make skill cards sharp with left blue border

**Files:**
- Modify: `index.html` (`.skill-card`, `.skill-card::after`, `.skill-card:hover`, `.skill-card:hover::after`, `.skill-icon`)

- [ ] **Step 1: Update `.skill-card`**

Find:
```css
    .skill-card {
      background: var(--bg-card);
      border: 1px solid var(--border);
      border-radius: 12px;
      padding: 22px;
      transition: all 0.22s ease;
      position: relative;
      overflow: hidden;
    }
```

Replace with:
```css
    .skill-card {
      background: var(--bg-card);
      border: 1px solid var(--border);
      border-left: 2px solid var(--blue);
      border-radius: 0;
      padding: 22px;
      transition: all 0.22s ease;
      position: relative;
      overflow: hidden;
    }
```

- [ ] **Step 2: Update `.skill-card::after` gradient color**

Find:
```css
    .skill-card::after {
      content: '';
      position: absolute;
      inset: 0;
      background: linear-gradient(135deg, rgba(74,222,128,0.06), transparent);
      opacity: 0;
      transition: opacity 0.22s;
    }
```

Replace with:
```css
    .skill-card::after {
      content: '';
      position: absolute;
      inset: 0;
      background: linear-gradient(135deg, rgba(56,189,248,0.06), transparent);
      opacity: 0;
      transition: opacity 0.22s;
    }
```

- [ ] **Step 3: Update `.skill-card:hover`**

Find:
```css
    .skill-card:hover {
      border-color: rgba(74,222,128,0.28);
      transform: translateY(-4px);
      box-shadow: 0 14px 40px rgba(0,0,0,0.35);
    }
```

Replace with:
```css
    .skill-card:hover {
      border-color: rgba(56,189,248,0.35);
      border-left-color: var(--blue);
      transform: translateY(-4px);
      box-shadow: 4px 4px 0 rgba(56,189,248,0.08), 0 14px 40px rgba(0,0,0,0.35);
    }
```

- [ ] **Step 4: Update `.skill-icon`**

Find:
```css
    .skill-icon {
      width: 42px;
      height: 42px;
      background: rgba(74,222,128,0.1);
      border-radius: 9px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.1rem;
      color: var(--green);
      margin-bottom: 13px;
      position: relative;
      z-index: 1;
    }
```

Replace with:
```css
    .skill-icon {
      width: 42px;
      height: 42px;
      background: rgba(56,189,248,0.1);
      border-radius: 0;
      border-left: 2px solid var(--blue);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.1rem;
      color: var(--blue);
      margin-bottom: 13px;
      position: relative;
      z-index: 1;
    }
```

- [ ] **Step 5: Commit**

```bash
git add index.html
git commit -m "style: make skill cards sharp with left blue border accent"
```

---

### Task 7: Make link cards sharp with left blue border

**Files:**
- Modify: `index.html` (`.link-card`, `.link-card:hover`, `.link-icon`, `.li-docs`, `.link-card:hover .link-arrow`)

- [ ] **Step 1: Update `.link-card`**

Find:
```css
    .link-card {
      background: var(--bg-card);
      border: 1px solid var(--border);
      border-radius: 12px;
      padding: 18px 22px;
      display: flex;
      align-items: center;
      gap: 16px;
      text-decoration: none;
      color: var(--text);
      transition: all 0.2s ease;
    }
```

Replace with:
```css
    .link-card {
      background: var(--bg-card);
      border: 1px solid var(--border);
      border-left: 2px solid var(--blue);
      border-radius: 0;
      padding: 18px 22px;
      display: flex;
      align-items: center;
      gap: 16px;
      text-decoration: none;
      color: var(--text);
      transition: all 0.2s ease;
    }
```

- [ ] **Step 2: Update `.link-card:hover`**

Find:
```css
    .link-card:hover {
      border-color: rgba(74,222,128,0.3);
      background: rgba(74,222,128,0.035);
      transform: translateX(5px);
    }
```

Replace with:
```css
    .link-card:hover {
      border-color: rgba(56,189,248,0.35);
      border-left-color: var(--blue);
      background: rgba(56,189,248,0.04);
      transform: translateX(5px);
      box-shadow: 4px 0 0 var(--blue);
    }
```

- [ ] **Step 3: Update `.link-icon` — remove border-radius**

Find:
```css
    .link-icon {
      width: 46px;
      height: 46px;
      border-radius: 10px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.2rem;
      flex-shrink: 0;
    }
```

Replace with:
```css
    .link-icon {
      width: 46px;
      height: 46px;
      border-radius: 0;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.2rem;
      flex-shrink: 0;
    }
```

- [ ] **Step 4: Update `.li-docs` to use blue**

Find:
```css
    .li-docs     { background: rgba(74,222,128,0.1); color: var(--green); }
```

Replace with:
```css
    .li-docs     { background: rgba(56,189,248,0.1); color: var(--blue); }
```

- [ ] **Step 5: Update link arrow hover color**

Find:
```css
    .link-card:hover .link-arrow {
      transform: translateX(4px);
      color: var(--green);
    }
```

Replace with:
```css
    .link-card:hover .link-arrow {
      transform: translateX(4px);
      color: var(--blue);
    }
```

- [ ] **Step 6: Commit**

```bash
git add index.html
git commit -m "style: make link cards sharp with left blue border accent"
```

---

### Task 8: Make contact box sharp, update footer and section eyebrows

**Files:**
- Modify: `index.html` (`.contact-box`, `.contact-box::before`, `.discord-pill`, `footer span`, `.sec-eyebrow`, `.nav-logo`)

- [ ] **Step 1: Update `.contact-box`**

Find:
```css
    .contact-box {
      background: var(--bg-card);
      border: 1px solid var(--border);
      border-radius: 16px;
      padding: 52px 40px;
      text-align: center;
      position: relative;
      overflow: hidden;
    }
```

Replace with:
```css
    .contact-box {
      background: var(--bg-card);
      border: 1px solid var(--border);
      border-left: 3px solid var(--blue);
      border-radius: 0;
      padding: 52px 40px;
      text-align: center;
      position: relative;
      overflow: hidden;
    }
```

- [ ] **Step 2: Update `.contact-box::before` glow**

Find:
```css
      background: radial-gradient(circle, rgba(74,222,128,0.07), transparent 65%);
```

Replace with:
```css
      background: radial-gradient(circle, rgba(56,189,248,0.07), transparent 65%);
```

- [ ] **Step 3: Update `.discord-pill` — remove border-radius**

Find:
```css
    .discord-pill {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      background: rgba(88,101,242,0.12);
      border: 1px solid rgba(88,101,242,0.3);
      color: #a5b4fc;
      padding: 9px 20px;
      border-radius: 8px;
      font-weight: 600;
      font-size: 0.9rem;
      margin-bottom: 24px;
      cursor: pointer;
      user-select: all;
      transition: background 0.2s;
      position: relative;
    }
```

Replace with:
```css
    .discord-pill {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      background: rgba(88,101,242,0.12);
      border: 1px solid rgba(88,101,242,0.3);
      color: #a5b4fc;
      padding: 9px 20px;
      border-radius: 0;
      font-weight: 600;
      font-size: 0.9rem;
      margin-bottom: 24px;
      cursor: pointer;
      user-select: all;
      transition: background 0.2s;
      position: relative;
    }
```

- [ ] **Step 4: Update `footer span` and `.sec-eyebrow` to use `--blue`**

Find:
```css
    footer span { color: var(--green); }
```

Replace with:
```css
    footer span { color: var(--blue); }
```

Find:
```css
      color: var(--green);
```
in the `.sec-eyebrow` rule:
```css
    .sec-eyebrow {
      font-family: 'VT323', monospace;
      font-size: 0.85rem;
      color: var(--green);
      letter-spacing: 3px;
      text-transform: uppercase;
      margin-bottom: 6px;
    }
```

Replace `color: var(--green);` with `color: var(--blue);` in that rule.

- [ ] **Step 5: Update `.nav-logo` color**

Find:
```css
      color: var(--green);
```
in the `.nav-logo` rule:
```css
    .nav-logo {
      font-family: 'VT323', monospace;
      font-size: 1.5rem;
      color: var(--green);
      letter-spacing: 2px;
      text-decoration: none;
    }
```

Replace `color: var(--green);` with `color: var(--blue);` in that rule.

- [ ] **Step 6: Commit**

```bash
git add index.html
git commit -m "style: make contact box sharp, update footer/eyebrow/nav to blue"
```

---

### Task 9: Verify in browser

**Files:** none — visual check only

- [ ] **Step 1: Open `index.html` in a browser**

Open the file directly: `file:///c:/Users/roych/OneDrive/Documents/GitHub/CJH3139.github.io/index.html`

- [ ] **Step 2: Check each section visually**

Verify:
- Hero: green "available" badge with square dot, no avatar, no subtitle line, blue heading gradient
- Skills section: blue eyebrow, sharp cards with left blue border
- Work section: sharp link cards with left blue border, arrow turns blue on hover
- Contact: sharp contact box, sharp discord pill, sharp blue button
- Footer: "CJH" in blue
- Background: subtle blue pixel grid visible
- Zero circles anywhere on the page

- [ ] **Step 3: Check page title still reads correctly**

Page `<title>` should still be `CJH — Minecraft Developer` — no change needed.

- [ ] **Step 4: Final commit**

```bash
git add index.html
git commit -m "style: complete electric blue blocky theme — replace green/circles with blue/angular"
```
