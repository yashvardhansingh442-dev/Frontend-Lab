# Module 03: Links and Navigation

**Folder:** `03-links-navigation/`
**Level:** Beginner (with Advanced notes)
**Time:** 6 to 8 hours
**Writing style:** ASD-STE100 (Simplified Technical English)
**Prerequisites:** Module 01 and Module 02

---

## Module Overview

### Goal
Learn to connect pages with links. Learn file paths. Build a navigation menu. Build a multi-page website.

### What you learn
After this module, you can:
1. Write links with the `<a>` element.
2. Choose between absolute and relative paths.
3. Link to a part of a page with `#id`.
4. Use `target`, `rel`, `download`, `mailto:`, and `tel:`.
5. Build an accessible `<nav>` menu.
6. Build a mini website with many pages.

### The main idea of this module
The word **HyperText** in HTML means text with links. Links make the web a web. A correct link needs two things: a correct **path** and a clear **link text**.

### Folder structure for this module
```
03-links-navigation/
├── lesson-01-anchor-paths.md
├── lesson-02-internal-links.md
├── lesson-03-link-attributes.md
├── lesson-04-nav-menu.md
├── lesson-05-project-mini-site.md
├── examples/
├── exercises/
└── project/
```

---

# Lesson 1: The Anchor Element and Paths

## 1.1 Learning objectives
After this lesson, you can:
- Write a link with `<a href>`.
- Explain absolute and relative paths.
- Use `./`, `../`, and `/` in paths.
- Write clear link text.

## 1.2 The anchor element

The `<a>` element makes a link. `a` means **anchor**.

```html
<a href="https://example.com">Visit Example</a>
```

| Part | Meaning |
|------|---------|
| `<a>` | The anchor element. |
| `href` | **H**ypertext **ref**erence. The address of the destination. |
| `Visit Example` | The link text. The user clicks this text. |

- The browser shows link text in blue and underlined by default.
- The `<a>` element is **inline**. It stays in the line of text.
- An `<a>` element can contain text, images, and other inline content.

```html
<a href="https://example.com">
  <img src="logo.png" alt="Example home page" width="100" />
</a>
```

## 1.3 Absolute paths (full URLs)

An absolute path has the full address. It starts with the scheme (`https://`).

```html
<a href="https://developer.mozilla.org/en-US/docs/Web/HTML">MDN HTML docs</a>
```

**Use absolute paths for:** pages on **other** websites.

## 1.4 Relative paths

A relative path gives the location of a file **from the current file**. It has no scheme and no domain.

**Use relative paths for:** pages on **your own** website.

Use this example folder:

```
my-site/
├── index.html
├── about.html
├── contact/
│   └── form.html
└── images/
    └── photo.jpg
```

### Paths from `index.html`

| Destination | Path |
|-------------|------|
| `about.html` (same folder) | `about.html` or `./about.html` |
| `contact/form.html` (folder below) | `contact/form.html` |
| `images/photo.jpg` | `images/photo.jpg` |

### Paths from `contact/form.html`

| Destination | Path |
|-------------|------|
| `index.html` (one folder up) | `../index.html` |
| `about.html` (one folder up) | `../about.html` |
| `images/photo.jpg` | `../images/photo.jpg` |

### Path symbols

| Symbol | Meaning |
|--------|---------|
| `./` | The current folder. |
| `../` | One folder up. |
| `../../` | Two folders up. |
| `/` at the start | The root of the website (root-relative path). |

```html
<!-- Same folder -->
<a href="about.html">About</a>

<!-- Folder below -->
<a href="contact/form.html">Contact form</a>

<!-- One folder up -->
<a href="../index.html">Home</a>

<!-- Root-relative -->
<a href="/about.html">About</a>
```

## 1.5 Which path type to use

| Situation | Path type |
|-----------|-----------|
| Link to another website | Absolute |
| Link to a page in your site | Relative |
| Site has a fixed domain and you are on a server | Root-relative (`/about.html`) is possible |

**Warning:** A root-relative path (`/about.html`) does not work when you open the file directly from your computer (`file://`). It also does not work on GitHub Pages **project sites**, because the root of the site is `username.github.io/` and not `username.github.io/repo-name/`. For learning, use plain relative paths.

## 1.6 Write clear link text

The link text must tell the user where the link goes.

| Bad | Good |
|-----|------|
| `Click here` | `Read the HTML guide` |
| `Link` | `Download the price list (PDF)` |
| `More` | `More about our team` |
| `https://example.com/page/123` | `Our pricing page` |

**Why:**
- Screen reader users can list all links on a page. "Click here" repeated 10 times is not useful.
- Search engines use link text to understand the destination.
- All users can scan the page faster.

## 1.7 Try It

1. Make a folder `my-site` with the structure in section 1.4. Each HTML file needs the boilerplate.
2. In `index.html`, add links to `about.html` and `contact/form.html`.
3. In `contact/form.html`, add links back to `index.html` and `about.html`.
4. In `about.html`, add a link to an outside website (absolute path).
5. Click all links. Make sure that no link shows a 404 error.

## 1.8 Advanced Note

- **URL resolution:** The browser resolves a relative URL against the **base URL** of the page. You can change it with `<base href="...">`. Do not use `<base>` in simple projects. It changes all relative URLs on the page, also `#` links.
- **Protocol-relative URLs:** `//example.com/page` uses the same scheme as the current page. This is old practice. Use `https://`.
- **Case sensitivity:** Most web servers use case-sensitive paths. `About.html` and `about.html` are different files. Your computer (Windows, macOS) can hide this problem. The error shows only after you publish. Use lowercase file names.
- **Spaces in paths:** A space in a URL becomes `%20`. Avoid spaces. Use hyphens.
- **Index files:** A path that ends in `/` (for example `/blog/`) loads `index.html` in that folder on most servers.
- **Clean URLs:** Many sites hide `.html` (for example `/about`). This needs a server rule or a framework.
- **Link text and images:** If a link has only an image, the `alt` text of the image is the link text.
- **Block-level links:** HTML5 lets an `<a>` contain block content (for example a whole card). Use it with care. Keep the link text short and clear.
- **Link states in CSS:** `:link`, `:visited`, `:hover`, `:focus`, `:active`. Use this order: **L**o**V**e **HA**te (LVHA).

## 1.9 Exercises

1. Write the path from `contact/form.html` to `images/photo.jpg`.
2. A file is in `blog/2026/post.html`. Write the path to `index.html` in the root.
3. Rewrite these link texts so that they are clear: `Click here`, `Read more`, `Link`.
4. Make a link that wraps an image. Write correct `alt` text.
5. Find the error:
   ```html
   <a href="About.html">About</a>
   ```
   The file is named `about.html`. What problem can this cause?
6. **Advanced:** Add `<base href="https://example.com/">` to a test page. Check what happens to your relative links. Then remove it.

## 1.10 Check your understanding
- What does `href` mean?
- When do you use an absolute path?
- What does `../` mean?
- Why is "click here" bad link text?

---

# Lesson 2: Internal Page Links and `#id` Jumps

## 2.1 Learning objectives
After this lesson, you can:
- Make a link to a part of the same page.
- Make a link to a part of another page.
- Make a "back to top" link.
- Make a table of contents.

## 2.2 Fragments

A **fragment** is the part of a URL after `#`. It points to an element with the same `id`.

```html
<!-- The link -->
<a href="#contact">Go to contact</a>

<!-- The target -->
<h2 id="contact">Contact</h2>
```

When the user clicks the link, the browser scrolls to the element with `id="contact"`.

## 2.3 Rules for `id`

1. The `id` must be **unique** in the page.
2. The `id` must not have spaces.
3. Use lowercase letters, numbers, and hyphens: `section-one`.
4. Start with a letter.
5. `id` values are case-sensitive: `#Contact` and `#contact` are different.

## 2.4 Link to a part of another page

Add the fragment after the file name.

```html
<a href="about.html#team">See our team</a>
<a href="https://example.com/faq.html#shipping">Shipping questions</a>
```

## 2.5 Special fragments

| Link | Result |
|------|--------|
| `<a href="#">` | Goes to the top of the page. |
| `<a href="#top">` | Goes to the top of the page. (HTML5 rule) |
| `<a href="#nonexistent">` | Does nothing, and the URL changes. |

**Tip:** `href="#"` is also used as a placeholder while you build. Replace it with a real link before you publish.

## 2.6 Table of contents example

```html
<h1>Long Article</h1>

<nav aria-label="Table of contents">
  <ol>
    <li><a href="#intro">Introduction</a></li>
    <li><a href="#method">Method</a></li>
    <li><a href="#result">Result</a></li>
  </ol>
</nav>

<h2 id="intro">Introduction</h2>
<p>...</p>

<h2 id="method">Method</h2>
<p>...</p>

<h2 id="result">Result</h2>
<p>...</p>

<p><a href="#top">Back to top</a></p>
```

## 2.7 Try It

1. Make a page with 4 `<h2>` sections. Write 5 to 6 paragraphs in each section, so that the page is long.
2. Add `id` to each `<h2>`.
3. Add a table of contents at the top with `#id` links.
4. Add a "Back to top" link at the end of each section.
5. Click the links. Look at the address bar. The `#id` shows at the end.
6. Make a second page. Link to a section of the first page (`page1.html#section-2`).

## 2.8 Advanced Note

- **`:target` in CSS:** The CSS selector `:target` selects the element that matches the fragment. You can highlight it.
  ```css
  :target { background: lightyellow; }
  ```
- **Smooth scrolling:** Add `html { scroll-behavior: smooth; }` in CSS. Respect users that reduce motion: use `@media (prefers-reduced-motion: no-preference)`.
- **Fixed headers:** A fixed header can cover the target element. Use `scroll-margin-top` on the target in CSS.
- **Text fragments:** Chromium browsers support `#:~:text=...` to link to text on a page, with no `id`. Example: `page.html#:~:text=hello`.
- **Focus management:** When the browser jumps to a fragment, keyboard focus moves to that point in newer browsers. This helps keyboard and screen reader users.
- **`name` attribute:** Old HTML used `<a name="x">` for targets. Do not use it. Use `id`.
- **Single-page apps:** Many apps use the fragment for routing (`#/home`). Modern apps use the History API instead.

## 2.9 Exercises

1. Make a FAQ page with 5 questions. Make a list of links at the top that jump to each answer.
2. Add "Back to top" links after each answer.
3. Make a link from `index.html` to a section in `about.html`.
4. Find the error:
   ```html
   <a href="#Intro">Intro</a>
   <h2 id="intro">Introduction</h2>
   ```
5. **Advanced:** Use `:target` to highlight the section that the user selects. Add `scroll-margin-top` for a fixed header.

## 2.10 Check your understanding
- What is a fragment?
- What attribute is the target of a `#` link?
- How do you link to a section on another page?
- Can two elements have the same `id`?

---

# Lesson 3: Link Attributes - `target`, `rel`, `download`, `mailto:`, `tel:`

## 3.1 Learning objectives
After this lesson, you can:
- Open links in a new tab, and know the risks.
- Use `rel` correctly.
- Make download links.
- Make email and phone links.

## 3.2 The `target` attribute

`target` tells the browser where to open the link.

| Value | Result |
|-------|--------|
| `_self` | Opens in the same tab. This is the default. |
| `_blank` | Opens in a new tab or window. |
| `_parent` | Opens in the parent frame. |
| `_top` | Opens in the full window (leaves all frames). |

```html
<a href="https://example.com" target="_blank">Example (opens in a new tab)</a>
```

**Best practice:**
- Use the default (`_self`) for most links. The user can open a new tab if they want.
- Use `_blank` only when the user can lose work (for example a form), or for a document that supports the current page.
- If a link opens in a new tab, tell the user in the link text.

## 3.3 The `rel` attribute

`rel` shows the **relationship** between the current page and the destination.

| Value | Meaning |
|-------|---------|
| `noopener` | The new page cannot control the old page (`window.opener`). |
| `noreferrer` | The browser does not send the `Referer` header. It also gives `noopener`. |
| `nofollow` | Tells search engines not to follow the link for ranking. |
| `external` | The link goes to another website. |
| `sponsored` | The link is paid or an advertisement. |
| `ugc` | The link is user-generated content (for example a comment). |
| `author` | The link goes to the page author. |
| `next` / `prev` | The link goes to the next or previous page in a series. |

**Safe pattern for new tabs:**
```html
<a href="https://example.com" target="_blank" rel="noopener noreferrer">Example</a>
```

**Note:** Modern browsers use `noopener` by default for `target="_blank"`. Write it anyway. It makes your intent clear and protects older browsers.

## 3.4 The `download` attribute

`download` tells the browser to **save** the file and not to open it.

```html
<a href="files/price-list.pdf" download>Download the price list (PDF, 250 KB)</a>
<a href="files/price-list.pdf" download="prices-2026.pdf">Download with a new name</a>
```

- `download` works only for files on the **same origin** (same website).
- Write the file type and size in the link text.

## 3.5 Email links: `mailto:`

```html
<a href="mailto:hello@example.com">Send us an email</a>
```

### Add a subject, copy, and body

```html
<a href="mailto:hello@example.com?subject=Question%20about%20pricing&body=Hello%2C%20I%20have%20a%20question.">
  Email us about pricing
</a>
```

| Parameter | Use |
|-----------|-----|
| `subject` | The email subject. |
| `body` | The email text. |
| `cc` | A copy to another address. |
| `bcc` | A hidden copy. |

Rules:
- Start the first parameter with `?`.
- Separate the other parameters with `&`.
- Replace spaces with `%20`.

## 3.6 Phone links: `tel:`

```html
<a href="tel:+911234567890">Call +91 123 456 7890</a>
```

- Use the international format: `+` and the country code.
- Do not put spaces, dashes, or brackets in the `href`.
- On a phone, the user can tap to call. On a computer, the link can open a calling app or do nothing.

### Other schemes

| Scheme | Use |
|--------|-----|
| `sms:+911234567890` | Opens a text message. |
| `https://wa.me/911234567890` | Opens a WhatsApp chat. |

## 3.7 Link to files

```html
<a href="docs/report.pdf">Read the report (PDF)</a>
<a href="data/results.csv" download>Download the data (CSV)</a>
```

Tell the user the file type and size.

## 3.8 Try It

1. Make a link to MDN that opens in a new tab. Add `rel="noopener noreferrer"`.
2. Make a link to download a PDF. Put a sample PDF in a `files/` folder.
3. Make an email link with a subject.
4. Make a phone link with your country code.
5. On a phone (or in Chrome device mode), tap the phone link.

## 3.9 Advanced Note

- **Reverse tabnabbing:** An old page opened with `target="_blank"` and no `noopener` can use `window.opener.location` to send the user to a fake page. Use `rel="noopener"`.
- **Privacy and `noreferrer`:** `Referer` tells the destination site where the user came from. `noreferrer` stops this. Some analytics tools then count the visit as "direct".
- **Referrer policy:** You can set a site-wide rule with `<meta name="referrer" content="strict-origin-when-cross-origin">`, or per link with `referrerpolicy`.
- **`ping` attribute:** `<a ping>` sends a tracking request. Browser support is limited. Avoid it.
- **`hreflang` and `type`:** `hreflang="fr"` tells the language of the destination. `type="application/pdf"` tells the file type. Both are hints only.
- **Named targets:** `target="mywindow"` opens the link in a window or frame with that name. Use it with `<iframe name="mywindow">`.
- **Cross-origin downloads:** For a file on a different origin, `download` is ignored. The server must send `Content-Disposition: attachment`.
- **Spam:** Public email addresses in HTML are collected by spam robots. Use a contact form, or obfuscate the address.
- **`mailto:` limits:** It depends on a mail app on the user's device. Always show the address in the text, so users can copy it.
- **Accessibility of new tabs:** WCAG advice: warn users before a link opens a new window. Example: `<a ... target="_blank">Report (opens in a new tab)</a>`.

## 3.10 Exercises

1. Write a link to an outside website that opens in a new tab in a safe way.
2. Write a download link for `brochure.pdf` with the file type and size in the text.
3. Write a `mailto:` link with a subject and a body text.
4. Write the correct `tel:` link for this number: `+44 (20) 7946 0958`.
5. Find the problem:
   ```html
   <a href="https://example.com" target="_blank">Click here</a>
   ```
   (List 2 problems.)
6. **Advanced:** Make a page that uses `window.opener` in a test to show why `noopener` is important. Use two local pages only.

## 3.11 Check your understanding
- What does `target="_blank"` do?
- Why do you add `rel="noopener"`?
- When does `download` not work?
- How do you write a phone link?

---

# Lesson 4: Build a Navigation Menu with `<nav>`

## 4.1 Learning objectives
After this lesson, you can:
- Use `<nav>` correctly.
- Build a menu as a list of links.
- Show the current page.
- Make a navigation that works with a keyboard and a screen reader.

## 4.2 The `<nav>` element

`<nav>` marks a block of **main navigation links**.

```html
<nav>
  <a href="index.html">Home</a>
  <a href="about.html">About</a>
  <a href="contact.html">Contact</a>
</nav>
```

- Use `<nav>` for main menus, a table of contents, and pagination.
- Do not use `<nav>` for every group of links. For example, a small list of links in a footer does not need `<nav>`.

## 4.3 Use a list inside `<nav>`

A menu is a list of links. A list gives the screen reader the number of items.

```html
<nav aria-label="Main">
  <ul>
    <li><a href="index.html">Home</a></li>
    <li><a href="about.html">About</a></li>
    <li><a href="services.html">Services</a></li>
    <li><a href="contact.html">Contact</a></li>
  </ul>
</nav>
```

| Part | Job |
|------|-----|
| `<nav>` | Tells browsers and assistive tools that this is navigation. |
| `aria-label="Main"` | Gives the menu a name. It helps if the page has more than one `<nav>`. |
| `<ul>` and `<li>` | Make the menu a list. |

## 4.4 Show the current page

Add `aria-current="page"` to the link of the current page.

```html
<nav aria-label="Main">
  <ul>
    <li><a href="index.html">Home</a></li>
    <li><a href="about.html" aria-current="page">About</a></li>
    <li><a href="contact.html">Contact</a></li>
  </ul>
</nav>
```

- Screen readers say "current page".
- You can style it in CSS: `a[aria-current="page"] { font-weight: bold; }`

## 4.5 Put the menu in a `<header>`

```html
<header>
  <a href="index.html">My Site</a>
  <nav aria-label="Main">
    <ul>
      <li><a href="index.html">Home</a></li>
      <li><a href="about.html">About</a></li>
      <li><a href="contact.html">Contact</a></li>
    </ul>
  </nav>
</header>
```

## 4.6 Rules for good navigation

1. Use the **same menu on all pages**, in the same place.
2. Keep the menu short: 7 items or fewer.
3. Use clear, short names.
4. Show the current page.
5. Make all links work with the keyboard (`Tab` and `Enter`).
6. Add a **skip link** for keyboard users. Module 08 teaches this.

## 4.7 Other types of navigation

### Breadcrumbs
```html
<nav aria-label="Breadcrumb">
  <ol>
    <li><a href="index.html">Home</a></li>
    <li><a href="products.html">Products</a></li>
    <li aria-current="page">Laptops</li>
  </ol>
</nav>
```

### Footer links
```html
<footer>
  <nav aria-label="Footer">
    <ul>
      <li><a href="privacy.html">Privacy</a></li>
      <li><a href="terms.html">Terms</a></li>
    </ul>
  </nav>
</footer>
```

## 4.8 Try It

1. Make 3 pages: `index.html`, `about.html`, `contact.html`.
2. Add the same `<nav>` to each page.
3. Add `aria-current="page"` to the correct link on each page.
4. Use only the `Tab` key to move through the menu. Press `Enter` on a link.
5. Add a breadcrumb to `contact.html`.

## 4.9 Advanced Note

- **Landmarks:** `<nav>` has the ARIA role `navigation`. Screen reader users can jump from landmark to landmark. Do not add `role="navigation"` to `<nav>`. It is redundant.
- **Unique names:** If a page has more than one `<nav>`, give each one a different `aria-label`. Do not include the word "navigation" in the label. The screen reader already says it.
- **Dropdown menus:** Dropdowns need care. Use a `<button>` with `aria-expanded` to open a submenu. Do not use `role="menu"` for site navigation. It is for application menus.
- **Mobile menus ("hamburger"):** Use a `<button aria-expanded="false" aria-controls="menu-id">`. Update `aria-expanded` with JavaScript.
- **Disclosure without JavaScript:** You can use `<details>` and `<summary>` for a simple collapsible menu.
- **Repeating content:** The same menu on each page is **consistent navigation**. WCAG requires it (Success Criterion 3.2.3).
- **Templates:** With plain HTML, you copy the menu to each page. Tools such as static site generators (Eleventy, Astro, Jekyll) and server includes reuse one menu file. You can learn this later.
- **SEO:** Links in `<nav>` help search engines find your pages. Use a `sitemap.xml` also (Module 09).
- **Performance:** Use `rel="prefetch"` for the next page to load it earlier. Use it with care.

## 4.10 Exercises

1. Make a menu with 5 links in a `<ul>` inside `<nav>`.
2. Add `aria-label` and `aria-current="page"`.
3. Make a breadcrumb for this path: Home > Blog > 2026 > My Post.
4. Make a page with a main menu and a footer menu. Give each `<nav>` a different `aria-label`.
5. Fix the error:
   ```html
   <nav role="navigation" aria-label="Main navigation">
   ```
6. **Advanced:** Use a screen reader. List the landmarks on your page. Check that each one has a clear name.

## 4.11 Check your understanding
- What does `<nav>` mean?
- Why do we put links in a list?
- What does `aria-current="page"` do?
- Should all pages have the same menu?

---

# Lesson 5: Module Project - Multi-Page Mini Site

## 5.1 Project goal
Build a mini website with at least 4 pages. Connect the pages with correct links. Use a consistent navigation menu.

## 5.2 Choose a topic

Pick one topic:
- Personal portfolio
- A hobby or club
- A small business (real or invented)
- A travel guide
- A fan page for a game, sport, or book

## 5.3 Required pages

| Page | File | Content |
|------|------|---------|
| Home | `index.html` | Welcome text and a short summary of the site. |
| About | `about.html` | Who you are or what the site is about. |
| Content page | `articles.html` (or a name you choose) | A long page with at least 3 sections and a table of contents. |
| Contact | `contact.html` | Email link, phone link, and address. |

## 5.4 Project folder

```
project/
├── index.html
├── about.html
├── articles.html
├── contact.html
├── files/
│   └── sample.pdf
├── images/
│   └── logo.png
└── README.md
```

## 5.5 Requirements

### Level 1: Beginner (required)
- [ ] 4 pages. Each page has the full HTML boilerplate.
- [ ] Each page has a different, clear `<title>`.
- [ ] The same `<nav>` with a `<ul>` on all pages.
- [ ] `aria-current="page"` on the correct link on each page.
- [ ] A table of contents with `#id` links on the content page.
- [ ] At least one "Back to top" link.
- [ ] At least one link to an outside website. It opens in a new tab with `rel="noopener noreferrer"`.
- [ ] A `mailto:` link and a `tel:` link on the contact page.
- [ ] A download link for a file, with the file type and size in the text.
- [ ] No "click here" link text.
- [ ] All links work. No 404 errors.
- [ ] Use only relative paths for your own pages.
- [ ] All file names are lowercase, with hyphens.

### Level 2: Intermediate (recommended)
- [ ] Put the site in a subfolder. Make a page at a deeper level (for example `blog/post-1.html`). Use `../` correctly.
- [ ] Add breadcrumbs on the deeper page.
- [ ] Add a footer with a second `<nav aria-label="Footer">`.
- [ ] Link to a section of another page (`about.html#team`).
- [ ] Validate all pages with `https://validator.w3.org`. Fix all errors.

### Level 3: Advanced (optional)
- [ ] Use a link checker. Examples: `npx linkinator ./project --recurse` or the W3C Link Checker.
- [ ] Use `:target` and `scroll-margin-top` in CSS.
- [ ] Add a custom `404.html` page.
- [ ] Publish the site on GitHub Pages. Make sure that all links work on the live site.
- [ ] Get a Lighthouse score of 100 for Accessibility.

## 5.6 Steps

1. Choose your topic.
2. Draw a **site map** (a diagram of pages and links) on paper.
   ```
   index.html ──┬── about.html
                ├── articles.html  (#section-1, #section-2, #section-3)
                └── contact.html
   ```
3. Make the folder and empty files.
4. Build `index.html`. Complete the `<nav>`.
5. Copy the HTML skeleton and the `<nav>` to the other pages. Change `<title>`, `<h1>`, and `aria-current`.
6. Add the content for each page.
7. Test all links. Use the keyboard also.
8. Validate the pages.
9. Write `README.md` with the site map.
10. Commit and push:
    ```bash
    git add .
    git commit -m "Add Module 03 multi-page mini site"
    git push
    ```

## 5.7 Starter template (use on each page)

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Page Name | Site Name</title>
  </head>
  <body>
    <header>
      <a href="index.html">Site Name</a>
      <nav aria-label="Main">
        <ul>
          <li><a href="index.html" aria-current="page">Home</a></li>
          <li><a href="about.html">About</a></li>
          <li><a href="articles.html">Articles</a></li>
          <li><a href="contact.html">Contact</a></li>
        </ul>
      </nav>
    </header>

    <main>
      <h1>Page Title</h1>
      <p>Page content.</p>
    </main>

    <footer>
      <p><small>&copy; 2026 Your Name</small></p>
    </footer>
  </body>
</html>
```

`<header>`, `<main>`, and `<footer>` are semantic elements. Module 07 explains them in full.

## 5.8 Contact page example

```html
<h1>Contact</h1>
<ul>
  <li>Email: <a href="mailto:hello@example.com?subject=Hello">hello@example.com</a></li>
  <li>Phone: <a href="tel:+911234567890">+91 123 456 7890</a></li>
  <li>Follow us: <a href="https://github.com/your-username" target="_blank" rel="noopener noreferrer">GitHub (opens in a new tab)</a></li>
  <li><a href="files/sample.pdf" download>Download our brochure (PDF, 120 KB)</a></li>
</ul>
```

## 5.9 Self-check list

1. Does each page have a different `<title>`?
2. Is the menu the same on all pages?
3. Does each page show the correct current link?
4. Do all internal links work from each page?
5. Does each outside link that opens in a new tab have `rel="noopener noreferrer"`?
6. Is the link text clear? Can you understand each link out of context?
7. Can you use the whole site with only the keyboard?
8. Does the validator show 0 errors?

## 5.10 Grading guide (self-assessment)

| Area | Points |
|------|--------|
| All links work (paths correct) | 25 |
| Consistent `<nav>` with `aria-current` | 20 |
| Fragment links and table of contents | 10 |
| Link attributes (`target`, `rel`, `download`, `mailto`, `tel`) | 15 |
| Clear link text | 10 |
| Validator shows 0 errors | 10 |
| Git commits and README | 10 |
| **Total** | **100** |

A score of 80 or more means you are ready for Module 04.

---

# Module 03 Review

## Final quiz

**Questions**

1. What does `href` mean?
2. When do you use an absolute path? When do you use a relative path?
3. Write the path from `contact/form.html` to `index.html`.
4. What attribute does a `#section` link point to?
5. What does `target="_blank"` do? Which `rel` value must you add?
6. What does the `download` attribute do?
7. Write a link that opens an email to `a@b.com` with the subject "Hi".
8. Why do we put menu links inside a `<ul>`?
9. What does `aria-current="page"` do?
10. Why is "click here" bad link text?

**Answers**

1. Hypertext reference: the address of the destination.
2. Absolute: for other websites. Relative: for pages in your own site.
3. `../index.html`
4. The element with the same `id`.
5. It opens the link in a new tab. Add `rel="noopener"` (or `noopener noreferrer`).
6. It tells the browser to save the file and not open it.
7. `<a href="mailto:a@b.com?subject=Hi">Email us</a>`
8. A list tells screen reader users how many items the menu has, and it groups the links.
9. It marks the link of the current page for assistive tools (and can be used for styling).
10. The text does not say where the link goes. Screen reader users and search engines cannot understand it out of context.

## Common mistakes

| Mistake | Fix |
|---------|-----|
| `href` with a wrong path | Check folders. Use `../` to go up. |
| Wrong letter case in file name | Use lowercase names. Match them exactly. |
| Spaces in file names | Use hyphens. |
| `/about.html` (root-relative) on a local file or project site | Use `about.html` or `./about.html`. |
| `target="_blank"` without `rel` | Add `rel="noopener noreferrer"`. |
| "Click here" text | Write the destination. |
| `#id` with different letter case | `id` values are case-sensitive. |
| Two elements with the same `id` | Make each `id` unique. |
| `tel:` with spaces or brackets | Write `tel:+911234567890`. |
| Different menus on different pages | Use the same menu everywhere. |
| `role="navigation"` on `<nav>` | Remove it. It is redundant. |
| Link to a file with no type or size | Add "(PDF, 250 KB)" to the link text. |

## Glossary

| Term | Definition |
|------|------------|
| Absolute path | A full URL with the scheme and domain. |
| Anchor | The `<a>` element. |
| Breadcrumb | A trail of links that shows where the user is in the site. |
| Fragment | The part of a URL after `#`. |
| Hyperlink | A link from one resource to another. |
| Landmark | A page region that assistive tools can find (for example `<nav>`). |
| Link text | The visible words of a link. |
| Navigation | A set of links that help users move through a site. |
| Relative path | A path from the current file to another file. |
| Root-relative path | A path that starts with `/` and goes from the root of the site. |
| Site map | A diagram or list of all pages in a site. |
| URL | The address of a resource on the web. |

## Module 03 progress checklist (copy to `PROGRESS.md`)

```markdown
## Module 03: Links and Navigation
- [ ] Lesson 1: Anchor tag, absolute vs relative paths
- [ ] Lesson 2: Internal page links and #id jumps
- [ ] Lesson 3: target, rel, download, mailto, tel
- [ ] Lesson 4: Building a nav menu
- [ ] Lesson 5: Multi-page mini site project
- [ ] Final quiz (8/10 or more)
- [ ] All links tested (no 404 errors)
- [ ] All pages validated with W3C
- [ ] Project pushed to GitHub
```

## Cheat sheet: Module 03

```html
<!-- Absolute (other site) -->
<a href="https://example.com">Example</a>

<!-- Relative (your site) -->
<a href="about.html">Same folder</a>
<a href="blog/post.html">Folder below</a>
<a href="../index.html">One folder up</a>

<!-- Fragment -->
<a href="#section">Same page</a>
<a href="page.html#section">Other page</a>
<h2 id="section">Target</h2>

<!-- New tab (safe) -->
<a href="https://example.com" target="_blank" rel="noopener noreferrer">Link (new tab)</a>

<!-- Download, email, phone -->
<a href="files/doc.pdf" download>Download (PDF, 1 MB)</a>
<a href="mailto:a@b.com?subject=Hi">Email</a>
<a href="tel:+911234567890">Call</a>

<!-- Navigation -->
<nav aria-label="Main">
  <ul>
    <li><a href="index.html" aria-current="page">Home</a></li>
    <li><a href="about.html">About</a></li>
  </ul>
</nav>
```

| Path symbol | Meaning |
|-------------|---------|
| `file.html` / `./file.html` | Same folder |
| `folder/file.html` | Folder below |
| `../file.html` | One folder up |
| `/file.html` | Root of the site |

## Next module
Go to **Module 04: Media**. You learn images, responsive images, audio, video, embeds, and inline SVG.
