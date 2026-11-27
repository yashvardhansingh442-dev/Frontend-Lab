# Module 07: Semantic HTML

**Folder:** `07-semantic-html/`
**Level:** Beginner (with Advanced notes)
**Time:** 6 to 8 hours
**Writing style:** ASD-STE100 (Simplified Technical English)
**Prerequisites:** Modules 01 to 06

---

## Module Overview

### Goal
Learn to choose HTML elements for their **meaning**. Build page structures that browsers, search engines, and assistive tools can understand.

### What you learn
After this module, you can:
1. Explain what semantic HTML is and why it is important.
2. Use `<header>`, `<main>`, `<footer>`, `<section>`, `<article>`, and `<aside>` correctly.
3. Choose between `<div>`, `<span>`, and semantic elements.
4. Use `<details>`, `<summary>`, `<dialog>`, `<time>`, and `<address>`.
5. Build a correct heading hierarchy and document outline.
6. Build a blog article layout.

### The main idea of this module
Every HTML element has a **meaning** (a semantic). A good developer asks: *"What is this content?"* and not *"How must it look?"*

| Question about appearance (bad) | Question about meaning (good) |
|---------------------------------|-------------------------------|
| "How do I make this big and bold?" | "Is this a heading?" |
| "How do I put this on the right?" | "Is this a side note (`<aside>`)?" |
| "How do I put a line at the bottom?" | "Is this the footer of the page?" |

CSS gives the appearance. HTML gives the meaning.

### Folder structure for this module
```
07-semantic-html/
├── lesson-01-why-semantics-matter.md
├── lesson-02-page-structure-elements.md
├── lesson-03-div-span-vs-semantic.md
├── lesson-04-details-dialog-time-address.md
├── lesson-05-outline-heading-hierarchy.md
├── lesson-06-project-blog-article-layout.md
├── examples/
├── exercises/
└── project/
```

---

# Lesson 1: Why Semantics Matter

## 1.1 Learning objectives
After this lesson, you can:
- Define semantic HTML.
- Give 4 reasons to use it.
- Compare a non-semantic page with a semantic page.

## 1.2 What is semantic HTML?

**Semantic** HTML uses elements that **describe their content**. The element name tells what the content is.

| Non-semantic | Semantic |
|--------------|----------|
| `<div>`, `<span>` | `<header>`, `<nav>`, `<main>`, `<article>`, `<footer>`, `<time>`, `<address>` |
| Name says nothing. | Name tells the role. |

## 1.3 Compare two pages

### Page A: Non-semantic ("div soup")

```html
<div class="top">
  <div class="logo">My Blog</div>
  <div class="menu">
    <div><a href="/">Home</a></div>
    <div><a href="/about">About</a></div>
  </div>
</div>
<div class="content">
  <div class="post">
    <div class="title">How I learned HTML</div>
    <div class="text">It took me three weeks.</div>
  </div>
</div>
<div class="bottom">Copyright 2026</div>
```

### Page B: Semantic

```html
<header>
  <p>My Blog</p>
  <nav aria-label="Main">
    <ul>
      <li><a href="/">Home</a></li>
      <li><a href="/about">About</a></li>
    </ul>
  </nav>
</header>
<main>
  <article>
    <h1>How I learned HTML</h1>
    <p>It took me three weeks.</p>
  </article>
</main>
<footer>
  <p><small>Copyright 2026</small></p>
</footer>
```

Both pages can **look** the same with CSS. But only Page B has **meaning**.

## 1.4 Four reasons to use semantic HTML

### 1. Accessibility
- Screen readers use **landmarks** (`<header>`, `<nav>`, `<main>`, `<footer>`, `<aside>`). The user can jump to the main content, or to the menu, with one key.
- A `<div>` gives no information. A user of a screen reader must listen to everything.

### 2. SEO (Search Engine Optimization)
- Search engines read the structure to understand which content is important.
- `<h1>`, `<article>`, `<time>`, and `<nav>` help a search engine to understand your page.

### 3. Maintenance
- Code is easier to read. `<footer>` is clearer than `<div class="bottom">`.
- Other developers (and you, in 6 months) can find parts of the page faster.

### 4. Built-in behavior
- Many elements give you free features: `<button>` has keyboard support, `<details>` opens and closes, `<dialog>` traps focus.
- Reader modes, voice assistants, and browser tools use semantic elements.

## 1.5 Semantic elements you know already

| Element | Meaning |
|---------|---------|
| `<h1>` to `<h6>` | Headings |
| `<p>` | Paragraph |
| `<ul>`, `<ol>`, `<dl>` | Lists |
| `<table>` | Data in rows and columns |
| `<figure>`, `<figcaption>` | A figure with a caption |
| `<blockquote>`, `<cite>` | A quote and its source |
| `<strong>`, `<em>` | Importance and stress |
| `<nav>` | Navigation |
| `<form>`, `<label>`, `<fieldset>` | Forms |
| `<button>` | A button |

## 1.6 New semantic elements in this module

| Element | Meaning |
|---------|---------|
| `<header>` | Introduction or heading area |
| `<main>` | The main content of the page |
| `<footer>` | Footer of the page or a section |
| `<section>` | A themed group of content with a heading |
| `<article>` | A self-contained piece of content |
| `<aside>` | Content that is related, but not main |
| `<details>`, `<summary>` | A disclosure widget (show and hide) |
| `<dialog>` | A dialog box or modal |
| `<time>` | A date or time |
| `<address>` | Contact information |

## 1.7 Try It

1. Open a website that you use. Right-click and choose **View Page Source**.
2. Search for `<div`. Count the `<div>` elements. Search for `<header`, `<nav`, `<main`, `<article`, and `<footer`. Count these also.
3. Open DevTools > Accessibility. Find the page **landmarks** in the tree.
4. Write two lists: elements the site uses well, and places where a semantic element is better than `<div>`.

## 1.8 Advanced Note

- **Accessibility tree:** The browser builds a second tree for assistive tools. Each HTML element maps to a **role**. For example, `<nav>` becomes `navigation`, `<main>` becomes `main`, `<button>` becomes `button`. `<div>` becomes `generic` (no meaning).
- **First rule of ARIA:** If you can use a native HTML element with the meaning that you need, use it. Do not add ARIA roles to a `<div>` to copy it. Native elements are more stable and have built-in keyboard support.
- **Machine-readable data:** Semantic HTML works with other tools: **Microdata**, **RDFa**, and **JSON-LD** (Module 09) for structured data.
- **Reader mode:** Browser reader modes (for example Safari Reader) use `<article>`, `<h1>`, and `<time>` to find the main text.
- **Voice assistants and AI crawlers** use structure to extract content. Clear structure helps them.
- **Print and CSS:** A semantic structure makes it easier to write print CSS and responsive CSS (for example `header`, `nav`, `main > article`).
- **WCAG:** Success Criterion 1.3.1 (Info and Relationships) and 2.4.1 (Bypass Blocks) need correct structure.
- **Do not overuse:** Semantic elements must be correct. A wrong semantic element is worse than a `<div>`. If no element fits, use `<div>` or `<span>`.

## 1.9 Exercises

1. List 5 reasons that a screen reader user prefers `<nav>` to `<div class="menu">`.
2. Rewrite this with semantic elements:
   ```html
   <div class="header"><div class="title">Shop</div></div>
   <div class="main"><div class="item">Shoes</div></div>
   <div class="footer">Contact us</div>
   ```
3. Find 3 `<div>` elements in a real website that must be semantic elements.
4. Explain "First rule of ARIA" in your own words.
5. **Advanced:** Use DevTools > Accessibility. Compare the accessibility tree of a semantic page and a div-only page.

## 1.10 Check your understanding
- What does "semantic" mean?
- Give 3 benefits of semantic HTML.
- What is a landmark?
- When must you use `<div>`?

---

# Lesson 2: Page Structure Elements

## 2.1 Learning objectives
After this lesson, you can:
- Use `<header>`, `<main>`, `<footer>`, `<section>`, `<article>`, and `<aside>`.
- Tell `<section>` from `<article>` from `<div>`.
- Explain how these elements map to landmarks.

## 2.2 The basic page layout

```
┌──────────────────────────────────────┐
│ <header>   (logo, title)             │
│   <nav>    (main menu)               │
├──────────────────────────┬───────────┤
│ <main>                   │ <aside>   │
│   <article>              │ (related  │
│   <article>              │  links)   │
│                          │           │
├──────────────────────────┴───────────┤
│ <footer>   (copyright, links)        │
└──────────────────────────────────────┘
```

```html
<body>
  <header>...</header>
  <nav>...</nav>
  <main>
    <article>...</article>
    <aside>...</aside>
  </main>
  <footer>...</footer>
</body>
```

## 2.3 `<header>`

`<header>` is the **introductory content** of its nearest parent. It can hold a logo, a title, a menu, and a search form.

```html
<header>
  <a href="/"><img src="logo.svg" alt="Acme home" width="120" height="40" /></a>
  <nav aria-label="Main">...</nav>
</header>
```

- A page can have **many** `<header>` elements. One per `<body>`, and one per `<article>` or `<section>`.
- A `<header>` that is a child of `<body>` is the **banner** landmark. A `<header>` inside `<article>` or `<section>` is **not** a landmark.
- `<header>` is not the same as `<head>` (the metadata container).
- `<header>` does not make a heading. It holds headings.

```html
<article>
  <header>
    <h2>Post title</h2>
    <p>By Ali, <time datetime="2026-05-01">1 May 2026</time></p>
  </header>
  <p>Text of the post.</p>
</article>
```

## 2.4 `<main>`

`<main>` holds the **main content** of the page. This is the content that is unique to this page. It does not include repeated content such as the menu, the logo, or the footer.

```html
<main>
  <h1>Welcome</h1>
  <p>...</p>
</main>
```

**Rules:**
1. Use **only one visible** `<main>` in a page.
2. Do not put `<main>` inside `<header>`, `<footer>`, `<nav>`, `<aside>`, or `<article>`.
3. `<main>` is the **main** landmark. A user of a screen reader can jump to it.
4. A "skip link" at the top of the page can link to it: `<a href="#main">Skip to main content</a>` with `<main id="main">`.

## 2.5 `<footer>`

`<footer>` holds the **closing content** of its nearest parent: author, copyright, links, and related documents.

```html
<footer>
  <p><small>&copy; 2026 Acme Company</small></p>
  <nav aria-label="Footer">
    <ul>
      <li><a href="/privacy">Privacy</a></li>
      <li><a href="/terms">Terms</a></li>
    </ul>
  </nav>
</footer>
```

- A page can have many `<footer>` elements. One per `<body>`, and one per `<article>` or `<section>`.
- A `<footer>` that is a child of `<body>` is the **contentinfo** landmark.
- A footer does not need to be at the bottom of the screen. It must be the **last** content of its parent.

## 2.6 `<article>`

`<article>` is a **self-contained** piece of content. It makes sense **alone**, if you copy it to a different place (for example in a news feed).

**Examples:** A blog post, a news story, a forum post, a product card, a comment, a widget.

```html
<article>
  <h2>How I learned HTML</h2>
  <p>It took me three weeks.</p>
</article>
```

**Test:** *"Can I put this in an RSS feed or share it alone, and does it still make sense?"* If yes, use `<article>`.

- Articles can be **nested**. Comments (`<article>`) inside a blog post (`<article>`) is correct.
- Each `<article>` should have a heading.

## 2.7 `<section>`

`<section>` is a **themed group** of content, usually with a heading. It is part of a bigger whole.

```html
<section>
  <h2>Features</h2>
  <p>...</p>
</section>
<section>
  <h2>Pricing</h2>
  <p>...</p>
</section>
```

**Rules:**
1. A `<section>` should have a **heading** (`<h1>` to `<h6>`).
2. If you cannot write a heading for it, use `<div>`.
3. Do not use `<section>` only for styling. Use `<div>` for that.
4. A `<section>` becomes a **region** landmark only if it has an accessible name (for example `aria-labelledby` that points to its heading).

```html
<section aria-labelledby="features-title">
  <h2 id="features-title">Features</h2>
  ...
</section>
```

## 2.8 `<aside>`

`<aside>` holds content that is **related, but separate** from the main content. It can be removed and the main content still makes sense.

**Examples:** A sidebar, a pull quote, a "related articles" list, an advertisement, a glossary box, author information.

```html
<aside aria-labelledby="related-title">
  <h2 id="related-title">Related articles</h2>
  <ul>
    <li><a href="/css-basics">CSS basics</a></li>
    <li><a href="/js-intro">JavaScript intro</a></li>
  </ul>
</aside>
```

- `<aside>` is the **complementary** landmark.
- It can be inside an `<article>` (for a note about that article) or outside `<main>` (for page-level information).

## 2.9 `<nav>` (a reminder)

`<nav>` holds **major navigation links**: the main menu, a table of contents, breadcrumbs, and pagination (Module 03).

## 2.10 Summary: how each element maps to a landmark

| Element | Landmark role | Condition |
|---------|---------------|-----------|
| `<header>` | `banner` | Only when it is a child of `<body>` |
| `<nav>` | `navigation` | Always |
| `<main>` | `main` | Always |
| `<aside>` | `complementary` | Always |
| `<footer>` | `contentinfo` | Only when it is a child of `<body>` |
| `<section>` | `region` | Only with an accessible name |
| `<form>` | `form` | Only with an accessible name |
| `<search>` | `search` | Always |
| `<article>` | `article` | Not a landmark (role only) |

## 2.11 Which element to choose?

```
Is it navigation links?                 → <nav>
Is it the main content of the page?     → <main>
Is it the intro of a page or section?   → <header>
Is it the closing part of a page/section? → <footer>
Can it stand alone (copyable)?          → <article>
Is it a themed group with a heading?    → <section>
Is it related, but not main?            → <aside>
None of the above?                      → <div>
```

## 2.12 Example: a full page

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Learn HTML | Acme Blog</title>
  </head>
  <body>
    <a href="#main" class="skip-link">Skip to main content</a>

    <header>
      <p><a href="/">Acme Blog</a></p>
      <nav aria-label="Main">
        <ul>
          <li><a href="/" aria-current="page">Home</a></li>
          <li><a href="/about">About</a></li>
        </ul>
      </nav>
    </header>

    <main id="main">
      <h1>Learn HTML</h1>

      <article>
        <header>
          <h2>Step 1: Structure</h2>
          <p>Posted <time datetime="2026-05-01">1 May 2026</time></p>
        </header>
        <p>Start with the document structure.</p>
        <footer><p>Filed under: Basics</p></footer>
      </article>

      <aside aria-labelledby="tips-title">
        <h2 id="tips-title">Tip</h2>
        <p>Always write a doctype.</p>
      </aside>
    </main>

    <footer>
      <p><small>&copy; 2026 Acme</small></p>
    </footer>
  </body>
</html>
```

## 2.13 Try It

1. Make a page with `<header>`, `<nav>`, `<main>`, `<aside>`, and `<footer>`.
2. Put two `<article>` elements in `<main>`. Give each a `<header>` and a `<footer>`.
3. Add a `<section>` with a heading.
4. Add CSS to make a two-column layout (`main` and `aside`) with Flexbox or Grid.
5. Open DevTools > Accessibility. Find the landmarks. Check that each one is in the tree.

## 2.14 Advanced Note

- **Why not `<section>` for everything?** A `<section>` with no heading and no name has the role `generic`. It gives no value. Accessibility experts say: use `<section>` only when it has a clear heading.
- **`<article>` vs `<section>`:** An `<article>` can stand alone. A `<section>` cannot. A blog page can be an `<article>` with `<section>` elements inside it.
- **`<main>` and SPAs:** In single-page apps, keep one `<main>`. Move focus to the new `<h1>` (or `<main>`) when the view changes.
- **Multiple `<main>`:** HTML5.2 allows many `<main>` if all but one have `hidden`. Use this only for tabbed views in apps.
- **`<header>` and `<footer>` scoping:** The rule is that these elements are **not** landmarks when they are inside `<article>`, `<aside>`, `<main>`, `<nav>`, or `<section>`. Browsers apply this in the accessibility tree.
- **Landmark labels:** If you have more than one landmark of the same type (for example 2 `<nav>`), give each a unique name with `aria-label` or `aria-labelledby`.
- **Too many landmarks:** Do not put every part in a landmark. A page with 3 to 7 landmarks is easy to use.
- **`<search>` element:** The new `<search>` element wraps a search form. It maps to the `search` landmark. Before this, developers used `<form role="search">`.
- **`<hgroup>`:** Use it to group a heading with its subtitle.
- **`<address>` and `<time>`:** See Lesson 4.
- **Microformats / Microdata:** Add `itemscope itemtype="https://schema.org/Article"` to an `<article>` for machine-readable data. JSON-LD is more common (Module 09).
- **Testing landmarks:** Use the "HeadingsMap" or "Landmarks" browser extensions, or a screen reader's landmark list (NVDA: `D` key; VoiceOver rotor).
- **CSS layout:** Style semantic elements directly: `body > header`, `main`, `main > article`. Do not add a class when the element name is enough.

## 2.15 Exercises

1. Choose the best element for each: (a) the site logo and menu, (b) a news story, (c) the "Related links" box, (d) the copyright line, (e) the main text of the page, (f) a group of "Pricing" content with a heading.
2. Write the HTML of a page with a header, a nav, a main with 2 articles, an aside, and a footer.
3. Find the error:
   ```html
   <header>
     <main>...</main>
   </header>
   ```
4. Find the problem: `<section><p>Some text</p></section>` (no heading).
5. **Advanced:** Use a screen reader. List the landmarks of your page. Add `aria-label` to any duplicate landmark types.

## 2.16 Check your understanding
- What is the difference between `<article>` and `<section>`?
- How many `<main>` elements can a page have?
- When is `<header>` the banner landmark?
- What is `<aside>` for?

---

# Lesson 3: `<div>` and `<span>` vs Semantic Tags

## 3.1 Learning objectives
After this lesson, you can:
- Explain what `<div>` and `<span>` are for.
- Decide when to use them.
- Replace `<div>` and `<span>` with semantic elements.

## 3.2 `<div>` and `<span>`

| Element | Type | Meaning |
|---------|------|---------|
| `<div>` | Block | **No meaning.** A generic container. |
| `<span>` | Inline | **No meaning.** A generic inline container. |

They are **neutral**. They exist so that you can group content for **CSS** or **JavaScript** when no semantic element fits.

```html
<div class="card">
  <h3>Title</h3>
  <p>Text with a <span class="highlight">special word</span>.</p>
</div>
```

## 3.3 When to use `<div>` and `<span>`

Use them when:
1. No semantic element fits the content.
2. You need a wrapper for CSS layout (Grid or Flexbox).
3. You need a hook for JavaScript.

Do not use them when a semantic element exists.

## 3.4 Replace `<div>` and `<span>`

| Instead of... | Use... |
|---------------|--------|
| `<div class="header">` | `<header>` |
| `<div class="nav">` | `<nav>` |
| `<div class="main">` | `<main>` |
| `<div class="footer">` | `<footer>` |
| `<div class="post">` | `<article>` |
| `<div class="sidebar">` | `<aside>` |
| `<div class="section">` (with a heading) | `<section>` |
| `<div class="title">` | `<h1>` to `<h6>` |
| `<div class="button" onclick="...">` | `<button type="button">` |
| `<div class="list"><div class="item">` | `<ul><li>` |
| `<span class="bold">` | `<strong>` |
| `<span class="italic">` | `<em>` |
| `<span class="date">` | `<time>` |
| `<span class="code">` | `<code>` |
| `<div class="quote">` | `<blockquote>` |
| `<div class="image-box">` (image + caption) | `<figure>` + `<figcaption>` |
| `<div class="address">` | `<address>` |
| `<div class="accordion">` | `<details>` + `<summary>` |

## 3.5 Why not a `<div>` button?

```html
<!-- Bad -->
<div class="btn" onclick="save()">Save</div>

<!-- Good -->
<button type="button" onclick="save()">Save</button>
```

The `<div>` has:
- No keyboard focus (`Tab`).
- No `Enter` or `Space` activation.
- No button role for screen readers.
- No `disabled` state.

To fix a `<div>` button, you must add `role="button"`, `tabindex="0"`, key handlers, and focus styles. A `<button>` gives all of this for free.

## 3.6 "Divitis" and "classitis"

- **Divitis:** Too many nested `<div>` elements, with no purpose.
- **Classitis:** A class on every element.

```html
<!-- Bad -->
<div class="wrapper">
  <div class="inner">
    <div class="box">
      <div class="text">Hello</div>
    </div>
  </div>
</div>

<!-- Good -->
<p class="box">Hello</p>
```

**Rule:** Add an element only if it has a purpose (meaning or layout).

## 3.7 Good uses of `<div>`

```html
<!-- Layout wrapper for CSS Grid -->
<div class="gallery-grid">
  <figure>...</figure>
  <figure>...</figure>
</div>

<!-- Scroll container for a wide table -->
<div class="table-wrap" tabindex="0" role="region" aria-labelledby="cap1">
  <table>...</table>
</div>

<!-- Group for styling -->
<div class="form-row">
  <label for="a">A</label>
  <input id="a" />
</div>
```

## 3.8 Good uses of `<span>`

```html
<p>Price: <span class="price">$25</span></p>
<p>This word is in <span lang="fr">français</span>.</p>
<button type="button">
  <span class="icon" aria-hidden="true">🔍</span>
  <span>Search</span>
</button>
```

## 3.9 Try It

1. Take this "div soup" and rewrite it with semantic elements:
   ```html
   <div class="page">
     <div class="top"><div class="site-name">My Site</div>
       <div class="links"><a href="/">Home</a><a href="/blog">Blog</a></div></div>
     <div class="content">
       <div class="post"><div class="post-title">Hello</div><div class="post-body">Text.</div></div>
     </div>
     <div class="bottom">Copyright</div>
   </div>
   ```
2. Replace a `<div onclick>` button with a real `<button>`. Compare the keyboard behavior.
3. Count the `<div>` elements in one of your earlier projects. Replace as many as you can.

## 3.10 Advanced Note

- **Generic role:** In the accessibility tree, `<div>` and `<span>` have the role `generic`. Most screen readers ignore them. This is correct behavior.
- **ARIA does not replace semantics.** `<div role="button">` needs extra JavaScript. A native `<button>` is better.
- **`<div>` inside `<p>`:** Not allowed. The parser closes the `<p>`. Use `<span>` inside `<p>`.
- **`display: contents`:** A CSS value that removes the box of an element, but keeps its children. In the past it removed accessibility semantics from buttons and lists in some browsers. Test before use.
- **Custom elements:** `<my-card>` is also generic. Use a custom element only with a good reason. It does not give meaning.
- **BEM and class names:** Use class names that describe the **role** (`card`, `price`), not the **look** (`red-text`, `left-box`).
- **Utility CSS frameworks (like Tailwind):** They use many classes. Keep semantic elements. The HTML element is for meaning, the classes are for style.
- **Performance:** A big DOM (thousands of nodes) is slower. Avoid useless wrappers. Lighthouse warns when the DOM is larger than about 1500 nodes.
- **CSS Grid subgrid and layout:** Modern CSS needs fewer wrapper `<div>` elements than old float and table layouts.
- **Linting:** Tools such as `eslint-plugin-jsx-a11y` and `axe` find a `<div onclick>` with no role.

## 3.11 Exercises

1. Replace the `<div>` or `<span>` with a better element: (a) `<span class="bold">Warning</span>`, (b) `<div class="menu-item">`, (c) `<div class="date">12 May</div>`.
2. Write a `<div>` that you need for layout only, with a short reason.
3. List 3 things that `<button>` does that `<div onclick>` does not do.
4. Rewrite the 4-level nested `<div>` example with one element.
5. **Advanced:** Make a `<div>` that works like a button with `role`, `tabindex`, and keyboard events. Compare the code size to a `<button>`.

## 3.12 Check your understanding
- What is the meaning of `<div>`?
- Give two good uses of `<div>`.
- Why is `<div onclick>` bad?
- What is "divitis"?

---

# Lesson 4: `<details>`, `<summary>`, `<dialog>`, `<time>`, and `<address>`

## 4.1 Learning objectives
After this lesson, you can:
- Build an accordion with `<details>` and `<summary>`.
- Open and close a `<dialog>`.
- Mark dates and times with `<time>`.
- Mark contact information with `<address>`.

## 4.2 `<details>` and `<summary>`

`<details>` makes a **disclosure widget**. The user clicks the summary to show or hide more content. No JavaScript is needed.

```html
<details>
  <summary>What is HTML?</summary>
  <p>HTML is the language for the structure of web pages.</p>
</details>
```

| Part | Job |
|------|-----|
| `<details>` | The container. |
| `<summary>` | The visible label. It must be the **first child**. |
| Other content | Hidden until the user opens it. |
| `open` attribute | Makes it open at the start. |

```html
<details open>
  <summary>Shipping information</summary>
  <p>We ship in 2 to 3 days.</p>
</details>
```

### Exclusive accordion (the `name` attribute)

Give many `<details>` the **same `name`**. Only one can be open at one time.

```html
<details name="faq">
  <summary>Question 1</summary>
  <p>Answer 1.</p>
</details>
<details name="faq">
  <summary>Question 2</summary>
  <p>Answer 2.</p>
</details>
```

### Good practice
- Keep the summary text **short and clear**.
- Do not put headings or buttons inside `<summary>`. A heading inside `<summary>` is allowed, but it can remove the button meaning for some screen readers.
- Use it for FAQs, extra details, and transcripts.
- Do not use it for main navigation menus (use `<nav>` with lists and, if necessary, buttons with `aria-expanded`).

## 4.3 `<dialog>`

`<dialog>` is a **dialog box** or a **modal**. The browser handles focus, the Escape key, and the backdrop.

```html
<dialog id="confirm-dialog">
  <h2>Delete this file?</h2>
  <p>You cannot undo this action.</p>
  <form method="dialog">
    <button value="cancel">Cancel</button>
    <button value="delete">Delete</button>
  </form>
</dialog>

<button type="button" id="open-btn">Delete file</button>
```

```js
const dialog = document.getElementById('confirm-dialog');
const openBtn = document.getElementById('open-btn');

openBtn.addEventListener('click', () => dialog.showModal());

dialog.addEventListener('close', () => {
  console.log('User chose:', dialog.returnValue); // "cancel" or "delete"
});
```

| Method / attribute | Job |
|--------------------|-----|
| `dialog.showModal()` | Opens as a **modal**. The rest of the page is inert. Focus goes into the dialog. `Esc` closes it. |
| `dialog.show()` | Opens as a **non-modal** dialog. |
| `dialog.close(value)` | Closes the dialog. Sets `returnValue`. |
| `open` attribute | The dialog is open. Do not set it by hand for modals. |
| `<form method="dialog">` | A submit button closes the dialog and sets `returnValue` to the button `value`. No server is used. |
| `::backdrop` | CSS pseudo-element for the layer behind a modal. |

```css
dialog::backdrop { background: rgb(0 0 0 / 0.5); }
dialog { border: 0; border-radius: 0.5rem; padding: 1.5rem; max-width: 30rem; }
```

### Good practice
- Always give the dialog a **heading** and a way to close it.
- Use `aria-labelledby="heading-id"` to name the dialog if it is complex.
- Put `autofocus` on the safest button (for example Cancel) for destructive actions.
- Do not use `alert()` and `confirm()` for design. Use `<dialog>`.

## 4.4 `<time>`

`<time>` marks a **date**, a **time**, or a **duration** in a form that a machine can read.

```html
<p>Published on <time datetime="2026-05-01">1 May 2026</time>.</p>
<p>The event starts at <time datetime="18:30">6:30 pm</time>.</p>
<p>Updated <time datetime="2026-05-01T18:30:00+05:30">1 May 2026, 6:30 pm IST</time>.</p>
<p>Reading time: <time datetime="PT5M">5 minutes</time>.</p>
```

| `datetime` format | Example | Meaning |
|-------------------|---------|---------|
| Date | `2026-05-01` | 1 May 2026 |
| Month | `2026-05` | May 2026 |
| Year | `2026` | The year 2026 |
| Time | `18:30` | 6:30 pm |
| Date and time | `2026-05-01T18:30` | Date and time (local) |
| With time zone | `2026-05-01T18:30:00+05:30` | Date and time with offset |
| UTC | `2026-05-01T13:00:00Z` | UTC time |
| Duration | `PT1H30M` | 1 hour 30 minutes |

- The text inside can be in any human format. The `datetime` value must be in the machine format.
- If the text is already in a valid machine format, you can omit `datetime`: `<time>2026-05-01</time>`.
- Search engines and calendar tools can use `<time>`.

## 4.5 `<address>`

`<address>` marks the **contact information** for the **author** or **owner** of the nearest `<article>` or of the whole page (`<body>`).

```html
<address>
  Written by <a href="mailto:ali@example.com">Ali Khan</a><br />
  <a href="https://example.com/ali">Website</a><br />
  <a href="tel:+911234567890">+91 123 456 7890</a>
</address>
```

**Rules:**
- Use it for **contact information** (email, phone, social links, a postal address of the person or the organization).
- Do **not** use it for any postal address. For example, an address of a shop that you list in a store directory is **not** a contact for the author. Use a `<p>` with `<br>`.
- Do not put other types of content inside, such as dates or headings.
- It often goes inside `<footer>` of the page or of an `<article>`.

## 4.6 Try It

1. Make an FAQ with 4 `<details>` elements. Use the same `name` to make an exclusive accordion.
2. Style the `<summary>` with CSS (`cursor: pointer`).
3. Make a `<dialog>` with a "Delete" and "Cancel" button. Open it with JavaScript. Close it with the `Esc` key and with the buttons.
4. Add `<time>` elements to a post with the date and the reading time.
5. Add an `<address>` in the footer with an email and a social link.
6. Use only the keyboard to open `<details>` (`Enter` or `Space`) and the dialog.

## 4.7 Advanced Note

- **`<details>` events:** The `toggle` event fires when it opens or closes. `details.open` is a boolean property. For exclusive groups with the `name` attribute, support is in all modern browsers.
- **Find in page:** In Chromium, text inside a closed `<details>` can be found with "Find in page", and the details open. The attribute `hidden="until-found"` gives the same effect for other elements.
- **Style the marker:** Use `summary::marker` or `summary { list-style: none; }` and `summary::-webkit-details-marker { display: none; }`. Add your own icon with `::before`. Keep the pointer cursor and a visible focus style.
- **Animate `<details>`:** Newer CSS (`::details-content`, `interpolate-size`) allows animation. Older methods used JavaScript.
- **Accessibility of `<details>`:** Screen readers announce "collapsed" or "expanded". This is built in. Do not add `aria-expanded`.
- **`<dialog>` and `inert`:** `showModal()` makes the rest of the page **inert** (not focusable or clickable) and puts the dialog in the **top layer**, above all `z-index` values.
- **`<dialog>` `closedby` and `popover`:** The `closedby` attribute (new) controls light dismiss. The `popover` attribute makes lightweight overlays (menus, tooltips) that need no JavaScript. They are different from a modal dialog.
- **Dialog focus return:** When a modal closes, the browser returns focus to the element that opened it. Check this in your tests.
- **Dialog and forms:** A `<form method="dialog">` does not send data. Use `dialog.returnValue` or a normal form with `method="post"` if you need to send data.
- **`<dialog>` roles:** `<dialog>` has the role `dialog`. For an alert that needs an answer, use `role="alertdialog"`.
- **Dates and time zones:** `<time>` does not show the date in the user's language. JavaScript can format it with `Intl.DateTimeFormat` using the `datetime` value.
- **`pubdate`:** An old attribute. It is removed. Do not use it.
- **Schema.org:** Use `itemprop="datePublished"` on `<time>`, or write JSON-LD (Module 09).
- **`<address>` scope:** The nearest `<article>` ancestor sets the scope. If none, the `<body>` is the scope.

## 4.8 Exercises

1. Write an FAQ with 3 questions in an exclusive accordion.
2. Write a confirmation `<dialog>` with a form that uses `method="dialog"`. Show `returnValue` in the console.
3. Write the `<time>` elements for: (a) 14 February 2026, (b) 9:15 am, (c) 2 hours 30 minutes.
4. Write an `<address>` for the author of an article with an email and a Mastodon or GitHub link.
5. Find the problem: `<address>12 Market Road, Delhi: our shop</address>` in a "Store locator" list.
6. **Advanced:** Write JavaScript that reads the `datetime` of all `<time>` elements and shows each in the user's locale with `Intl.DateTimeFormat`.

## 4.9 Check your understanding
- Where must `<summary>` be in `<details>`?
- What does `showModal()` do that `show()` does not?
- Why does `<time>` have a `datetime` attribute?
- What is `<address>` for?

---

# Lesson 5: Document Outline and Heading Hierarchy

## 5.1 Learning objectives
After this lesson, you can:
- Build a correct heading hierarchy.
- Explain the document outline.
- Test your structure with tools.

## 5.2 What is the document outline?

The **document outline** is the structure of a page as a **tree of headings**. Users of screen readers use it to understand the page and to jump to a section.

```
h1  Learn Web Development
 ├── h2  HTML
 │     ├── h3  Elements
 │     └── h3  Attributes
 ├── h2  CSS
 │     └── h3  Selectors
 └── h2  JavaScript
```

## 5.3 Rules for a correct hierarchy

1. Use **one** `<h1>` that describes the page.
2. Go **down one level at a time**: `<h2>` then `<h3>`. Do not skip (`<h2>` then `<h4>`).
3. You can go **up** any number of levels: after an `<h4>`, an `<h2>` is correct.
4. Choose the level for **structure**, not for size. Use CSS for size.
5. Write headings that describe the content that follows.
6. Do not use a heading only to make text big or bold.
7. Every `<section>`, `<article>`, `<aside>`, and `<nav>` that is a major part should have a heading (it can be hidden visually).

## 5.4 Correct and incorrect

**Correct:**
```html
<h1>Cooking Blog</h1>
  <h2>Recipes</h2>
    <h3>Soups</h3>
    <h3>Salads</h3>
  <h2>Tips</h2>
```

**Incorrect:**
```html
<h1>Cooking Blog</h1>
  <h4>Recipes</h4>      <!-- skipped h2 and h3 -->
<h1>Tips</h1>           <!-- a second h1 -->
  <h3>Soups</h3>        <!-- skipped h2 -->
```

## 5.5 Headings and sectioning elements

HTML5 has a feature called the **outline algorithm**. It says that `<section>` and `<article>` start a new "section" so that you can use `<h1>` in each one.

**Important:** **No browser or screen reader uses this algorithm.** The HTML standard has removed it. You must use **explicit heading levels** (`<h1>` to `<h6>`) that match the real depth.

```html
<main>
  <h1>Learn HTML</h1>

  <section aria-labelledby="s1">
    <h2 id="s1">Basics</h2>
    <article>
      <h3>What is an element?</h3>
      <p>...</p>
    </article>
  </section>

  <section aria-labelledby="s2">
    <h2 id="s2">Advanced</h2>
    ...
  </section>
</main>
```

## 5.6 Headings for the whole page

A page has a heading hierarchy that covers **all** its content, also the content outside `<main>`.

| Part | Heading |
|------|---------|
| Page title | `<h1>` (in `<main>`) |
| Main sections | `<h2>` |
| Sidebar (`<aside>`) | `<h2>` (a section at the same level as the main sections) |
| Footer, with a group of links | `<h2>` (it can be visually hidden) |
| Site name in the header | `<p>` or a link (not a heading), or `<h1>` on the home page, if it is the page title |

## 5.7 Hide a heading visually, but keep it for assistive tools

Use a "visually hidden" class. Do not use `display: none` or `hidden` (they hide the heading from assistive tools also).

```html
<nav aria-labelledby="footer-nav-title">
  <h2 id="footer-nav-title" class="visually-hidden">Footer links</h2>
  <ul>...</ul>
</nav>
```

```css
.visually-hidden {
  position: absolute; width: 1px; height: 1px; overflow: hidden;
  clip: rect(0 0 0 0); white-space: nowrap;
}
```

## 5.8 Subtitles and `<hgroup>`

If a heading has a subtitle or a tagline, group them in `<hgroup>`. Only the heading counts in the outline.

```html
<hgroup>
  <h1>Learn HTML</h1>
  <p>A free course for beginners</p>
</hgroup>
```

## 5.9 Test your outline

| Tool | How to use |
|------|------------|
| **Browser extension** "HeadingsMap" or "Web Developer" | Shows a tree of your headings. |
| **W3C Validator** | Warns about empty headings and some section problems. |
| **Lighthouse** | Checks that headings are in a sequential order. |
| **axe DevTools** | Finds skipped levels and empty headings. |
| **Screen reader** | NVDA: `H` key jumps to the next heading. `Insert + F7` lists all headings. VoiceOver: Rotor > Headings. |
| **DevTools console** | `[...document.querySelectorAll('h1,h2,h3,h4,h5,h6')].map(h => h.tagName + ' ' + h.textContent.trim())` |

## 5.10 Try It

1. Run the console command from the table on a news website. Read the outline. Is it correct?
2. Write the outline of a page about your city: 1 `<h1>`, 3 `<h2>`, and 2 `<h3>` under each.
3. Add the headings to a page. Add a visually hidden heading to a footer navigation.
4. Install a headings extension. Check your page.
5. Break the outline on purpose (skip a level). See how the tool reports it.

## 5.11 Advanced Note

- **History:** The HTML5 outline algorithm was never implemented in browsers. It was removed from the standard in 2022. Older tutorials still teach it. Do not follow them.
- **`<h1>` count:** HTML does not forbid many `<h1>`. But the best practice is one `<h1>` per page. Accessibility tools (WebAIM, Deque) advise this.
- **Headings in components:** In reusable components (for example a card), the heading level depends on where you put the component. Let the component accept a heading level as a parameter (`<h2>` or `<h3>`), or use `role="heading" aria-level="3"` only as a last resort.
- **`aria-level`:** `<div role="heading" aria-level="2">` can set the level, but a native `<h2>` is better.
- **Empty headings:** An empty `<h2></h2>` is a problem for screen readers. Remove it or add text.
- **Headings in buttons/links:** `<h2><a href="...">Title</a></h2>` is correct. `<a><h2>Title</h2></a>` is valid in HTML5 but can be noisy.
- **Heading text in images:** If a heading is an image, the `alt` text is the heading text.
- **SEO:** Search engines use headings to understand the topic. Use the main keywords in a natural way. Do not stuff keywords.
- **Table of contents:** Generate it from the headings with JavaScript. Use `id` on each heading for links. Add `scroll-margin-top` for a fixed header.
- **Skip heading links:** A "link to this heading" anchor is a common pattern in documentation. Make sure its name is clear ("Link to: Section title").
- **WCAG:** 1.3.1 (structure in code), 2.4.6 (headings and labels describe the topic), 2.4.10 (section headings, level AAA).
- **Landmarks and headings together:** Use landmarks for the big areas. Use headings for the content structure inside. They are two different navigation tools.

## 5.12 Exercises

1. Fix the outline:
   ```html
   <h1>Pets</h1>
   <h3>Dogs</h3>
   <h3>Cats</h3>
   <h1>Care</h1>
   <h5>Food</h5>
   ```
2. Write the outline for a recipe page: title, ingredients, steps, notes, and related recipes in a sidebar.
3. Add a visually hidden `<h2>` for a sidebar that has only links.
4. Write a JavaScript function that logs the outline as an indented tree.
5. **Advanced:** Write a script that builds a table of contents from the `<h2>` and `<h3>` elements of the page, with links.

## 5.13 Check your understanding
- How many `<h1>` should a page have?
- Can you skip from `<h2>` to `<h4>`?
- Does a browser use the HTML5 outline algorithm?
- How do you hide a heading visually, but keep it for screen readers?

---

# Lesson 6: Module Project - Blog Article Layout

## 6.1 Project goal
Build a **blog article page**. Use semantic elements, a correct heading hierarchy, and the new elements from this module. The page must be easy to use with a screen reader.

## 6.2 Page plan

```
┌───────────────────────────────────────────┐
│ Skip link                                 │
│ <header>  site name + <nav>               │
├─────────────────────────────┬─────────────┤
│ <main>                      │ <aside>     │
│  <article>                  │  About the  │
│    <header> title, author,  │  author     │
│      <time>                 │             │
│    intro                    │  Related    │
│    <section> parts          │  posts      │
│    <figure>                 │             │
│    <details> FAQ            │             │
│    <footer> tags, address   │             │
│  </article>                 │             │
│  <section> comments         │             │
│    <article> comment...     │             │
├─────────────────────────────┴─────────────┤
│ <footer> links, copyright                 │
└───────────────────────────────────────────┘
```

## 6.3 Required content

| Part | Content | Elements |
|------|---------|----------|
| Skip link | Link to main content | `<a href="#main">` |
| Site header | Site name and menu | `<header>`, `<nav>` |
| Article header | Title, subtitle, author, date, reading time | `<header>`, `<hgroup>`, `<h1>`, `<time>` |
| Intro | A short introduction | `<p>` |
| Sections | At least 3 sections with headings | `<section>`, `<h2>`, `<h3>` |
| Media | One image with a caption | `<figure>`, `<figcaption>` |
| Quote | One quote with a source | `<blockquote>`, `<cite>` |
| FAQ | At least 3 questions | `<details>`, `<summary>` |
| Table of contents | Links to the sections | `<nav aria-label="Table of contents">`, `<ol>` |
| Article footer | Tags and the author contact | `<footer>`, `<address>` |
| Sidebar | Author bio and related posts | `<aside>` |
| Comments | At least 2 comments | `<section>`, nested `<article>`, `<time>` |
| Dialog | A "Share" dialog | `<dialog>` |
| Page footer | Navigation links and copyright | `<footer>`, `<nav>` |

## 6.4 Project folder

```
project/
├── index.html
├── style.css
├── script.js          (for the dialog; keep it small)
├── images/
│   └── article-photo.jpg
└── README.md
```

## 6.5 Requirements

### Level 1: Beginner (required)
- [ ] Full HTML boilerplate with `lang`, and a clear `<title>`.
- [ ] One `<header>`, one `<nav>`, one `<main>`, one `<footer>` at page level.
- [ ] One `<article>` with its own `<header>` and `<footer>`.
- [ ] One `<aside>`.
- [ ] At least 3 `<section>` elements, each with a heading.
- [ ] A correct heading hierarchy. One `<h1>`. No skipped levels.
- [ ] At least one `<time>` with a correct `datetime`.
- [ ] One `<address>` with contact information of the author.
- [ ] One `<figure>` with `<figcaption>`, and an image with good `alt` text.
- [ ] At least 3 `<details>` elements (FAQ).
- [ ] No `<div>` or `<span>` where a semantic element exists.
- [ ] Each landmark type that appears twice has a unique `aria-label`.
- [ ] Use CSS to make a two-column layout (`main` and `aside`) that becomes one column on a narrow screen.

### Level 2: Intermediate (recommended)
- [ ] A skip link that works with the keyboard and is visible on focus.
- [ ] A table of contents with `<nav>` and links to the section IDs.
- [ ] A comments section with nested `<article>` elements, each with a `<time>`.
- [ ] A `<dialog>` "Share" with `<form method="dialog">`, opened with `showModal()`.
- [ ] Exclusive FAQ with the `name` attribute on `<details>`.
- [ ] `aria-labelledby` on each `<section>` that is a landmark.
- [ ] Validate the page with `https://validator.w3.org`. Fix all errors.
- [ ] Check the outline with a headings extension or the console command.

### Level 3: Advanced (optional)
- [ ] Add JSON-LD structured data (`@type: BlogPosting`) in `<head>`.
- [ ] Add a visually hidden heading to each region that has no visible heading.
- [ ] Format dates in the user's locale with `Intl.DateTimeFormat`.
- [ ] Add print CSS that hides the navigation, the sidebar, and the dialog.
- [ ] Test the page with a screen reader (NVDA or VoiceOver). List landmarks and headings. Write a short report in `README.md`.
- [ ] Get a Lighthouse score of 100 for Accessibility and SEO.
- [ ] Add `prefers-reduced-motion` and `prefers-color-scheme` support in CSS.

## 6.6 Steps

1. Choose a topic for the article (for example, "5 tips for new web developers").
2. Write the **outline** first: the `<h1>`, the `<h2>` sections, and the FAQ questions.
3. Draw the page layout. Mark each region with the semantic element that you will use.
4. Write the HTML. Start with the page structure (`header`, `main`, `aside`, `footer`) with no content.
5. Add the article structure. Add content one part at a time.
6. Add the sidebar, comments, and dialog.
7. Add the CSS. Start with mobile (one column). Add the two-column layout for wide screens.
8. Test with the keyboard only. Test with the console command for the outline.
9. Validate. Run Lighthouse. Check the landmarks in DevTools > Accessibility.
10. Write `README.md`: the topic, the outline, and what you tested.
11. Commit and push:
    ```bash
    git add .
    git commit -m "Add Module 07 semantic blog article layout"
    git push
    ```

## 6.7 Starter template

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>5 Tips for New Web Developers | Acme Blog</title>
    <meta name="description" content="Five practical tips for people who start to learn web development." />
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <a class="skip-link" href="#main">Skip to main content</a>

    <header class="site-header">
      <p class="site-name"><a href="index.html">Acme Blog</a></p>
      <nav aria-label="Main">
        <ul>
          <li><a href="index.html" aria-current="page">Home</a></li>
          <li><a href="#">Articles</a></li>
          <li><a href="#">About</a></li>
        </ul>
      </nav>
    </header>

    <div class="layout">
      <main id="main">
        <article>
          <header>
            <hgroup>
              <h1>5 Tips for New Web Developers</h1>
              <p>Start well, and avoid common mistakes</p>
            </hgroup>
            <p>
              By <a href="#author">Ali Khan</a> |
              Published <time datetime="2026-05-01">1 May 2026</time> |
              Reading time <time datetime="PT6M">6 minutes</time>
            </p>
          </header>

          <p>Short introduction to the article.</p>

          <nav aria-label="Table of contents">
            <h2>Contents</h2>
            <ol>
              <li><a href="#tip-1">Learn the basics first</a></li>
              <li><a href="#tip-2">Build small projects</a></li>
              <li><a href="#tip-3">Use semantic HTML</a></li>
            </ol>
          </nav>

          <section aria-labelledby="tip-1">
            <h2 id="tip-1">Learn the basics first</h2>
            <p>...</p>
            <figure>
              <img src="images/article-photo.jpg" alt="A laptop with code on the screen next to a notebook" width="800" height="533" />
              <figcaption>Write code every day, even for 20 minutes.</figcaption>
            </figure>
          </section>

          <section aria-labelledby="tip-2">
            <h2 id="tip-2">Build small projects</h2>
            <p>...</p>
            <blockquote cite="https://example.com/source">
              <p>The best way to learn is to build something.</p>
            </blockquote>
            <p>Source: <cite>A Book About Learning</cite></p>
          </section>

          <section aria-labelledby="tip-3">
            <h2 id="tip-3">Use semantic HTML</h2>
            <p>...</p>
          </section>

          <section aria-labelledby="faq-title">
            <h2 id="faq-title">Questions and answers</h2>
            <details name="faq">
              <summary>How long does it take to learn HTML?</summary>
              <p>Most people learn the basics in 2 to 4 weeks.</p>
            </details>
            <details name="faq">
              <summary>Do I need to know CSS first?</summary>
              <p>No. Learn HTML first, then CSS.</p>
            </details>
            <details name="faq">
              <summary>Which editor is best?</summary>
              <p>VS Code is a good free choice.</p>
            </details>
          </section>

          <footer>
            <p>Tags: <a href="#">HTML</a>, <a href="#">Beginners</a></p>
            <address>
              Contact the author:
              <a href="mailto:ali@example.com">ali@example.com</a>
            </address>
            <button type="button" id="share-btn">Share this article</button>
          </footer>
        </article>

        <section aria-labelledby="comments-title">
          <h2 id="comments-title">Comments</h2>
          <article>
            <header>
              <h3>Sara</h3>
              <p><time datetime="2026-05-02T09:15">2 May 2026, 9:15 am</time></p>
            </header>
            <p>Great tips. Thank you!</p>
          </article>
          <!-- Add another comment -->
        </section>
      </main>

      <aside aria-labelledby="author">
        <section>
          <h2 id="author">About the author</h2>
          <p>Ali Khan is a web developer and teacher.</p>
        </section>
        <section aria-labelledby="related-title">
          <h2 id="related-title">Related articles</h2>
          <ul>
            <li><a href="#">CSS for beginners</a></li>
            <li><a href="#">First steps with Git</a></li>
          </ul>
        </section>
      </aside>
    </div>

    <footer class="site-footer">
      <nav aria-label="Footer">
        <ul>
          <li><a href="#">Privacy</a></li>
          <li><a href="#">Terms</a></li>
        </ul>
      </nav>
      <p><small>&copy; 2026 Acme Blog</small></p>
    </footer>

    <dialog id="share-dialog" aria-labelledby="share-title">
      <h2 id="share-title">Share this article</h2>
      <p><a href="#">Copy link</a></p>
      <form method="dialog">
        <button value="close" autofocus>Close</button>
      </form>
    </dialog>

    <script src="script.js"></script>
  </body>
</html>
```

## 6.8 Starter JavaScript (`script.js`)

```js
const dialog = document.getElementById('share-dialog');
const openBtn = document.getElementById('share-btn');

openBtn.addEventListener('click', () => dialog.showModal());
```

## 6.9 Starter CSS (`style.css`)

```css
:root { --accent: #2563eb; --text: #111827; --bg: #ffffff; --muted: #4b5563; }
* { box-sizing: border-box; }
body { margin: 0; font-family: system-ui, sans-serif; line-height: 1.6; color: var(--text); background: var(--bg); }
a { color: var(--accent); }
img { max-width: 100%; height: auto; }

.skip-link {
  position: absolute; left: 1rem; top: -4rem;
  background: #000; color: #fff; padding: 0.5rem 1rem; z-index: 10;
}
.skip-link:focus { top: 1rem; }

.site-header, .site-footer { padding: 1rem; background: #f3f4f6; }
.site-header nav ul, .site-footer nav ul { list-style: none; display: flex; gap: 1rem; padding: 0; margin: 0; flex-wrap: wrap; }

.layout { display: grid; gap: 2rem; padding: 1rem; max-width: 70rem; margin: 0 auto; }
@media (min-width: 52rem) {
  .layout { grid-template-columns: minmax(0, 2fr) minmax(0, 1fr); }
}

article > header h1 { margin-bottom: 0.25rem; }
hgroup p { margin: 0; color: var(--muted); }

details { border: 1px solid #d1d5db; border-radius: 0.375rem; padding: 0.5rem 1rem; margin-bottom: 0.5rem; }
summary { cursor: pointer; font-weight: 600; }
summary:focus-visible, a:focus-visible, button:focus-visible { outline: 3px solid var(--accent); outline-offset: 2px; }

blockquote { border-left: 4px solid var(--accent); margin-left: 0; padding-left: 1rem; color: var(--muted); }

dialog { border: 0; border-radius: 0.5rem; padding: 1.5rem; max-width: 28rem; }
dialog::backdrop { background: rgb(0 0 0 / 0.5); }

.visually-hidden {
  position: absolute; width: 1px; height: 1px; overflow: hidden;
  clip: rect(0 0 0 0); white-space: nowrap;
}

@media print {
  .site-header, aside, dialog, #share-btn, .skip-link { display: none; }
}
```

## 6.10 Self-check list

1. Does the page have exactly one `<h1>` and no skipped heading levels?
2. Do `<header>`, `<nav>`, `<main>`, `<aside>`, and `<footer>` exist at page level?
3. Is each `<section>` named by a heading?
4. Does each repeated landmark type have a unique `aria-label` or `aria-labelledby`?
5. Is the `<article>` truly self-contained?
6. Do all `<time>` elements have a correct `datetime`?
7. Is `<address>` used only for contact information?
8. Do you use `<div>` only where no semantic element fits?
9. Can you use the whole page with only the keyboard (skip link, FAQ, dialog)?
10. Does the validator show 0 errors?
11. Does Lighthouse show a score of 90 or more for Accessibility?

## 6.11 Grading guide (self-assessment)

| Area | Points |
|------|--------|
| Correct page structure (`header`, `main`, `footer`, `aside`, `nav`) | 20 |
| Correct `article` and `section` use | 15 |
| Heading hierarchy (outline) | 15 |
| `details`, `dialog`, `time`, `address` | 15 |
| Accessibility (skip link, labels, keyboard) | 15 |
| Responsive CSS layout | 5 |
| Validator shows 0 errors | 5 |
| Git commits and README | 10 |
| **Total** | **100** |

A score of 80 or more means you are ready for Module 08.

---

# Module 07 Review

## Final quiz

**Questions**

1. What does "semantic HTML" mean?
2. Name 3 reasons to use semantic elements.
3. How many visible `<main>` elements can a page have?
4. What is the difference between `<article>` and `<section>`?
5. When is `<header>` a `banner` landmark?
6. What is `<aside>` for?
7. Why is `<button>` better than `<div onclick>`?
8. Where must `<summary>` be in `<details>`?
9. What does `showModal()` do?
10. Does a browser use the HTML5 outline algorithm? What must you do instead?

**Answers**

1. HTML elements are chosen because of the **meaning** of the content, not because of how the content looks.
2. For example: accessibility (landmarks for screen readers), SEO (search engines understand the structure), maintenance (code is easier to read), and built-in behavior (for example `<button>`, `<details>`).
3. One.
4. `<article>` is self-contained and makes sense alone. `<section>` is a themed group of content with a heading, as part of a bigger whole.
5. When it is a direct child of `<body>`. Inside `<article>`, `<section>`, and similar elements, it is not a landmark.
6. For content that is related to the main content, but separate from it (a sidebar, related links, a note, a pull quote).
7. A `<button>` has keyboard focus, `Enter` and `Space` support, the correct role, and a `disabled` state, with no extra code.
8. As the first child.
9. It opens the dialog as a modal: the rest of the page becomes inert, focus goes into the dialog, `Esc` closes it, and a backdrop shows.
10. No. Use explicit heading levels (`<h1>` to `<h6>`) that match the real structure, with no skipped levels.

## Common mistakes

| Mistake | Fix |
|---------|-----|
| "Div soup" | Use semantic elements where they fit. |
| `<section>` with no heading | Add a heading, or use `<div>`. |
| `<section>` only for styling | Use `<div>`. |
| `<article>` for content that cannot stand alone | Use `<section>` or `<div>`. |
| Many visible `<main>` elements | Use one. |
| `<main>` inside `<article>` or `<header>` | Put `<main>` at the page level. |
| `<header>` confused with `<head>` | `<head>` is metadata. `<header>` is visible intro content. |
| `<div onclick>` for buttons | Use `<button type="button">`. |
| Skipped heading levels | Go down one level at a time. |
| Many `<h1>` elements | Use one. |
| Heading level chosen for size | Choose by structure. Style with CSS. |
| Hiding a heading with `display: none` | Use a visually-hidden class. |
| Two `<nav>` elements with no names | Add unique `aria-label` values. |
| `<address>` for any postal address | Use only for contact information of the author or owner. |
| `<time>` without a valid `datetime` | Use a correct machine-readable value. |
| `role="navigation"` on `<nav>` | Remove it. It is redundant. |
| `<details>` with `aria-expanded` | Remove it. It is built in. |
| `alert()` for custom dialogs | Use `<dialog>`. |
| Trusting the HTML5 outline algorithm | Use explicit heading levels. |

## Glossary

| Term | Definition |
|------|------------|
| Accessibility tree | A tree that the browser builds for assistive tools. |
| ARIA | Accessible Rich Internet Applications. Attributes that add meaning for assistive tools. |
| Banner | The landmark role of the page-level `<header>`. |
| Complementary | The landmark role of `<aside>`. |
| Contentinfo | The landmark role of the page-level `<footer>`. |
| Disclosure widget | A control that shows and hides content (`<details>`). |
| Divitis | Too many useless `<div>` elements. |
| Document outline | The tree of headings of a page. |
| Generic | The role of `<div>` and `<span>`: no meaning. |
| Landmark | A page region that assistive tools can find and jump to. |
| Modal | A dialog that blocks the rest of the page. |
| Region | The landmark role of a named `<section>`. |
| Semantic | Related to meaning. |
| Skip link | A link at the top of the page that jumps to the main content. |
| Visually hidden | Text that is hidden on the screen, but available to assistive tools. |

## Module 07 progress checklist (copy to `PROGRESS.md`)

```markdown
## Module 07: Semantic HTML
- [ ] Lesson 1: Why semantics matter
- [ ] Lesson 2: header, main, footer, section, article, aside
- [ ] Lesson 3: div and span vs semantic tags
- [ ] Lesson 4: details, summary, dialog, time, address
- [ ] Lesson 5: Document outline and heading hierarchy
- [ ] Lesson 6: Blog article layout project
- [ ] Final quiz (8/10 or more)
- [ ] Landmarks and outline checked with DevTools or an extension
- [ ] Page validated with W3C
- [ ] Lighthouse accessibility check done
- [ ] Project pushed to GitHub
```

## Cheat sheet: Module 07

```html
<body>
  <a href="#main">Skip to main content</a>

  <header>                      <!-- banner (page level) -->
    <nav aria-label="Main">...</nav>
  </header>

  <main id="main">              <!-- one per page -->
    <h1>Page title</h1>

    <article>                   <!-- self-contained -->
      <header>
        <h2>Title</h2>
        <p><time datetime="2026-05-01">1 May 2026</time></p>
      </header>

      <section aria-labelledby="s1">   <!-- themed group + heading -->
        <h3 id="s1">Part</h3>
        <figure><img src="a.jpg" alt="..." /><figcaption>...</figcaption></figure>
      </section>

      <details name="faq"><summary>Question</summary><p>Answer</p></details>

      <footer>
        <address><a href="mailto:a@b.com">a@b.com</a></address>
      </footer>
    </article>

    <aside aria-labelledby="r">   <!-- related, not main -->
      <h2 id="r">Related</h2>
    </aside>
  </main>

  <footer>                      <!-- contentinfo (page level) -->
    <p><small>&copy; 2026</small></p>
  </footer>

  <dialog id="d"><form method="dialog"><button>Close</button></form></dialog>
</body>
```

| Element | Landmark role | Note |
|---------|---------------|------|
| `<header>` | `banner` | Only as a child of `<body>` |
| `<nav>` | `navigation` | Name each one if more than one |
| `<main>` | `main` | One visible per page |
| `<aside>` | `complementary` | Related content |
| `<footer>` | `contentinfo` | Only as a child of `<body>` |
| `<section>` | `region` | Only with an accessible name |
| `<search>` | `search` | Wraps a search form |

| Question | Element |
|----------|---------|
| Can it stand alone? | `<article>` |
| Is it a themed group with a heading? | `<section>` |
| Is it related, but not main? | `<aside>` |
| Is it a date or time? | `<time datetime="...">` |
| Is it contact info of the author? | `<address>` |
| Is it show/hide content? | `<details>` + `<summary>` |
| Is it a dialog or modal? | `<dialog>` |
| None of these? | `<div>` or `<span>` |

## Next module
Go to **Module 08: Accessibility (a11y)**. You learn WCAG basics, alt text, ARIA, keyboard navigation, skip links, and testing with Lighthouse and screen readers.
