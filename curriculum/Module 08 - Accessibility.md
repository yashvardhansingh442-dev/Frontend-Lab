# Module 08: Accessibility (a11y)

**Folder:** `08-accessibility/`
**Level:** Beginner (with Advanced notes)
**Time:** 8 to 10 hours
**Writing style:** ASD-STE100 (Simplified Technical English)
**Prerequisites:** Modules 01 to 07

---

## Module Overview

### Goal
Learn to build web pages that **all people** can use. This includes people who are blind, have low vision, are deaf, have motor limits, or have cognitive differences.

### What you learn
After this module, you can:
1. Explain the principles of accessibility and the WCAG levels.
2. Write good alternative text for images.
3. Use ARIA correctly, and know when **not** to use it.
4. Make a page work with a keyboard only.
5. Add skip links and control focus order.
6. Test a page with Lighthouse, axe, and a screen reader.
7. Audit a broken page and fix it.

### The main idea of this module
Accessibility is **not** an extra feature. It is part of correct HTML. Most of the work is done by the things you learned in Modules 01 to 07: semantic elements, labels, alt text, headings, and tables.

The word **a11y** is a short form of "accessibility": the letter **a**, then **11** letters, then the letter **y**.

### Who needs accessibility?

| Group | Example | What helps |
|-------|---------|------------|
| Blind users | Use a screen reader | Alt text, headings, labels, landmarks |
| Low vision users | Zoom, high contrast | Good contrast, text that resizes, reflow |
| Deaf and hard of hearing users | Cannot hear audio | Captions, transcripts |
| Motor impairment | Cannot use a mouse; use a keyboard, switch, or voice | Keyboard access, large targets |
| Cognitive differences | Dyslexia, ADHD, memory limits | Simple language, clear layout, no time limits |
| Temporary limits | A broken arm, bright sun, a noisy room | All of the above |
| Everyone | Older users, slow connections, small screens | All of the above |

About 1 in 6 people in the world has a significant disability. Accessible design also helps all users.

### Folder structure for this module
```
08-accessibility/
├── lesson-01-principles-wcag.md
├── lesson-02-alt-text.md
├── lesson-03-aria.md
├── lesson-04-keyboard-tabindex.md
├── lesson-05-skip-links-focus-order.md
├── lesson-06-testing.md
├── lesson-07-project-audit-and-fix.md
├── examples/
├── exercises/
└── project/
```

---

# Lesson 1: Accessibility Principles (WCAG Basics)

## 1.1 Learning objectives
After this lesson, you can:
- Name the four principles of WCAG (POUR).
- Explain the levels A, AA, and AAA.
- Name the key success criteria for HTML developers.
- Explain how people use assistive technology.

## 1.2 What is WCAG?

**WCAG** = Web Content Accessibility Guidelines. It is an international standard from the W3C. The current version is **WCAG 2.2**.

- WCAG has **guidelines** and **success criteria** (numbered rules, for example 1.1.1).
- Many laws refer to WCAG (for example the European Accessibility Act, Section 508 in the USA, and others). The usual target is **Level AA**.

## 1.3 The four principles: POUR

| Letter | Principle | Meaning | Example |
|--------|-----------|---------|---------|
| **P** | **Perceivable** | Users must be able to **sense** the content. | Alt text, captions, contrast |
| **O** | **Operable** | Users must be able to **use** the controls. | Keyboard access, enough time, no flashing |
| **U** | **Understandable** | Users must be able to **understand** the content and the interface. | Clear labels, error help, page language |
| **R** | **Robust** | Content must work with many browsers and **assistive technology**. | Valid HTML, correct names and roles |

## 1.4 Conformance levels

| Level | Meaning | Use |
|-------|---------|-----|
| **A** | The minimum. | Basic barriers removed. |
| **AA** | The normal target. | Most laws need this. |
| **AAA** | The highest. | Not possible for all content. Use where you can. |

## 1.5 Key success criteria for developers

| SC | Level | Rule | Module link |
|----|-------|------|-------------|
| **1.1.1** Non-text Content | A | Give a text alternative for images. | Module 04 |
| **1.2.2** Captions (Prerecorded) | A | Give captions for video with speech. | Module 04 |
| **1.3.1** Info and Relationships | A | Structure (headings, lists, tables, labels) is in the code. | Modules 02, 05, 06, 07 |
| **1.3.5** Identify Input Purpose | AA | Use `autocomplete` on personal data fields. | Module 06 |
| **1.4.1** Use of Color | A | Do not use color as the only way to show meaning. | This module |
| **1.4.3** Contrast (Minimum) | AA | Text contrast at least **4.5:1** (large text **3:1**). | This module |
| **1.4.4** Resize Text | AA | Text can zoom to **200%** with no loss. | This module |
| **1.4.10** Reflow | AA | No two-way scroll at **320 CSS px** width (400% zoom). | This module |
| **1.4.11** Non-text Contrast | AA | UI parts and graphics at least **3:1**. | This module |
| **1.4.12** Text Spacing | AA | Content works when the user changes text spacing. | This module |
| **2.1.1** Keyboard | A | All functions work with a keyboard. | Lesson 4 |
| **2.1.2** No Keyboard Trap | A | Focus can always leave a component. | Lesson 4 |
| **2.2.2** Pause, Stop, Hide | A | The user can stop moving content. | This module |
| **2.3.1** Three Flashes | A | Nothing flashes more than 3 times in 1 second. | Module 04 |
| **2.4.1** Bypass Blocks | A | Give a way to skip repeated blocks (skip link). | Lesson 5 |
| **2.4.2** Page Titled | A | Each page has a clear `<title>`. | Module 01 |
| **2.4.3** Focus Order | A | Focus order is logical. | Lesson 5 |
| **2.4.4** Link Purpose | A | Link text tells where it goes. | Module 03 |
| **2.4.6** Headings and Labels | AA | Headings and labels describe the topic. | Modules 02, 06 |
| **2.4.7** Focus Visible | AA | Keyboard focus is visible. | Lesson 4 |
| **2.4.11** Focus Not Obscured (Minimum) | AA | Focus is not fully hidden by other content (WCAG 2.2). | Lesson 5 |
| **2.5.8** Target Size (Minimum) | AA | Targets are at least **24 by 24 CSS px** (WCAG 2.2). | This module |
| **3.1.1** Language of Page | A | Set `lang` on `<html>`. | Module 01 |
| **3.2.3** Consistent Navigation | AA | Navigation is in the same place on each page. | Module 03 |
| **3.3.1** Error Identification | A | Describe errors in text. | Module 06 |
| **3.3.2** Labels or Instructions | A | Fields have labels. | Module 06 |
| **4.1.2** Name, Role, Value | A | Controls have a name, a role, and a state. | Lesson 3 |

## 1.6 Color contrast

Contrast is the difference in brightness between text and its background. It is a ratio from 1:1 (no contrast) to 21:1 (black on white).

| Content | Minimum ratio (AA) |
|---------|--------------------|
| Normal text (under 24 px, or under 18.66 px bold) | **4.5:1** |
| Large text (24 px or more, or 18.66 px bold or more) | **3:1** |
| UI components (borders of inputs, icons) and graphics | **3:1** |
| Logos and decorative text | No rule |

| Example | Ratio | Result |
|---------|-------|--------|
| `#000000` on `#ffffff` | 21:1 | Pass |
| `#595959` on `#ffffff` | 7:1 | Pass |
| `#767676` on `#ffffff` | 4.54:1 | Pass (the lightest grey for normal text on white) |
| `#999999` on `#ffffff` | 2.85:1 | **Fail** |
| `#ffffff` on `#3b82f6` | 3.68:1 | Pass for large text only |

Tools: Chrome DevTools (click a color in the Styles pane), WebAIM Contrast Checker, and the Colour Contrast Analyser app.

## 1.7 Do not use color alone

```html
<!-- Bad: only color shows the error -->
<input style="border-color: red" />

<!-- Good: color, icon, and text -->
<input aria-invalid="true" aria-describedby="e1" style="border-color: #b91c1c" />
<p id="e1"><span aria-hidden="true">⚠</span> Enter a valid email address.</p>
```

Also: do not write "Click the green button". Write "Click the **Save** button".

## 1.8 How people use the web

| Tool | Who uses it | How it works |
|------|-------------|--------------|
| **Screen reader** (NVDA, JAWS, VoiceOver, TalkBack, Narrator) | Blind and low vision users | Reads the page aloud (or to a braille display) from the accessibility tree |
| **Screen magnifier / browser zoom** | Low vision users | Makes the page bigger |
| **Keyboard only** | Motor impairment, blind users, power users | Uses `Tab`, arrows, `Enter`, `Space`, `Esc` |
| **Switch device** | Severe motor impairment | One or two buttons scan through the controls |
| **Voice control** (Dragon, Voice Control) | Motor impairment | User says the **visible name** of a control ("click Search") |
| **High contrast / forced colors mode** | Low vision, light sensitivity | The system replaces your colors |
| **Reduced motion setting** | Vestibular disorders | Asks sites to reduce animation |

**Important for voice control:** The **visible text** of a control must be part of its **accessible name**. If a button shows "Search" but has `aria-label="Find"`, a voice user who says "click Search" has a problem (WCAG 2.5.3 Label in Name).

## 1.9 Try It

1. Zoom your browser to 200% on three websites. Which ones still work? Which ones break?
2. Open the WebAIM Contrast Checker. Test `#999` on white. Then find the nearest color that passes.
3. Turn on **Forced Colors** (Windows: High Contrast) or Chrome DevTools > Rendering > Emulate `forced-colors`. Look at one of your pages.
4. Put your mouse away. Try to use one website with only the keyboard for 2 minutes. Write what you could not do.

## 1.10 Advanced Note

- **WCAG 2.2 new criteria:** 2.4.11 Focus Not Obscured (AA), 2.4.13 Focus Appearance (AAA), 2.5.7 Dragging Movements (AA), 2.5.8 Target Size Minimum (AA), 3.2.6 Consistent Help (A), 3.3.7 Redundant Entry (A), 3.3.8 Accessible Authentication Minimum (AA). 4.1.1 Parsing was removed.
- **WCAG 3.0** is a draft. Do not use it for compliance now.
- **APCA:** An alternative contrast method in WCAG 3 drafts. WCAG 2 ratio rules are still the legal test.
- **Legal:** In the EU, the European Accessibility Act applies to many products and services from June 2025. In the USA, courts use the ADA for websites, and Section 508 for government. In India, the RPwD Act and GIGW guidelines apply. Check the law of your country.
- **Accessibility statement:** Many sites publish a page that describes their level of conformance, known problems, and contact information.
- **VPAT / ACR:** A report that vendors give to customers to show conformance.
- **Media queries for user needs:**
  ```css
  @media (prefers-reduced-motion: reduce) { * { animation: none !important; transition: none !important; } }
  @media (prefers-color-scheme: dark) { :root { --bg: #111; --text: #eee; } }
  @media (prefers-contrast: more) { :root { --border: #000; } }
  @media (forced-colors: active) { .btn { border: 1px solid ButtonText; } }
  ```
- **Text spacing:** Users can set line height 1.5, paragraph spacing 2x, letter spacing 0.12em, and word spacing 0.16em. Your layout must not cut or overlap text. Do not use fixed heights on text boxes.
- **Use relative units:** Use `rem` and `em` for font sizes, not `px`, so that user font settings work.
- **Language of parts:** `<span lang="fr">bonjour</span>` makes a screen reader use French pronunciation (3.1.2, AA).
- **Reading level:** WCAG AAA 3.1.5 asks for lower secondary reading level. Use plain language where you can.
- **Cognitive accessibility:** Use clear headings, short sentences, consistent patterns, and avoid timeouts. Allow users to undo and review.
- **Automated tools find about 30 to 40 percent of issues.** Manual tests are required.

## 1.11 Exercises

1. Write the four WCAG principles and one example for each.
2. Check these color pairs with a contrast checker and write pass or fail for normal text: `#777 on #fff`, `#fff on #0066cc`, `#ccc on #fff`, `#222 on #ffeb3b`.
3. Rewrite the instruction "Click the red button to delete" so that it does not depend on color.
4. List 5 ways that a person can use a website with no mouse.
5. **Advanced:** Add `prefers-reduced-motion` and `forced-colors` rules to a page with an animation and a custom button.

## 1.12 Check your understanding
- What does POUR mean?
- Which WCAG level is the normal legal target?
- What is the minimum contrast ratio for normal text?
- Why must the visible label be in the accessible name?

---

# Lesson 2: Alt Text Best Practices

## 2.1 Learning objectives
After this lesson, you can:
- Decide what type of image you have.
- Write correct alt text for each type.
- Handle complex images, icons, and images of text.

## 2.2 A reminder

The `alt` attribute gives a **text alternative** for an image. Module 04 introduced it. This lesson gives the full decision process.

## 2.3 The decision tree

```
Does the image add information or function?
│
├── NO (decoration only)
│     └── alt=""   (empty)  or use a CSS background
│
└── YES
      │
      ├── Is it a link or a button?
      │     └── alt describes the DESTINATION or ACTION
      │
      ├── Does it contain text?
      │     └── alt = the same text (if the text is not already in the page)
      │
      ├── Is it a chart, diagram, or map (complex)?
      │     └── short alt + long description in the page text
      │
      └── Is it a photo or an illustration with meaning?
            └── alt describes what matters in THIS context
```

## 2.4 Types of images and the correct alt

| Type | Example | Correct `alt` |
|------|---------|---------------|
| **Informative** | A photo of a product | `alt="Blue running shoe with white sole, side view"` |
| **Decorative** | A line, a pattern, a stock photo that adds nothing | `alt=""` |
| **Functional** | A magnifier icon that is a search button | `alt="Search"` |
| **Image link** | A logo that links to the home page | `alt="Acme, home page"` |
| **Image of text** | A banner that says "Sale 50% off" | `alt="Sale: 50% off all shoes"` |
| **Complex** | A bar chart | Short `alt` + long description nearby |
| **Group** | 3 star images that mean "3 of 5 stars" | One `alt` on the group: `alt="Rating: 3 out of 5 stars"` |
| **Image with a caption that says the same** | Photo with a full caption | Short `alt`, or `alt=""` if the caption fully describes it |

## 2.5 Rules for good alt text

1. **Think about the context.** The same photo can need different alt text on different pages.
2. **Say what matters, not everything.** Short is best. Try to stay under about 125 characters.
3. **Do not start with** "image of", "picture of", or "photo of". The screen reader already says "image".
4. **Do not repeat** the text next to the image.
5. **Do not put the file name** in alt (`alt="IMG_3029.jpg"`).
6. **Include text that is in the image** if it is important.
7. **Use correct punctuation.** A period at the end gives a short pause. It is good for full sentences.
8. **Never leave out** the `alt` attribute. Use `alt=""` for decoration.
9. **Do not use `title`** instead of `alt`.

### Same image, different context

A photo of a person at a podium:
- On a news page about a speech: `alt="Maria Lopez speaks at the climate conference"`
- On a page that lists "Our team": `alt="Maria Lopez, Chief Executive"`
- On a page that is only decoration: `alt=""`

## 2.6 Good and bad examples

| Image | Bad | Good |
|-------|-----|------|
| Dog on a beach | `alt="dog"` | `alt="A brown dog runs through shallow waves on a beach"` |
| Logo with link | `alt="logo"` | `alt="Acme Shop, home page"` |
| Twitter icon link | `alt="icon"` | `alt="Acme on X (opens in a new tab)"` (or put the text in the link) |
| Chart | `alt="chart"` | `alt="Line chart: website visits grew from 1,000 in January to 5,000 in June."` |
| Spacer | `alt="blank"` | `alt=""` |
| Hero photo, decorative | `alt="Beautiful sunset over ocean"` | `alt=""` (if the page does not need it) |

## 2.7 Icons and icon fonts

```html
<!-- Icon with visible text: hide the icon -->
<button type="button">
  <svg aria-hidden="true" focusable="false" width="16" height="16">...</svg>
  Save
</button>

<!-- Icon only: name the button -->
<button type="button" aria-label="Close dialog">
  <svg aria-hidden="true" focusable="false" width="16" height="16">...</svg>
</button>

<!-- Icon font: hide the glyph, give text -->
<a href="/cart">
  <span class="icon-cart" aria-hidden="true"></span>
  <span class="visually-hidden">Shopping cart</span>
</a>
```

## 2.8 Complex images

For a chart or a diagram, give the data in text.

```html
<figure>
  <img src="sales.png"
       alt="Bar chart of sales by quarter. The full data is in the table below."
       width="600" height="400" />
  <figcaption>Figure 1: Sales by quarter, 2026.</figcaption>
</figure>

<table>
  <caption>Sales by quarter, 2026 (in thousands of USD)</caption>
  <thead><tr><th scope="col">Quarter</th><th scope="col">Sales</th></tr></thead>
  <tbody>
    <tr><th scope="row">Q1</th><td>120</td></tr>
    <tr><th scope="row">Q2</th><td>150</td></tr>
  </tbody>
</table>
```

Other options: a link to a long description page, or `aria-describedby` that points to a text block.

## 2.9 Images of text

Avoid images of text. Use real text and CSS. If you must use an image of text (a logo, for example), the `alt` must contain the same text.

## 2.10 Other media

| Media | Text alternative |
|-------|------------------|
| Video with speech | Captions + transcript |
| Video with important visuals | Audio description (or a text description) |
| Audio only | Transcript |
| `<canvas>` | Fallback content inside `<canvas>...</canvas>`, or `aria-label` + text |
| `<svg>` | `<title>` + `role="img"` or `aria-hidden="true"` |
| `<iframe>` | `title` attribute |

## 2.11 Try It

1. Find 5 images on a website. Write your own alt text for each. Classify each as informative, decorative, functional, or complex.
2. Open DevTools. Check the real `alt` of those images. Compare.
3. Write alt text for the same photo in 3 different contexts.
4. Turn off images in your browser (or block them). Read a page. Does it make sense?
5. Install a screen reader (NVDA is free). Listen to an image with `alt=""` and one with no `alt`.

## 2.12 Advanced Note

- **Missing `alt`:** Screen readers may read the file name or URL. This is worse than nothing.
- **`role="presentation"` / `role="none"` on `<img>`:** The same as `alt=""`. Use `alt=""`, which is simpler.
- **`aria-label` on `<img>`:** It works, but `alt` is the standard. Do not use both with different text.
- **`title` attribute:** It is not reliable. Touch and keyboard users cannot see it. Do not use it as the only name.
- **`longdesc`:** Obsolete.
- **`aria-describedby` for long descriptions:** Point to a visible text block. It adds the description after the alt text.
- **Alt text for AI-generated descriptions:** Automatic alt text can be wrong. Check it. It does not know your context.
- **Social images:** Add alt text when you post images on social media. Most platforms have a field for it.
- **Background images:** CSS background images have **no** alt text. Use them for decoration only. If the image has meaning, use `<img>`.
- **SVG:** Inline SVG needs `role="img"` and a `<title>`, or `aria-hidden="true"`. SVG in `<img>` uses `alt`.
- **Emoji:** Screen readers read the emoji name ("red heart"). Use emoji with care. Do not use many in a row.
- **Alt text length:** Some screen readers do not stop reading, so the user cannot skip. Keep it short, and use the long description in the page.
- **CAPTCHA images:** Give an alternative (for example an audio CAPTCHA or a different method). Better: use methods that do not need a CAPTCHA (WCAG 3.3.8).
- **Automated check:** Tools can find a **missing** alt. They cannot tell if the alt text is **good**.

## 2.13 Exercises

1. Write alt text for: (a) a photo of your school used in an "About us" page, (b) a "download PDF" icon that is a link, (c) a line that separates two sections.
2. Explain why `alt="image of a cat"` is not good.
3. Write the HTML for a pie chart of 3 values, with a short alt text and a data table.
4. Fix: `<a href="/home"><img src="logo.png" alt="logo"></a>` for a company named "Zen Tea".
5. **Advanced:** Write a script that finds all `<img>` without `alt` or with a file name as `alt` on a page. Log the list to the console.

## 2.14 Check your understanding
- When do you use `alt=""`?
- What must the alt text of an image link describe?
- How do you give a long description for a chart?
- Why is `title` not a good replacement for `alt`?

---

# Lesson 3: ARIA - Roles, Labels, and When Not to Use Them

## 3.1 Learning objectives
After this lesson, you can:
- Explain what ARIA is and what it does not do.
- Use the five rules of ARIA.
- Use the common `aria-*` attributes correctly.
- Know when **not** to use ARIA.

## 3.2 What is ARIA?

**ARIA** = Accessible Rich Internet Applications. It is a set of attributes that you add to HTML to give extra information to assistive technology.

ARIA changes **only** what assistive technology hears and sees in the accessibility tree. It does **not**:
- Change how the element looks.
- Add keyboard behavior.
- Add focus.
- Change what the browser does.

```html
<div role="button">Save</div>
```
This `<div>` is **announced** as a button. But it still cannot be focused with `Tab`, and `Enter` does nothing. You must add all of that yourself. A real `<button>` does all of it already.

## 3.3 The five rules of ARIA

1. **If you can use a native HTML element or attribute with the meaning and behavior that you need, use it.** Do not add ARIA.
2. **Do not change native semantics**, unless you really must. (`<h2 role="tab">` is bad.)
3. **All interactive ARIA controls must work with the keyboard.**
4. **Do not use `role="presentation"` or `aria-hidden="true"` on a focusable element.**
5. **All interactive elements must have an accessible name.**

**Short version:** *No ARIA is better than bad ARIA.* Pages with ARIA have, on average, more errors than pages with no ARIA.

## 3.4 The three parts of ARIA

| Part | Meaning | Example |
|------|---------|---------|
| **Roles** | **What** the element is | `role="dialog"`, `role="tablist"`, `role="alert"` |
| **Properties** | Features that rarely change | `aria-label`, `aria-labelledby`, `aria-describedby`, `aria-controls` |
| **States** | Conditions that **change** (usually with JavaScript) | `aria-expanded`, `aria-checked`, `aria-pressed`, `aria-invalid`, `aria-hidden` |

## 3.5 Roles

### Landmark roles (mostly given by HTML elements)

| Role | Native element |
|------|----------------|
| `banner` | `<header>` (page level) |
| `navigation` | `<nav>` |
| `main` | `<main>` |
| `complementary` | `<aside>` |
| `contentinfo` | `<footer>` (page level) |
| `region` | `<section>` with a name |
| `search` | `<search>` or `<form role="search">` |
| `form` | `<form>` with a name |

### Widget roles (use when no native element exists)

`tablist`, `tab`, `tabpanel`, `dialog`, `alertdialog`, `menu`, `menuitem`, `combobox`, `listbox`, `slider`, `switch`, `tree`, `grid`.

These roles need **a lot** of JavaScript (keyboard, state). Use the **ARIA Authoring Practices Guide (APG)** at `https://www.w3.org/WAI/ARIA/apg/` for the exact patterns, or use a tested library.

### Live region roles

| Role | Use |
|------|-----|
| `status` | A polite message ("3 results found") |
| `alert` | An important, urgent message ("Payment failed") |
| `log` | A list of messages that grows (chat) |
| `timer` | A timer |

### Roles that you do **not** need to write

Do not write `role="button"` on `<button>`, `role="navigation"` on `<nav>`, `role="list"` on `<ul>`, or `role="link"` on `<a href>`. They are redundant.

## 3.6 Naming: `aria-label`, `aria-labelledby`, `aria-describedby`

| Attribute | Job | Example |
|-----------|-----|---------|
| `aria-label` | A **name** as text (not visible). | `<button aria-label="Close">×</button>` |
| `aria-labelledby` | A **name** from **other element(s)** by `id`. | `<section aria-labelledby="h1">` |
| `aria-describedby` | A **description** (extra help) from other element(s). | `<input aria-describedby="hint">` |

**Order of name sources** (the browser uses the first that exists): `aria-labelledby` > `aria-label` > native label (`<label>`, `alt`, text content) > `title`.

```html
<!-- aria-label for an icon button -->
<button type="button" aria-label="Open menu">
  <svg aria-hidden="true" focusable="false">...</svg>
</button>

<!-- aria-labelledby: the heading names the region -->
<section aria-labelledby="news-title">
  <h2 id="news-title">Latest news</h2>
</section>

<!-- aria-describedby: help text -->
<label for="pw">Password</label>
<input type="password" id="pw" aria-describedby="pw-hint" />
<p id="pw-hint">At least 8 characters.</p>
```

**Warning:** `aria-label` does not work reliably on `<div>` and `<span>` that have no role. Use it on interactive elements and landmarks.

## 3.7 Common states and properties

| Attribute | Used on | Meaning |
|-----------|---------|---------|
| `aria-expanded="true|false"` | Buttons that open something | The controlled content is open or closed. |
| `aria-controls="id"` | Buttons, tabs | Points to the element that it controls. |
| `aria-pressed="true|false"` | Toggle buttons | The button is on or off. |
| `aria-selected="true|false"` | Tabs, options | The item is selected. |
| `aria-checked="true|false|mixed"` | Custom checkboxes | The checked state. |
| `aria-current="page|step|true"` | Links, steps | The current item in a set. |
| `aria-hidden="true"` | Any non-focusable element | Hides it from assistive technology only. |
| `aria-invalid="true"` | Form fields | The value is not valid. |
| `aria-required="true"` | Custom widgets | A value is required. (Use `required` on native fields.) |
| `aria-disabled="true"` | Custom widgets | The control is disabled. |
| `aria-live="polite|assertive|off"` | Containers | Announce changes in the content. |
| `aria-busy="true"` | Containers | The content is loading. |
| `aria-modal="true"` | `dialog` | The rest of the page is inert (native `<dialog>` with `showModal()` does this). |
| `aria-haspopup` | Buttons | The button opens a menu, listbox, dialog, etc. |

## 3.8 Example: A menu toggle button

```html
<button type="button" aria-expanded="false" aria-controls="site-menu" id="menu-btn">
  Menu
</button>
<nav id="site-menu" aria-label="Main" hidden>
  <ul>...</ul>
</nav>
```

```js
const btn = document.getElementById('menu-btn');
const menu = document.getElementById('site-menu');

btn.addEventListener('click', () => {
  const open = btn.getAttribute('aria-expanded') === 'true';
  btn.setAttribute('aria-expanded', String(!open));
  menu.hidden = open;
});
```

The **state** (`aria-expanded`) **must change** with JavaScript when the menu opens and closes. A wrong state is worse than no state.

## 3.9 Live regions

A live region tells a screen reader to announce a change **without moving focus**.

```html
<!-- The region must exist in the page BEFORE you change its text -->
<div id="status" role="status" aria-live="polite"></div>
```

```js
document.getElementById('status').textContent = '3 items added to your cart.';
```

| Value | Behavior |
|-------|----------|
| `polite` | Waits for the user to stop. Use for most messages. |
| `assertive` | Interrupts. Use only for urgent messages. |
| `role="alert"` | Same as `assertive` and `aria-atomic="true"`. |

**Tips:** Keep messages short. Do not announce each key press. Do not use too many live regions.

## 3.10 `aria-hidden` and hiding content

| Method | Hidden visually | Hidden from screen readers | Removed from tab order |
|--------|-----------------|----------------------------|------------------------|
| `display: none` or `hidden` | Yes | Yes | Yes |
| `visibility: hidden` | Yes | Yes | Yes |
| `aria-hidden="true"` | **No** | Yes | **No** |
| `.visually-hidden` class | Yes | **No** | No (stays focusable) |
| `inert` attribute | No (but not interactive) | Yes | Yes |

**Never** put `aria-hidden="true"` on a focusable element (a link, a button, an input). A keyboard user could focus an element that the screen reader cannot see.

## 3.11 When **not** to use ARIA

| Situation | Do this instead |
|-----------|-----------------|
| You want a button | Use `<button>`. |
| You want a link | Use `<a href>`. |
| You want a heading | Use `<h1>` to `<h6>`. |
| You want a list | Use `<ul>`, `<ol>`. |
| You want a checkbox | Use `<input type="checkbox">`. |
| You want a table | Use `<table>`. |
| You want an accordion | Use `<details>`. |
| You want a modal | Use `<dialog>`. |
| You want a form label | Use `<label>`. |
| You want to say "required" | Use `required`. |
| You want to hide something | Use `hidden` or CSS. |
| You are not sure | Do not add ARIA. Test first. |

## 3.12 Try It

1. Find 5 `role` attributes on a website. Is each one needed?
2. Make an icon-only button with `aria-label`. Check its name in DevTools > Accessibility.
3. Make a disclosure button with `aria-expanded` and `aria-controls`. Update the state with JavaScript.
4. Make a live region and update it. Use a screen reader to hear it.
5. Replace a `<div role="button" tabindex="0">` with a real `<button>`. Compare the code.

## 3.13 Advanced Note

- **Accessible name computation:** The W3C "Accname" specification describes the exact steps. DevTools shows the result in the Accessibility pane.
- **Name from content:** Some roles (button, link, heading, tab) take their name from their content. Others (textbox, region) need a label.
- **`aria-labelledby` can point to hidden elements.** This is a useful trick: a hidden `<span id="x">` can give a name.
- **`aria-owns`, `aria-activedescendant`:** For complex widgets (comboboxes, trees). Hard to get right. Use libraries.
- **`aria-roledescription`:** It changes the spoken role name. Use with extreme care. It can make a page worse.
- **`aria-atomic`, `aria-relevant`:** Control what a live region reads.
- **Live region timing:** Add the content **after** the region exists. Some screen readers do not announce a region that is created with its text already inside.
- **`aria-hidden` and focus bugs:** A hidden parent with a focusable child is a known bug type. Axe finds it.
- **Presentational roles:** `role="presentation"` / `role="none"` removes the semantics of an element, but not its children. Use with care. Example: `<table role="presentation">` for a layout table.
- **`role="img"` for groups:** `<div role="img" aria-label="Rating: 4 of 5">★★★★☆</div>` gives one name to a group of symbols.
- **ARIA in HTML:** The W3C spec "ARIA in HTML" lists which roles and attributes are allowed on each element. Validators check this.
- **ARIA 1.3 and new features:** `aria-description`, `aria-braillelabel`, and other new attributes have limited support. Test first.
- **Shadow DOM:** ID references (`aria-labelledby`, `for`) do not cross the shadow boundary. Newer APIs (`ariaLabelledByElements`) help.
- **Testing:** Use at least two screen reader and browser pairs (for example NVDA with Firefox, and VoiceOver with Safari).
- **Libraries:** Use well-tested components (for example Radix UI, React Aria, Reach UI, or native elements) for tabs, comboboxes, and menus.

## 3.14 Exercises

1. Write the five rules of ARIA in your own words.
2. Write the HTML for an icon-only "Search" button, with a correct accessible name.
3. Remove the ARIA that is not needed: `<nav role="navigation"><ul role="list"><li role="listitem"><a role="link" href="/">Home</a></li></ul></nav>`
4. Write a toggle button "Mute" with `aria-pressed` and the JavaScript to change the state.
5. Explain the difference between `aria-label`, `aria-labelledby`, and `aria-describedby`.
6. **Advanced:** Build an accessible tab list (`tablist`, `tab`, `tabpanel`) with arrow-key navigation. Follow the APG pattern.

## 3.15 Check your understanding
- What does ARIA **not** do?
- What is the first rule of ARIA?
- When do you update `aria-expanded`?
- Why is `aria-hidden="true"` on a link a problem?

---

# Lesson 4: Keyboard Navigation and `tabindex`

## 4.1 Learning objectives
After this lesson, you can:
- Explain which elements are focusable by default.
- Use `tabindex` correctly.
- Make focus visible.
- Find and fix keyboard traps.

## 4.2 Why the keyboard is important

Many users do not use a mouse: blind users, users with motor impairment, and users who prefer the keyboard. **If a function works only with a mouse, it fails these users** (WCAG 2.1.1).

## 4.3 Basic keyboard commands

| Key | Action |
|-----|--------|
| `Tab` | Go to the next focusable element. |
| `Shift + Tab` | Go to the previous focusable element. |
| `Enter` | Activate a link or a button. Submit a form. |
| `Space` | Activate a button. Check a checkbox. Scroll the page. |
| Arrow keys | Change radio buttons, choose in a `<select>`, move in tabs and menus. |
| `Esc` | Close a dialog, a menu, or a popup. |
| `Home` / `End` | Go to the first / last item in a widget. |

## 4.4 Focusable by default

These elements are in the tab order with no extra work:

- `<a href="...">` (a link **with** `href`)
- `<button>`
- `<input>` (except `type="hidden"`), `<select>`, `<textarea>`
- `<summary>` (in `<details>`)
- `<audio controls>`, `<video controls>`
- Elements with `contenteditable`
- `<iframe>` (the frame itself, and its content)

These are **not** focusable by default: `<div>`, `<span>`, `<p>`, `<li>`, headings, and `<a>` with no `href`.

```html
<a href="/about">Focusable</a>
<a>Not focusable (no href)</a>
<div>Not focusable</div>
```

## 4.5 The `tabindex` attribute

| Value | Effect |
|-------|--------|
| `tabindex="0"` | The element joins the **normal tab order**, in DOM order. |
| `tabindex="-1"` | The element is **not in the tab order**, but you can focus it with **JavaScript** (`element.focus()`) or a link to its `#id`. |
| `tabindex="1"` (or any positive number) | **Do not use.** It breaks the natural order. |

### When to use each value

| Value | Use |
|-------|-----|
| `0` | A custom widget that must be focusable (and has a role and key handlers). A scrollable region (for keyboard users to scroll it). |
| `-1` | A heading or `<main>` that you move focus to by script (after a page change). An element that is the target of a skip link. A dialog container. |
| Positive | Never. |

```html
<!-- Scrollable region that a keyboard user can focus and scroll -->
<div class="table-wrap" tabindex="0" role="region" aria-labelledby="cap">...</div>

<!-- Target for focus by script -->
<h1 id="page-title" tabindex="-1">Search results</h1>
```

```js
document.getElementById('page-title').focus();
```

## 4.6 Focus must be visible

When a keyboard user tabs to an element, a **focus indicator** must show where they are (WCAG 2.4.7).

**Never do this without a replacement:**
```css
/* Bad */
*:focus { outline: none; }
```

**Do this:**
```css
:focus-visible {
  outline: 3px solid #2563eb;
  outline-offset: 2px;
}
```

| Pseudo-class | Matches |
|--------------|---------|
| `:focus` | The element has focus (mouse and keyboard). |
| `:focus-visible` | The element has focus **and** the browser thinks that a visible indicator helps (keyboard use, in most cases). |
| `:focus-within` | The element or **a child** has focus. |

**Good focus indicator:**
- At least 2 CSS px thick.
- Contrast of at least 3:1 against the colors around it.
- Not hidden by other elements (2.4.11).

## 4.7 Tab order must be logical

The tab order follows the **DOM order** (the order in your HTML). It must match the **visual order**.

```html
<!-- Visual order: A B C. DOM order: A C B. Problem! -->
```

**Problem sources:** CSS `order` in Flexbox/Grid, `position: absolute`, `float`, and `flex-direction: row-reverse` can change the visual order, but **not** the tab order.

**Fix:** Change the HTML order, not only the CSS.

## 4.8 Keyboard traps

A **keyboard trap** is a place where focus goes in but cannot leave (WCAG 2.1.2).

| Cause | Fix |
|-------|-----|
| A modal that has no `Esc` or close button | Use `<dialog>` with `showModal()`, or add a close button and `Esc`. |
| An embedded widget (iframe, video, map) that captures keys | Test it. Tell the user how to leave. |
| JavaScript that moves focus back | Remove the script, or fix the logic. |

**Good trap:** A modal dialog should **keep** focus inside while it is open. The user must be able to leave with `Esc` or a close button. Then focus must go back to the button that opened it.

## 4.9 Custom controls

If you must build a custom control, you need all of this:

| Need | How |
|------|-----|
| Focus | `tabindex="0"` |
| Role | `role="button"` (etc.) |
| Name | Text or `aria-label` |
| State | `aria-pressed`, `aria-expanded` (etc.) |
| Keyboard | `Enter` and `Space` for buttons (key events) |
| Focus style | `:focus-visible` |

```html
<div role="button" tabindex="0" id="fake-btn">Save</div>
```
```js
const el = document.getElementById('fake-btn');
function activate() { /* save */ }
el.addEventListener('click', activate);
el.addEventListener('keydown', (e) => {
  if (e.key === 'Enter') { activate(); }
  if (e.key === ' ') { e.preventDefault(); activate(); }
});
```

Compare to: `<button type="button">Save</button>`. Always prefer the native element.

## 4.10 Pointer target size

| Rule | Size |
|------|------|
| WCAG 2.2 AA (2.5.8) | At least **24 by 24** CSS px (or enough space around) |
| Recommended (iOS, Android, WCAG AAA) | At least **44 by 44** CSS px |

```css
button, a.btn { min-height: 44px; min-width: 44px; }
```

## 4.11 Try It

1. Press `Tab` on a page that you made. Is the focus always visible? Is the order logical?
2. Add `*:focus { outline: none; }` to a page. Tab again. What do you see? Remove it and add `:focus-visible` style.
3. Make a `<div>` with `tabindex="0"`. Tab to it. Add `role`, a name, and key handlers.
4. Use Flexbox `order` or `row-reverse` on 3 links. Tab through them. What do you find?
5. Find a keyboard trap: open a dialog made with `<div>` that has no `Esc` handler. Then test the native `<dialog>`.

## 4.12 Advanced Note

- **Roving tabindex:** For a composite widget (toolbar, tabs, menu, radio-like group), only **one** item is in the tab order (`tabindex="0"`). The others have `tabindex="-1"`. Arrow keys move the `0`. This makes `Tab` leave the widget quickly.
- **`aria-activedescendant`:** An alternative for composite widgets: focus stays on the container, and the attribute points to the "active" child.
- **`inert` attribute:** Makes an element and all children **not focusable, not clickable, and hidden from assistive tech**. Use it for the rest of the page when you show a custom modal. Native `<dialog>.showModal()` does this for you.
  ```html
  <main inert>...</main>
  ```
- **Focus management in SPAs:** When a route changes, move focus to the new `<h1>` (with `tabindex="-1"`) or to `<main>`, and update `document.title`. Announce the change if needed.
- **Focus return:** After closing a modal or menu, return focus to the control that opened it. Native `<dialog>` does this.
- **Focus trap in custom modals:** Use `inert` on the background. The older way was to catch `Tab` at the first and last element with JavaScript.
- **`autofocus`:** It moves focus at page load. It can confuse screen reader users. Use it only in dialogs and for the main field of a single-purpose page.
- **`:focus-visible` rules:** Browsers show the ring for keyboard focus, and usually **not** for a mouse click on a button. For text fields, they always show it.
- **`scroll-padding` and `scroll-margin`:** Stop sticky headers from hiding focused elements (WCAG 2.4.11).
  ```css
  html { scroll-padding-top: 5rem; }
  ```
- **Accesskeys:** `accesskey` often conflicts with browser and screen reader shortcuts. Do not use it.
- **Single-key shortcuts:** WCAG 2.1.4 says that a single-character shortcut (for example `s` for search) must be possible to turn off or remap.
- **Sequential focus navigation starting point:** After a click on a non-focusable element or a fragment link, `Tab` continues from that point.
- **Dragging:** WCAG 2.5.7 needs a non-drag alternative (for example up/down buttons for a sortable list).
- **Hover and focus content:** Tooltips must be dismissible, hoverable, and persistent (WCAG 1.4.13).
- **Testing tools:** Chrome DevTools > Rendering > "Show focus rings" (not available in all versions); the "Tab Order" browser extensions; Accessibility Insights "Tab stops".

## 4.13 Exercises

1. List 6 elements that are focusable by default.
2. Explain the difference between `tabindex="0"` and `tabindex="-1"`. Why is a positive value bad?
3. Write a focus style with `:focus-visible` that has a 3:1 contrast on a white background.
4. Make a `<div role="button">` work with `Enter` and `Space`. Then replace it with `<button>`.
5. A page uses `flex-direction: row-reverse` on a nav with 3 links. What problem can this make? How do you fix it?
6. **Advanced:** Build a toolbar of 4 buttons with roving tabindex (arrow keys, `Home`, `End`).

## 4.14 Check your understanding
- Which keys do you use to activate a button and a link?
- What does `tabindex="-1"` do?
- Why must you never remove the focus outline with no replacement?
- What is a keyboard trap?

---

# Lesson 5: Skip Links and Focus Order

## 5.1 Learning objectives
After this lesson, you can:
- Build a working skip link.
- Control focus order in dialogs and page changes.
- Avoid focus problems with sticky headers.

## 5.2 The problem

On each page, a keyboard user must press `Tab` through the logo and the whole menu before they reach the main content. If the menu has 30 links, this is slow and tiring. WCAG 2.4.1 (Bypass Blocks) needs a way to skip these repeated blocks.

## 5.3 The skip link

A **skip link** is the **first** focusable element on the page. It jumps to the main content.

```html
<body>
  <a class="skip-link" href="#main">Skip to main content</a>

  <header>...</header>
  <nav>...</nav>

  <main id="main" tabindex="-1">
    <h1>Page title</h1>
    ...
  </main>
</body>
```

```css
.skip-link {
  position: absolute;
  left: 1rem;
  top: -4rem;                 /* off-screen until focused */
  padding: 0.75rem 1rem;
  background: #000;
  color: #fff;
  z-index: 1000;
}
.skip-link:focus {
  top: 1rem;                  /* visible when it has focus */
}
```

**Rules:**
1. It must be the **first** focusable element.
2. It must become **visible** when it gets focus.
3. The target (`id`) must exist.
4. Use `tabindex="-1"` on the target so that focus **really moves** in all browsers (needed for some older browsers).
5. The text must be clear: "Skip to main content".
6. For big sites, you can add more links: "Skip to search", "Skip to footer".

**Do not hide it with `display: none`.** Then it is never focusable.

## 5.4 Other ways to bypass blocks

| Method | Use |
|--------|-----|
| Landmarks (`<main>`, `<nav>`) | Screen reader users jump by landmark. |
| Headings | Users jump by heading. |
| Skip link | Keyboard users jump to the content. |
| Collapsible menu | Fewer links to pass. |

Use **all** of these together.

## 5.5 Focus order rules

1. **Follow the visual and logical order**: left to right, top to bottom (in left-to-right languages).
2. **Do not use positive `tabindex`.**
3. **Put the DOM in the correct order.** Do not rely on CSS only.
4. **Related items go together.** A label, a field, and its error message are next to each other.
5. **Moving content:** When something new appears (a dialog, an error summary, an expanded menu), place it right after the control that opened it in the DOM, or move focus to it.

## 5.6 Focus after page changes and dynamic content

| Event | Where focus must go |
|-------|---------------------|
| User opens a modal dialog | Into the dialog (first control or the heading). |
| User closes a dialog | Back to the button that opened it. |
| User submits a form with errors | To the error summary, or the first invalid field. |
| Form submits OK (no page reload) | To the success message, or the next logical place. |
| Single-page app changes view | To the new `<h1>` or `<main>`. Update `document.title`. |
| User deletes an item from a list | To the next item, or the list heading. Never lose focus to `<body>`. |
| An item loads under "Load more" | To the first new item, or announce with a live region. |

```js
// After a form fails validation
const summary = document.getElementById('error-summary');
summary.hidden = false;
summary.focus();   // summary has tabindex="-1"
```

```html
<div id="error-summary" tabindex="-1" role="alert">
  <h2>There are 2 errors</h2>
  <ul>
    <li><a href="#email">Enter a valid email address</a></li>
    <li><a href="#pw">Password must have 8 characters</a></li>
  </ul>
</div>
```

## 5.7 Sticky headers hide focus

A sticky or fixed header can **cover** the element that has focus (WCAG 2.4.11).

```css
html { scroll-padding-top: 5rem; }   /* the height of the sticky header + a gap */
```

Test: `Tab` through the page. Is every focused element fully visible (not under the header or a cookie banner)?

## 5.8 Try It

1. Add a skip link to one of your pages. Test it with `Tab`, then `Enter`.
2. Press `Tab` after you used the skip link. Where does focus go? (It must go to the first control **after** the target.)
3. Remove `tabindex="-1"` from `<main>`. Test in Firefox and Chrome. Do you see a difference?
4. Make a page with a sticky header. Tab through 20 links. Add `scroll-padding-top`.
5. Make an error summary that gets focus after a failed form submit.

## 5.9 Advanced Note

- **Skip link with `:target`:** If you use `href="#main"`, browsers set the **sequential focus navigation starting point** to `#main`, even if it is not focusable. Modern browsers move the next `Tab` to the first focusable element after it. `tabindex="-1"` makes it more reliable.
- **Outline on `<main tabindex="-1">`:** When `main` gets focus, some browsers show an outline around the whole page. You can remove the outline for `main:focus` **only** (it is not an interactive control): `main:focus { outline: none; }`. This is one of the few good cases.
- **Skip link in SPAs:** The URL hash can conflict with routers. Use a button that calls `main.focus()`, or a link with a click handler.
- **Focus order and `display`/`visibility`:** Hidden elements (`display: none`, `visibility: hidden`, `hidden`, `inert`) are not in the focus order. Off-screen elements (`left: -9999px`) **are** still focusable. Use this only for skip links and visually hidden text that must be focusable.
- **Focus on route change:** Many frameworks (Next.js, React Router, Angular) now have focus management or announcements. Check your framework docs. Test with a screen reader.
- **Announcing page changes:** An `aria-live` region that says "Page loaded: Search results" helps. Use only one.
- **`focus({ preventScroll: true })`:** Moves focus with no scroll jump.
- **Focus lost after DOM removal:** If the focused element is removed, focus goes to `<body>`. Move focus before you remove it.
- **Tab order in Shadow DOM:** The browser follows the "flattened tree" order. Test web components.
- **Skip link and `scroll-behavior: smooth`:** Smooth scroll is fine, but respect `prefers-reduced-motion`.
- **Focus order and `tabindex` on non-interactive content:** WCAG does not need every text to be focusable. Do not add `tabindex="0"` to paragraphs "for screen readers". Screen readers read non-focusable text with their own commands.
- **Roving focus and composite widgets:** See Lesson 4.
- **Focus appearance (WCAG 2.4.13, AAA):** A ring at least as big as a 2 px perimeter, with 3:1 contrast between focused and unfocused states.

## 5.10 Exercises

1. Write the HTML and the CSS for a skip link that appears on focus.
2. Explain where focus must go: (a) after a modal closes, (b) after a form fails, (c) after a user deletes the item that has focus.
3. Fix a page where a sticky header covers the focused link.
4. Write a JavaScript function `moveFocusTo(id)` that sets `tabindex="-1"` if needed and focuses an element.
5. **Advanced:** Build a "Load more" list. After the click, focus goes to the first new item, and a live region says "10 more items loaded."

## 5.11 Check your understanding
- Where must a skip link be in the page?
- Why do we use `tabindex="-1"` on `<main>`?
- Where must focus go after a modal closes?
- Why does `scroll-padding-top` help?

---

# Lesson 6: Testing with Lighthouse and Screen Readers

## 6.1 Learning objectives
After this lesson, you can:
- Run automated accessibility tests.
- Do a manual keyboard test.
- Use a screen reader for basic tests.
- Make a short audit report.

## 6.2 Three levels of testing

| Level | Tools | Finds |
|-------|-------|-------|
| **1. Automated** | Lighthouse, axe DevTools, WAVE, HTML validator | About **30 to 40 percent** of issues (missing alt, low contrast, missing labels, bad ARIA) |
| **2. Manual** | Keyboard test, zoom, color checks, reading the page | Focus order, visible focus, logic, clear text |
| **3. Assistive technology and users** | Screen readers, voice control, magnifier, real users with disabilities | Real usability problems |

**A score of 100 in Lighthouse does not mean that a page is accessible.** It means that the automatic tests did not find a problem.

## 6.3 Lighthouse

Lighthouse is built into Chrome.

1. Open DevTools (`F12`) > **Lighthouse** tab.
2. Choose **Accessibility** (and others if you wish).
3. Choose **Mobile** or **Desktop**.
4. Click **Analyze page load**.
5. Read the **Failed audits**. Each one links to a help page.
6. Look at the **Manual checks** list. Do them by hand.

Common failures:
- Images with no `alt`.
- Low color contrast.
- Form fields with no labels.
- Links with no discernible name.
- `[aria-*]` attributes that are not valid.
- Missing `lang` on `<html>`.
- Heading elements not in sequential order.
- Buttons with no accessible name.
- No `<title>`.

## 6.4 Other automated tools

| Tool | Notes |
|------|-------|
| **axe DevTools** (browser extension, free version) | Very good rules. Shows how to fix each issue. |
| **WAVE** (`wave.webaim.org`, extension) | Shows icons on the page. Easy for beginners. |
| **Accessibility Insights for Web** | Microsoft tool. Has a guided manual test ("Assessment"). |
| **Pa11y**, **axe-core**, **jest-axe** | Run tests in a script or CI pipeline. |
| **W3C Validator** | Finds invalid HTML (duplicate IDs, wrong nesting). |
| **Chrome DevTools > Accessibility pane** | Shows the accessibility tree, names, and roles. |

## 6.5 Manual test checklist (10 minutes)

Do these on each key page:

1. **Keyboard:** Use only the keyboard. Can you reach and use every control? Is the order logical? Is focus always visible? Is there a trap?
2. **Skip link:** Does it appear and work?
3. **Zoom:** Zoom to 200%. Then 400% (or a 320 px window). Is there loss of content? Two-way scroll?
4. **Text spacing:** Use a bookmarklet or extension that changes text spacing. Is any text cut?
5. **Color:** Is meaning shown by more than color? Check contrast of text, borders, and icons.
6. **Headings and landmarks:** Check the outline and landmarks with an extension.
7. **Images:** Turn off images. Does the page still make sense?
8. **Forms:** Do all fields have labels? Are errors clear and linked to fields?
9. **Media:** Do videos have captions? Does audio have a transcript? Is there autoplay?
10. **Motion:** Turn on "reduce motion" in the OS. Do animations stop?

## 6.6 Screen readers

| Screen reader | Platform | Cost | Common browser |
|---------------|----------|------|----------------|
| **NVDA** | Windows | Free | Firefox, Chrome |
| **JAWS** | Windows | Paid | Chrome, Edge |
| **Narrator** | Windows | Built in | Edge |
| **VoiceOver** | macOS, iOS | Built in | Safari |
| **TalkBack** | Android | Built in | Chrome |
| **Orca** | Linux | Free | Firefox |

For a first test, use **NVDA with Firefox** (Windows) or **VoiceOver with Safari** (Mac).

### Basic NVDA commands

| Command | Action |
|---------|--------|
| `Ctrl` | Stop speech |
| `Insert + Down arrow` (or `Caps Lock + Down`) | Read all |
| `H` / `Shift + H` | Next / previous heading |
| `1` to `6` | Next heading of that level |
| `D` | Next landmark |
| `K` | Next link |
| `B` | Next button |
| `F` | Next form field |
| `T` | Next table |
| `Insert + F7` | List of links, headings, landmarks |
| `Tab` | Next focusable element |
| `Insert + Space` | Toggle browse and focus mode |

### Basic VoiceOver commands (macOS)

| Command | Action |
|---------|--------|
| `Cmd + F5` | Turn VoiceOver on or off |
| `VO` = `Ctrl + Option` | The VoiceOver modifier |
| `VO + Right arrow` | Next item |
| `VO + U` | Open the **Rotor** (lists of headings, links, landmarks) |
| `VO + Space` | Activate |
| `VO + A` | Read all |

### What to listen for

1. Does the page **title** make sense?
2. Do **headings** give a good overview?
3. Are **landmarks** present and named?
4. Does each **link** make sense out of context?
5. Does each **image** have good alt (or is it skipped if decorative)?
6. Does each **form field** announce its label, type, required state, and help text?
7. Are **errors** announced?
8. Are **dynamic changes** (menus, dialogs, messages) announced?
9. Are **tables** read with the right headers?

**Tip:** Close your eyes (or turn off the screen) for a while. You will find problems fast.

## 6.7 Mobile testing

- **iOS:** Settings > Accessibility > VoiceOver. Swipe right and left to move. Double-tap to activate.
- **Android:** Settings > Accessibility > TalkBack.
- Test touch target size, orientation (portrait and landscape), and zoom.

## 6.8 Write an audit report

A short report has these parts:

| Part | Content |
|------|---------|
| **Page and date** | URL, browser, screen reader, date |
| **Summary** | Number of issues by severity |
| **Issues table** | One row per issue |

| # | Issue | WCAG SC | Severity | Where | How to fix |
|---|-------|---------|----------|-------|------------|
| 1 | Image has no alt | 1.1.1 (A) | High | Hero image | Add descriptive `alt` |
| 2 | Text contrast is 2.8:1 | 1.4.3 (AA) | High | Subtitle | Use `#595959` or darker |
| 3 | No visible focus | 2.4.7 (AA) | High | All links | Add `:focus-visible` style |

**Severity guide:**
- **Critical / High:** Blocks a user from a task (no keyboard access, no labels).
- **Medium:** Makes a task hard (poor contrast, unclear link text).
- **Low:** Small barrier (redundant ARIA, minor structure issue).

## 6.9 Make accessibility part of your workflow

1. **Design:** Check contrast and target size in the design.
2. **Code:** Use semantic HTML first. Use a linter (`eslint-plugin-jsx-a11y`, `axe-linter`, `html-validate`).
3. **Review:** Add an accessibility check to each pull request.
4. **CI:** Run `axe-core` or `pa11y` in your build pipeline.
5. **Release:** Do a manual keyboard and screen reader test of key flows.
6. **After release:** Publish a way to report barriers. Fix them.

## 6.10 Try It

1. Run Lighthouse on one of your earlier projects. Write the score and the failed audits.
2. Run axe DevTools and WAVE on the same page. Compare the results.
3. Do the 10-minute manual checklist. Write every problem.
4. Install NVDA (Windows) or turn on VoiceOver (Mac). Go through your page with only the headings (`H` or Rotor), then only the links, then only the form fields.
5. Write a short audit report with at least 5 issues.

## 6.11 Advanced Note

- **Lighthouse scoring:** The accessibility score is a weighted average of the audits. Some audits have more weight. A page with a keyboard trap can still get 100.
- **axe-core in tests:**
  ```js
  // Playwright + axe
  import AxeBuilder from '@axe-core/playwright';
  const results = await new AxeBuilder({ page }).analyze();
  expect(results.violations).toEqual([]);
  ```
- **CI tools:** Lighthouse CI, Pa11y CI, axe-linter (GitHub Action), and Storybook a11y addon.
- **Accessibility tree in DevTools:** Chrome > DevTools > Elements > Accessibility pane. Firefox has a full **Accessibility Inspector** with a simulation of color blindness and contrast checks.
- **Vision simulations:** Chrome DevTools > Rendering > "Emulate vision deficiencies" (blurred vision, protanopia, deuteranopia, tritanopia, achromatopsia).
- **Screen reader and browser pairs:** Support differs. Common recommended pairs: NVDA + Firefox, JAWS + Chrome, VoiceOver + Safari, TalkBack + Chrome. Do not test only with one.
- **Screen reader modes:** Windows screen readers have **browse mode** (virtual cursor, many keys are commands) and **focus/forms mode** (keys go to the control). Roles such as `application` and form fields switch the mode.
- **Speech Viewer:** NVDA has a "Speech Viewer" that shows the text it speaks. Use it to record issues.
- **Voice control test:** Use Windows Voice Access or macOS/iOS Voice Control. Say "show numbers" or "click Search". Check that visible labels work.
- **Real users:** The best test is with people who have disabilities. Pay them for their time. Many companies and communities offer this service.
- **Cognitive checks:** Is the language plain? Are instructions clear? Is there a time limit? Can users undo?
- **Overlays and widgets:** Accessibility "overlay" products do not fix inaccessible code. Experts and many users advise against them.
- **Standards for testing:** W3C **WCAG-EM** (Evaluation Methodology) and the **ACT Rules** describe how to test in a repeatable way.
- **Document accessibility:** PDF and Word documents have their own rules (PDF/UA, tagged PDF).
- **Email accessibility:** HTML emails need semantic structure and alt text too.

## 6.12 Exercises

1. List 5 things that automatic tools **cannot** find.
2. Run Lighthouse on any website. Choose 3 failed audits and explain how to fix each.
3. With a screen reader, list all headings of a news website's home page. Is the outline logical?
4. Write the NVDA or VoiceOver commands to: (a) list all links, (b) jump to the next landmark, (c) read the whole page.
5. Write an audit report for a page with 5 issues, each with a WCAG SC, a severity, and a fix.
6. **Advanced:** Add `axe-core` to a small project test with Playwright or Puppeteer. Make the test fail if there are violations.

## 6.13 Check your understanding
- What part of the issues can automated tools find?
- What are 3 things to check in a manual test?
- Name a free screen reader for Windows.
- Why must you test with more than one tool?

---

# Lesson 7: Module Project - Audit and Fix a Broken Page

## 7.1 Project goal
You get an **inaccessible page** with many problems. You must:
1. **Audit** it with tools and manual tests.
2. **Write a report** of the issues.
3. **Fix** all issues.
4. **Re-test** and show the improvement.

## 7.2 Project folder

```
project/
├── broken/
│   └── index.html        (the page with problems: do not edit)
├── fixed/
│   ├── index.html        (your fixed version)
│   ├── style.css
│   └── script.js
├── AUDIT.md              (your report)
└── README.md
```

## 7.3 The broken page

Save this as `broken/index.html`. Use it as is. Do not fix it in this file.

```html
<html>
<head>
  <title>Document</title>
  <meta name="viewport" content="width=device-width, initial-scale=1, user-scalable=no">
  <style>
    body { font-family: Arial; background: #fff; color: #999; }
    *:focus { outline: none; }
    .top { background: #eee; padding: 10px; }
    .menu span { margin-right: 15px; color: #aaa; cursor: pointer; }
    .btn { background: #ccc; color: #fff; padding: 6px 10px; display: inline-block; cursor: pointer; }
    .err { color: red; }
    .hero { width: 100%; max-width: 600px; }
    td, th { border: 1px solid #ddd; padding: 4px; }
    .modal { display: none; position: fixed; top: 20%; left: 20%; background: #fff; border: 1px solid #000; padding: 20px; }
  </style>
</head>
<body>
  <div class="top">
    <div style="font-size:24px">Green Garden Shop</div>
    <div class="menu">
      <span onclick="go('home')">Home</span>
      <span onclick="go('plants')">Plants</span>
      <span onclick="go('contact')">Contact</span>
    </div>
  </div>

  <div class="content" tabindex="3">
    <h3>Welcome to Green Garden</h3>
    <img src="hero.jpg" class="hero">
    <img src="divider.png" alt="image">
    <h1>Our plants</h1>
    <p>We sell plants for home and garden. <a href="plants.html">Click here</a> to see all plants.
       <a href="sale.html">Click here</a> for sale items.</p>

    <h4>Opening hours</h4>
    <table>
      <tr><td><b>Day</b></td><td><b>Hours</b></td></tr>
      <tr><td>Mon-Fri</td><td>9-18</td></tr>
      <tr><td>Sat</td><td>10-14</td></tr>
    </table>

    <h2>Newsletter</h2>
    <form action="/subscribe" method="post">
      <input type="text" placeholder="Your name">
      <input type="text" placeholder="Email">
      <div class="btn" onclick="subscribe()">Sign up</div>
      <p class="err">Wrong value</p>
    </form>

    <video src="intro.mp4" autoplay loop></video>

    <p>Language note: "Gartenfreund" means friend of the garden.</p>

    <div class="btn" onclick="openModal()">Help</div>
    <div class="btn" onclick="toggleCart()"><img src="cart.svg"></div>
  </div>

  <div class="modal" id="modal">
    <div style="font-size:20px">Need help?</div>
    <p>Call us.</p>
    <div class="btn" onclick="closeModal()">X</div>
  </div>

  <script>
    function openModal() { document.getElementById('modal').style.display = 'block'; }
    function closeModal() { document.getElementById('modal').style.display = 'none'; }
    function subscribe() { alert('Thanks'); }
    function go(p) { location.href = p + '.html'; }
    function toggleCart() {}
  </script>
</body>
</html>
```

## 7.4 Steps

1. **Run the automated tests** (Lighthouse, axe, WAVE, W3C validator) on `broken/index.html`. Write the scores.
2. **Do the manual tests**: keyboard only, 200% zoom, contrast, headings, landmarks, forms, and a screen reader.
3. **Write `AUDIT.md`** with an issues table: issue, WCAG SC, severity, location, fix. Find as many issues as you can **before** you read the answer key.
4. **Copy** `broken/index.html` to `fixed/index.html`. Move the CSS to `style.css` and the script to `script.js`.
5. **Fix all issues** with semantic HTML first. Use ARIA only where needed.
6. **Re-test** with the same tools. Write the new scores.
7. **Write `README.md`** with before and after scores, and what you learned.
8. Commit and push:
   ```bash
   git add .
   git commit -m "Add Module 08 accessibility audit and fix"
   git push
   ```

## 7.5 Requirements

### Level 1: Beginner (required)
- [ ] `AUDIT.md` lists **at least 15** issues with WCAG references.
- [ ] All issues in the answer key (7.6) that are marked "Basic" are fixed.
- [ ] The fixed page validates with 0 errors in the W3C validator.
- [ ] Lighthouse Accessibility score of 95 or higher on the fixed page.
- [ ] The whole fixed page works with the keyboard only.
- [ ] Focus is always visible.
- [ ] README has before and after scores.

### Level 2: Intermediate (recommended)
- [ ] Fix **all** issues in the answer key, including "Intermediate".
- [ ] Use a native `<dialog>` for the help modal.
- [ ] Add an error summary and `aria-describedby` for the form.
- [ ] Add `prefers-reduced-motion` support and a pause for the video, or remove autoplay.
- [ ] Add a live region message after "Sign up".
- [ ] Test with a screen reader. Write what you heard in `AUDIT.md`.

### Level 3: Advanced (optional)
- [ ] Find 3 more issues that are **not** in the answer key.
- [ ] Add an automated test with `axe-core` (Playwright, Puppeteer, or Jest) that passes on `fixed/` and fails on `broken/`.
- [ ] Add support for `forced-colors` and `prefers-contrast`.
- [ ] Test with voice control (say "click Sign up").
- [ ] Add a short accessibility statement page.

## 7.6 Answer key (read **after** your own audit)

| # | Issue | WCAG SC | Level | How to fix |
|---|-------|---------|-------|------------|
| 1 | `<html>` has no `lang` | 3.1.1 (A) | Basic | `<html lang="en">` |
| 2 | `<title>Document</title>` is not useful | 2.4.2 (A) | Basic | `Green Garden Shop \| Plants for home and garden` |
| 3 | Viewport has `user-scalable=no` | 1.4.4 (AA) | Basic | Remove `user-scalable=no` |
| 4 | Text color `#999` on white has contrast about 2.8:1 | 1.4.3 (AA) | Basic | Use `#595959` or darker |
| 5 | `*:focus { outline: none }` removes focus | 2.4.7 (AA) | Basic | Add a `:focus-visible` style |
| 6 | Site name and menu are `<div>` and `<span>`: no landmarks | 1.3.1 (A) | Basic | Use `<header>`, `<nav aria-label="Main">`, `<ul>`, `<li>`, `<a>` |
| 7 | Menu items are `<span onclick>`: not focusable, not links | 2.1.1 (A), 4.1.2 (A) | Basic | Use real links `<a href="...">` |
| 8 | No skip link | 2.4.1 (A) | Basic | Add a skip link and `<main id="main">` |
| 9 | No `<main>` landmark | 1.3.1 (A) | Basic | Wrap content in `<main>` |
| 10 | `tabindex="3"` on `.content` (positive and not interactive) | 2.4.3 (A) | Basic | Remove it |
| 11 | Heading order: `<h3>`, then `<h1>`, `<h4>`, `<h2>` | 1.3.1 (A), 2.4.6 (AA) | Basic | One `<h1>`, then `<h2>`, then `<h3>` in order |
| 12 | Hero `<img>` has no `alt` | 1.1.1 (A) | Basic | Add descriptive `alt`, `width`, `height` |
| 13 | Divider image has `alt="image"` (decorative) | 1.1.1 (A) | Basic | `alt=""` |
| 14 | Two links with the text "Click here" | 2.4.4 (A) | Basic | "See all plants", "See sale items" |
| 15 | Table headers are `<td><b>`: no `<th>`, no `<caption>` | 1.3.1 (A) | Basic | Use `<caption>`, `<thead>`, `<th scope="col">` |
| 16 | Form fields have only placeholders, no labels | 3.3.2 (A), 1.3.1 (A), 4.1.2 (A) | Basic | Add `<label for>`, `id`, `name`, `autocomplete`, `type="email"` |
| 17 | Submit "button" is a `<div onclick>` | 2.1.1 (A), 4.1.2 (A) | Basic | `<button type="submit">` |
| 18 | White text `#fff` on `#ccc` button: contrast about 1.6:1 | 1.4.3 (AA) | Basic | Use dark text on a light button, or white on a dark color |
| 19 | Error text uses only red color and says "Wrong value" | 1.4.1 (A), 3.3.1 (A), 3.3.3 (AA) | Intermediate | Clear message, icon, `aria-describedby`, `aria-invalid`, `role="alert"` |
| 20 | Video has `autoplay loop` and no controls or captions | 1.4.2 (A), 2.2.2 (A), 1.2.2 (A) | Intermediate | Remove autoplay, add `controls`, `<track kind="captions">` |
| 21 | German phrase has no `lang` | 3.1.2 (AA) | Intermediate | `<span lang="de">Gartenfreund</span>` |
| 22 | "Help" is a `<div onclick>` | 2.1.1 (A), 4.1.2 (A) | Basic | `<button type="button">` |
| 23 | Cart button is an image with no name | 4.1.2 (A), 1.1.1 (A) | Basic | `<button type="button" aria-label="Shopping cart"><img alt="" ...></button>` or SVG with `aria-hidden` |
| 24 | Modal is a `<div>`: no role, no name, no focus management, no `Esc` | 4.1.2 (A), 2.1.1 (A), 2.4.3 (A) | Intermediate | Use `<dialog>` + `showModal()`, a heading, and a real close button |
| 25 | Close button is a `<div>` with the text "X" | 4.1.2 (A) | Basic | `<button type="button" aria-label="Close help dialog">` |
| 26 | Small targets (padding 6px 10px, no minimum size) | 2.5.8 (AA) | Intermediate | `min-height: 44px; min-width: 44px` |
| 27 | `<td>`-based CSS uses tiny padding and low contrast borders | 1.4.11 (AA) | Intermediate | Borders of at least 3:1 where needed, more padding |
| 28 | Inline styles and a fixed `font-size` in `px` on the shop name | 1.4.4 (AA) | Intermediate | Move to CSS, use `rem` |
| 29 | Script `alert('Thanks')` for the success message | 4.1.3 (AA) | Intermediate | A live region (`role="status"`) |
| 30 | `<html>`, `<head>`, `<body>` missing doctype | (validity) | Basic | Add `<!DOCTYPE html>` and `<meta charset="UTF-8">` |

## 7.7 Fixed page starter (partial)

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Green Garden Shop | Plants for home and garden</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <a class="skip-link" href="#main">Skip to main content</a>

  <header>
    <p class="site-name">Green Garden Shop</p>
    <nav aria-label="Main">
      <ul>
        <li><a href="index.html" aria-current="page">Home</a></li>
        <li><a href="plants.html">Plants</a></li>
        <li><a href="contact.html">Contact</a></li>
      </ul>
    </nav>
  </header>

  <main id="main" tabindex="-1">
    <h1>Welcome to Green Garden</h1>
    <img src="hero.jpg" alt="Shelves with green house plants in clay pots" width="600" height="400" class="hero" />

    <p>We sell plants for home and garden.
       <a href="plants.html">See all plants</a>.
       <a href="sale.html">See sale items</a>.</p>

    <section aria-labelledby="hours-title">
      <h2 id="hours-title">Opening hours</h2>
      <table>
        <caption>Opening hours by day</caption>
        <thead><tr><th scope="col">Day</th><th scope="col">Hours</th></tr></thead>
        <tbody>
          <tr><th scope="row">Mon-Fri</th><td>9:00 to 18:00</td></tr>
          <tr><th scope="row">Sat</th><td>10:00 to 14:00</td></tr>
        </tbody>
      </table>
    </section>

    <section aria-labelledby="news-title">
      <h2 id="news-title">Newsletter</h2>
      <form action="/subscribe" method="post">
        <label for="name">Your name</label>
        <input type="text" id="name" name="name" autocomplete="name" required />

        <label for="email">Email address</label>
        <input type="email" id="email" name="email" autocomplete="email" required aria-describedby="email-error" />
        <p id="email-error" class="error" hidden></p>

        <button type="submit">Sign up</button>
      </form>
      <div id="status" role="status"></div>
    </section>

    <!-- Continue: video with controls and captions, language span, help dialog, cart button -->
  </main>
</body>
</html>
```

## 7.8 `AUDIT.md` template

```markdown
# Accessibility audit: Green Garden Shop

**Date:** 2026-xx-xx
**Browsers and tools:** Chrome (Lighthouse, axe), Firefox + NVDA, keyboard only

## Scores
| Test | Broken page | Fixed page |
|------|-------------|------------|
| Lighthouse Accessibility | | |
| axe issues | | |
| WAVE errors | | |
| W3C validator errors | | |

## Issues
| # | Issue | WCAG SC | Severity | Location | Fix |
|---|-------|---------|----------|----------|-----|
| 1 | | | | | |

## Screen reader notes
What I heard, and what was confusing:

## What I learned
```

## 7.9 Self-check list

1. Does the fixed page pass the W3C validator with 0 errors?
2. Is the Lighthouse Accessibility score 95 or higher?
3. Can you use **every** function with only the keyboard?
4. Is focus always visible and in a logical order?
5. Do all images, buttons, links, and form fields have correct accessible names?
6. Is the heading outline correct?
7. Do all text and UI colors pass the contrast rules?
8. Does the page work at 200% zoom and at 320 px width?
9. Is there no ARIA that a native element can replace?
10. Did you test with a screen reader at least once?
11. Does `AUDIT.md` show before and after results?

## 7.10 Grading guide (self-assessment)

| Area | Points |
|------|--------|
| Quality of the audit (`AUDIT.md`: issues, SC, severity) | 20 |
| Fixes: semantic HTML (landmarks, headings, buttons, links, tables) | 20 |
| Fixes: names, labels, alt text, forms | 15 |
| Fixes: keyboard, focus, skip link, dialog | 15 |
| Fixes: color, contrast, zoom, motion | 10 |
| Re-test results (scores, validator) | 10 |
| Git commits and README | 10 |
| **Total** | **100** |

A score of 80 or more means you are ready for Module 09.

---

# Module 08 Review

## Final quiz

**Questions**

1. What do the letters in POUR mean?
2. Which WCAG level is the usual legal target?
3. What are the minimum contrast ratios for normal text and for large text?
4. When do you use `alt=""`?
5. What is the first rule of ARIA?
6. Does `role="button"` on a `<div>` make it work with the keyboard?
7. What does `tabindex="-1"` do? Why do you not use positive `tabindex` values?
8. Where must a skip link be in the page, and when must it be visible?
9. Where must focus go after a modal dialog closes?
10. What part of the accessibility issues can automated tools find? What must you do about the rest?

**Answers**

1. Perceivable, Operable, Understandable, Robust.
2. Level AA.
3. 4.5:1 for normal text. 3:1 for large text (and for UI components and graphics).
4. When an image is only decoration and adds no information or function.
5. If a native HTML element or attribute gives the meaning and behavior that you need, use it. Do not add ARIA.
6. No. ARIA changes only what assistive technology announces. You must add focus (`tabindex`), key handling, and styles yourself. A real `<button>` is better.
7. `tabindex="-1"` makes an element focusable by script or link, but removes it from the tab order. Positive values change the natural order and make it confusing.
8. It must be the first focusable element. It must become visible when it gets focus.
9. Back to the control that opened the dialog.
10. About 30 to 40 percent. Do manual tests (keyboard, zoom, contrast, reading) and test with screen readers and real users.

## Common mistakes

| Mistake | Fix |
|---------|-----|
| Thinking that a Lighthouse score of 100 means "accessible" | Do manual and screen reader tests too. |
| `alt="image of ..."` or the file name | Describe the purpose. Do not start with "image of". |
| Leaving out `alt` | Always write `alt`. Use `alt=""` for decoration. |
| Low-contrast "light grey" text | Use at least 4.5:1 for normal text. |
| Color as the only signal | Add text or an icon. |
| `outline: none` with no replacement | Use a visible `:focus-visible` style. |
| `<div onclick>` or `<span onclick>` | Use `<button>` or `<a href>`. |
| `role="button"` on a `<div>` with no keyboard support | Use `<button>`. |
| ARIA that repeats native meaning (`<nav role="navigation">`) | Remove it. |
| `aria-hidden="true"` on a focusable element | Remove it, or use `hidden` / `inert`. |
| `aria-label` that does not match the visible text | Include the visible text in the name. |
| `aria-expanded` that does not change | Update the state with JavaScript. |
| Positive `tabindex` values | Remove them. Fix the DOM order. |
| No skip link | Add one as the first focusable element. |
| Focus lost after closing a dialog or deleting an item | Move focus to a logical place. |
| Sticky header covers focus | Use `scroll-padding-top`. |
| `user-scalable=no` or `maximum-scale=1` | Remove them. |
| Autoplay with sound | Remove autoplay. Give controls. |
| No captions or transcripts | Add them. |
| Error text that says only "Invalid" | Say what is wrong and how to fix it. |
| Testing with only one tool | Use automated, manual, and screen reader tests. |

## Glossary

| Term | Definition |
|------|------------|
| a11y | A short form of "accessibility". |
| Accessible name | The text that assistive technology uses to name a control. |
| Accessibility tree | A tree of objects (name, role, state) that the browser gives to assistive technology. |
| Assistive technology (AT) | Software or devices that help people with disabilities to use a computer. |
| ARIA | A set of attributes that add accessibility information. |
| Contrast ratio | The difference in brightness between two colors (1:1 to 21:1). |
| Focus | The element that receives keyboard input. |
| Focus indicator | The visible mark that shows which element has focus. |
| Keyboard trap | A place where keyboard focus enters but cannot leave. |
| Landmark | A page region that assistive technology can jump to. |
| Live region | An area where changes are announced by a screen reader. |
| POUR | Perceivable, Operable, Understandable, Robust. |
| Screen reader | Software that reads the screen aloud or to a braille display. |
| Skip link | A link that jumps over repeated blocks to the main content. |
| Success criterion (SC) | A numbered, testable rule in WCAG. |
| `tabindex` | An attribute that controls if and how an element receives focus. |
| WCAG | Web Content Accessibility Guidelines. |

## Module 08 progress checklist (copy to `PROGRESS.md`)

```markdown
## Module 08: Accessibility
- [ ] Lesson 1: Principles and WCAG basics
- [ ] Lesson 2: Alt text best practices
- [ ] Lesson 3: ARIA roles, labels, and when not to use them
- [ ] Lesson 4: Keyboard navigation and tabindex
- [ ] Lesson 5: Skip links and focus order
- [ ] Lesson 6: Testing with Lighthouse and screen readers
- [ ] Lesson 7: Audit and fix a broken page project
- [ ] Final quiz (8/10 or more)
- [ ] AUDIT.md written with before and after scores
- [ ] Fixed page validated with W3C
- [ ] Fixed page tested with keyboard only
- [ ] Fixed page tested with a screen reader
- [ ] Project pushed to GitHub
```

## Cheat sheet: Module 08

```html
<!-- Page basics -->
<html lang="en">
<title>Clear page title | Site</title>
<meta name="viewport" content="width=device-width, initial-scale=1" />

<!-- Skip link + landmarks -->
<a class="skip-link" href="#main">Skip to main content</a>
<header>...<nav aria-label="Main">...</nav></header>
<main id="main" tabindex="-1">...</main>
<footer>...</footer>

<!-- Images -->
<img src="a.jpg" alt="What matters here" width="600" height="400" />
<img src="line.png" alt="" />

<!-- Names -->
<button type="button" aria-label="Close dialog">×</button>
<label for="e">Email</label>
<input id="e" type="email" required aria-describedby="e-hint" aria-invalid="false" />
<p id="e-hint">Example: name@example.com</p>

<!-- State -->
<button type="button" aria-expanded="false" aria-controls="menu">Menu</button>
<button type="button" aria-pressed="false">Mute</button>

<!-- Live region -->
<div role="status" aria-live="polite"></div>

<!-- Focusable regions -->
<div tabindex="0" role="region" aria-labelledby="cap">...</div>
```

```css
:focus-visible { outline: 3px solid #2563eb; outline-offset: 2px; }
html { scroll-padding-top: 5rem; }
button, a.btn { min-height: 44px; min-width: 44px; }
.visually-hidden { position: absolute; width: 1px; height: 1px; overflow: hidden; clip: rect(0 0 0 0); white-space: nowrap; }
@media (prefers-reduced-motion: reduce) { * { animation: none !important; transition: none !important; } }
```

| Check | Rule |
|-------|------|
| Text contrast | 4.5:1 (large text 3:1) |
| UI and graphics contrast | 3:1 |
| Target size | 24 by 24 px minimum (44 by 44 px best) |
| Zoom | Works at 200%, and at 320 px width |
| Keyboard | Everything works. Focus is visible. No trap. |
| `tabindex` | Use `0` and `-1` only |
| ARIA | Native element first. No ARIA is better than bad ARIA. |

| Key (NVDA) | Action |
|------------|--------|
| `H` / `1` to `6` | Next heading |
| `D` | Next landmark |
| `K` | Next link |
| `F` | Next form field |
| `Insert + F7` | List of links, headings, landmarks |

## Next module
Go to **Module 09: Head, Meta, and SEO**. You learn `<title>`, meta description, viewport, Open Graph, favicons, canonical URLs, robots, sitemaps, and JSON-LD.
