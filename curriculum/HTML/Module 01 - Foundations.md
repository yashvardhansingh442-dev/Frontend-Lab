# Module 01: Foundations

**Folder:** `01-foundations/`
**Level:** Beginner (with Advanced notes)
**Time:** 6 to 8 hours
**Writing style:** ASD-STE100 (Simplified Technical English)

---

## Module Overview

### Goal
Learn how a web page works. Set up your tools. Write and publish your first HTML page.

### Prerequisites
- A computer (Windows, macOS, or Linux)
- An internet connection
- No coding experience is necessary

### What you learn
After this module, you can:
1. Explain how a browser gets a web page from a server.
2. Install and configure VS Code, Git, and a GitHub account.
3. Write a valid HTML document from memory.
4. Use elements, attributes, and nesting correctly.
5. Use comments, whitespace rules, and character entities.
6. Build and publish a "Hello World" page.

### How to use this module
- Read each lesson in order.
- Do the **Try It** tasks while you read. Do not skip them.
- Read the **Advanced Note** boxes if you have experience. Beginners can skip them and return later.
- Do the **Exercises** at the end of each lesson.
- Do the **Module Project** last.

### Folder structure for this module
```
01-foundations/
├── lesson-01-how-the-web-works.md
├── lesson-02-setting-up.md
├── lesson-03-html-document-anatomy.md
├── lesson-04-elements-tags-attributes.md
├── lesson-05-comments-whitespace-entities.md
├── lesson-06-project-hello-world.md
├── examples/
├── exercises/
└── project/
```

---

# Lesson 1: How the Web Works

## 1.1 Learning objectives
After this lesson, you can:
- Name the parts of a web request.
- Explain the job of a client and a server.
- Explain the parts of a URL.
- Name the roles of HTML, CSS, and JavaScript.

## 1.2 Key terms

| Term | Meaning |
|------|---------|
| Client | A device or program that asks for data. Your browser is a client. |
| Server | A computer that stores files and sends them to clients. |
| Browser | A program that gets web pages and shows them. Examples: Chrome, Firefox, Safari, Edge. |
| HTTP | HyperText Transfer Protocol. The set of rules that a client and a server use to talk. |
| HTTPS | HTTP with encryption. It keeps the data private. |
| URL | Uniform Resource Locator. The address of a resource on the web. |
| DNS | Domain Name System. It changes a domain name into an IP address. |
| IP address | A number that identifies a computer on a network. Example: `93.184.216.34` |
| Request | A message from the client to the server. |
| Response | A message from the server to the client. |

## 1.3 The request and response cycle

Follow these steps when you open `https://example.com` in a browser:

1. **You type the URL.** The browser reads it.
2. **The browser asks DNS for the IP address.** DNS is like a phone book for the web.
3. **The browser opens a connection to the server.** For HTTPS, the browser and server also set up encryption.
4. **The browser sends an HTTP request.** The request says: "Send me the page at `/`."
5. **The server sends an HTTP response.** The response has a status code, headers, and a body. The body is the HTML file.
6. **The browser reads the HTML.** It finds other files that it needs (CSS, JavaScript, images, fonts).
7. **The browser asks for those files.** Steps 4 to 6 repeat for each file.
8. **The browser shows the page.**

```
 Browser (client)                          Server
      |                                       |
      |  1. DNS lookup (name -> IP)           |
      |-------------------------------------->|
      |  2. HTTP request: GET /index.html     |
      |-------------------------------------->|
      |  3. HTTP response: 200 OK + HTML      |
      |<--------------------------------------|
      |  4. Requests for CSS, JS, images      |
      |-------------------------------------->|
      |<--------------------------------------|
      |  5. Browser draws the page            |
```

## 1.4 Parts of a URL

```
https://www.example.com:443/blog/post.html?id=7#comments
\___/   \_____________/ \_/ \____________/ \___/ \______/
  |            |         |        |          |       |
scheme       host      port     path       query  fragment
```

| Part | Example | Meaning |
|------|---------|---------|
| Scheme | `https` | The protocol to use. |
| Host | `www.example.com` | The name of the server. |
| Port | `443` | The door on the server. HTTPS uses 443. HTTP uses 80. The browser hides the default port. |
| Path | `/blog/post.html` | The location of the file on the server. |
| Query | `?id=7` | Extra data that you send to the server. |
| Fragment | `#comments` | A place inside the page. The browser does not send it to the server. |

## 1.5 Common HTTP status codes

| Code | Name | Meaning |
|------|------|---------|
| 200 | OK | The request worked. |
| 301 | Moved Permanently | The page has a new address. |
| 304 | Not Modified | Use the copy that you saved before. |
| 403 | Forbidden | You do not have permission. |
| 404 | Not Found | The server does not have this page. |
| 500 | Internal Server Error | The server has a problem. |

**Memory rule:** 2xx = success. 3xx = redirect. 4xx = client error. 5xx = server error.

## 1.6 The three languages of the web

| Language | Job | Simple example |
|----------|-----|----------------|
| **HTML** | Structure and content | "This is a heading. This is a paragraph." |
| **CSS** | Appearance | "Make the heading blue." |
| **JavaScript** | Behavior | "Show a message when the user clicks." |

Think of a house:
- HTML is the walls and rooms.
- CSS is the paint and furniture.
- JavaScript is the electricity and switches.

This course starts with HTML. HTML is the base for all web pages.

## 1.7 Try It: See a real request

1. Open Chrome or Edge.
2. Go to `https://example.com`.
3. Press `F12` to open Developer Tools.
4. Click the **Network** tab.
5. Press `Ctrl + R` (Windows/Linux) or `Cmd + R` (macOS) to reload.
6. Click the first item in the list (`example.com`).
7. Read the **Headers** tab. Find the status code and the request method.
8. Click the **Response** tab. This is the HTML of the page.

## 1.8 Advanced Note: What the browser does with HTML

The browser does these steps to show a page (the rendering pipeline):

1. **Parse HTML.** The browser builds the **DOM** (Document Object Model), a tree of objects.
2. **Parse CSS.** The browser builds the **CSSOM**.
3. **Combine.** The browser makes the **render tree**. It has only the visible nodes.
4. **Layout.** The browser calculates size and position of each box.
5. **Paint.** The browser draws pixels.
6. **Composite.** The browser puts the layers together on the screen.

More facts for advanced learners:
- The HTML parser works in a stream. It can start to build the DOM before the full file arrives.
- A `<script>` tag without `defer` or `async` blocks the parser. You learn this in Module 10.
- HTTP/2 and HTTP/3 let the browser send many requests on one connection.
- Servers use `Cache-Control` headers to tell the browser how long to keep a file.

## 1.9 Exercises

1. Write the full path of the request cycle in your own words (8 steps maximum).
2. Divide this URL into its parts: `http://shop.test:8080/items/list?sort=price#top`
3. Open any website. In the Network tab, find one 200 response, and one file type that is not HTML.
4. Type a wrong address, such as `https://example.com/nothing-here`. Find the status code.
5. **Advanced:** Find the `Content-Type` and `Cache-Control` headers for the HTML response. Write what each header does.

## 1.10 Check your understanding
- What is the difference between a client and a server?
- What does DNS do?
- Which language gives a page its structure?
- What does a 404 code mean?

---

# Lesson 2: Setting Up

## 2.1 Learning objectives
After this lesson, you can:
- Install VS Code and use it to edit files.
- Use Live Server to see changes at once.
- Install Git and make a commit.
- Make a GitHub repository and push your code.

## 2.2 Install the tools

### Tool 1: A modern browser
Install Chrome, Firefox, or Edge. This course uses Chrome examples. Other browsers work too.

### Tool 2: VS Code
1. Go to `https://code.visualstudio.com`.
2. Download the version for your system.
3. Install it. Use the default settings.

### Tool 3: VS Code extensions
Open the Extensions panel (`Ctrl + Shift + X`). Install these:

| Extension | Purpose |
|-----------|---------|
| **Live Server** (Ritwick Dey) | Reloads the page when you save a file. |
| **Prettier - Code formatter** | Formats your code in a standard way. |
| **HTML CSS Support** (optional) | Gives help for class names. |
| **Auto Rename Tag** (optional) | Changes the closing tag when you change the opening tag. |

### Tool 4: Git
1. Go to `https://git-scm.com`.
2. Download and install Git.
3. Open a terminal. Type: `git --version`
4. If you see a version number, Git is ready.

### Tool 5: GitHub account
1. Go to `https://github.com`.
2. Make a free account.
3. Choose a username that you can show to employers.

## 2.3 Configure Git (one time)

Use your own name and email.

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --global init.defaultBranch main
```

## 2.4 Make your project folder

1. Make a folder named `html-course`.
2. Open VS Code.
3. Click **File > Open Folder**. Select `html-course`.
4. Make a new file. Name it `index.html`.

**File name rules:**
- Use lowercase letters.
- Use hyphens instead of spaces. Write `my-page.html`, not `My Page.html`.
- Do not use special characters.
- The main page of a site is always `index.html`.

## 2.5 Try It: Use Live Server

1. Type this in `index.html`:
   ```html
   <h1>Hello</h1>
   ```
2. Save the file (`Ctrl + S`).
3. Right-click the file. Select **Open with Live Server**.
4. The browser opens. You see "Hello".
5. Change "Hello" to "Hello, world". Save.
6. The browser updates without a manual reload.

## 2.6 Make your first commit

Open the VS Code terminal (`Ctrl + ~`). Type:

```bash
git init
git add .
git commit -m "Add first index.html"
```

| Command | Meaning |
|---------|---------|
| `git init` | Starts a Git repository in this folder. |
| `git add .` | Selects all changed files for the next commit. |
| `git commit -m "..."` | Saves a snapshot with a message. |
| `git status` | Shows what changed. |
| `git log --oneline` | Shows the list of commits. |

## 2.7 Push to GitHub

1. On GitHub, click **New repository**.
2. Name it `html-course`. Do not add a README (you already have files).
3. Copy the two commands that GitHub shows. They look like this:

```bash
git remote add origin https://github.com/YOUR-USERNAME/html-course.git
git push -u origin main
```

4. Refresh the GitHub page. Your file is there.

## 2.8 Good commit messages

- Start with a verb: `Add`, `Fix`, `Update`, `Remove`.
- Keep the first line under 50 characters.
- Say what changed.

| Bad | Good |
|-----|------|
| `stuff` | `Add navigation to home page` |
| `fix` | `Fix broken image path` |
| `update` | `Update contact form labels` |

## 2.9 Advanced Note: Better setup

- **`.gitignore`:** Make a file named `.gitignore`. List files that Git must ignore. Example: `.DS_Store`, `node_modules/`.
- **`.editorconfig`:** Set the same indent size and line endings for all editors.
- **SSH keys:** Use SSH instead of HTTPS for GitHub. Run `ssh-keygen -t ed25519`. Add the public key to GitHub.
- **Branches:** Do new work on a branch. Use `git switch -c lesson-02`. Merge it with a pull request.
- **Prettier settings:** Make `.prettierrc` with `{ "printWidth": 100, "tabWidth": 2 }`. Turn on **Format On Save** in VS Code.
- **Emmet:** VS Code has Emmet. Type `!` and press `Tab` to make an HTML boilerplate. Type `ul>li*3` and press `Tab` to make a list of 3 items.

## 2.10 Exercises

1. Install all tools. Run `git --version` and write the result.
2. Make `html-course` and push it to GitHub. Put the link in your `README.md`.
3. Make 3 commits. Each commit must have a clear message.
4. Use `git log --oneline`. Check that you see 3 commits.
5. **Advanced:** Make a `.gitignore` file and a branch named `lesson-02`. Open a pull request on your own repository, and merge it.

## 2.11 Common problems

| Problem | Solution |
|---------|----------|
| Live Server option is missing | Check that the extension is installed. Restart VS Code. |
| `git` is not recognized | Restart the terminal. If the error stays, install Git again. |
| `git push` asks for a password | GitHub does not accept passwords. Use a Personal Access Token or SSH key. |
| Browser shows old content | Do a hard reload: `Ctrl + Shift + R`. |

---

# Lesson 3: Anatomy of an HTML Document

## 3.1 Learning objectives
After this lesson, you can:
- Write a complete HTML document.
- Explain the job of each part.
- Name what goes in `<head>` and what goes in `<body>`.

## 3.2 The minimum HTML document

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>My First Page</title>
  </head>
  <body>
    <h1>Hello, world</h1>
    <p>This is my first web page.</p>
  </body>
</html>
```

## 3.3 Line-by-line explanation

| Line | Job |
|------|-----|
| `<!DOCTYPE html>` | Tells the browser to use modern HTML5 rules. It is not an HTML tag. It must be the first line. |
| `<html lang="en">` | The root element. All other elements are inside it. `lang="en"` sets the language to English. |
| `<head>` | Holds information about the page. The user does not see it on the page. |
| `<meta charset="UTF-8" />` | Sets the character encoding. UTF-8 supports almost all written languages and emoji. |
| `<meta name="viewport" ...>` | Makes the page work correctly on phone screens. |
| `<title>` | The text in the browser tab. Search engines also use it. |
| `<body>` | Holds all content that the user sees. |

## 3.4 Head and body

```
<html>
 ├── <head>   -> Information ABOUT the page (invisible)
 │     ├── <meta>
 │     ├── <title>
 │     └── <link> (CSS)
 └── <body>   -> Content ON the page (visible)
       ├── <h1>
       ├── <p>
       └── <img>
```

**Rule:** Put visible content in `<body>` only. Put metadata in `<head>` only.

## 3.5 Try It: Build the page by hand

1. Make a new file: `lesson-03.html`.
2. Type the minimum document. Do not copy and paste. Type it.
3. Change the title to your name.
4. Change the `<h1>` to a sentence about you.
5. Save. Open with Live Server.
6. Look at the browser tab. Find your title.

**Shortcut:** After you can type it by hand, use Emmet. Type `!` and press `Tab`.

## 3.6 Why `lang` is important
- Screen readers use `lang` to choose the correct voice and pronunciation.
- Browsers use it to offer translation.
- Search engines use it to find the language of the page.

Examples: `lang="en"` (English), `lang="hi"` (Hindi), `lang="fr"` (French), `lang="en-GB"` (British English).

## 3.7 Advanced Note: What happens behind the scenes

- **Quirks mode:** If you do not write `<!DOCTYPE html>`, the browser uses quirks mode. In quirks mode, the layout rules are old and different. Always write the doctype.
- **Implied tags:** The HTML parser adds `<html>`, `<head>`, and `<body>` if you omit them. Do not depend on this. Write all of them.
- **Case:** The doctype and tag names are not case-sensitive. The standard way is lowercase for tags: `<html>`. The doctype is often `<!DOCTYPE html>`.
- **Charset position:** Put `<meta charset>` in the first 1024 bytes of the file. Put it before `<title>`.
- **Viewport:** `width=device-width` sets the layout width to the device width. Do not use `user-scalable=no`. It blocks zoom and causes an accessibility problem.
- **Document order in `<head>`:** A good order is: charset, viewport, title, description, other meta, links to CSS, scripts.
- **Allowed elements in `<head>`:** `<title>`, `<meta>`, `<link>`, `<style>`, `<script>`, `<base>`, `<noscript>`, `<template>`.

## 3.8 Exercises

1. Write the minimum document from memory. Do not look at the lesson.
2. Add `lang="hi"` to the `<html>` tag. What changes in the browser (if anything)?
3. Move an `<h1>` into `<head>`. Open the page. Describe the result.
4. Delete `<!DOCTYPE html>`. In Chrome DevTools, type `document.compatMode` in the Console. Write the result. Put the doctype back and repeat.
5. **Advanced:** Open `view-source:https://developer.mozilla.org`. List 5 elements that you find in `<head>`.

## 3.9 Check your understanding
- What does `<!DOCTYPE html>` do?
- Where does the page title show?
- What is the difference between `<head>` and `<body>`?
- Why do we write `lang`?

---

# Lesson 4: Elements, Tags, Attributes, and Nesting

## 4.1 Learning objectives
After this lesson, you can:
- Identify the parts of an HTML element.
- Use attributes correctly.
- Nest elements in a valid way.
- Tell block elements from inline elements.

## 4.2 Anatomy of an element

```
   opening tag     content          closing tag
  ┌──────────┐ ┌─────────────┐ ┌──────────┐
  <p class="note">Read this text.</p>
   │  └───┬───┘
   │      └── attribute (name="value")
   └── tag name
  └──────────────────────────────────────┘
                 element
```

| Part | Example | Meaning |
|------|---------|---------|
| Opening tag | `<p>` | Starts the element. |
| Content | `Read this text.` | What the element holds. |
| Closing tag | `</p>` | Ends the element. It has a slash. |
| Element | The full group | Opening tag + content + closing tag. |

**Note:** "Tag" and "element" are not the same. A tag is a marker. An element is the complete structure.

## 4.3 Void elements (empty elements)

Some elements have no content and no closing tag. These are **void elements**.

| Element | Purpose |
|---------|---------|
| `<br>` | Line break |
| `<hr>` | Horizontal rule |
| `<img>` | Image |
| `<input>` | Form field |
| `<meta>` | Metadata |
| `<link>` | External resource link |

Write `<br>` or `<br />`. Both are valid in HTML5. Pick one style and use it in all files.

## 4.4 Attributes

An attribute gives extra information to an element.

**Syntax:** `name="value"`

```html
<a href="https://example.com" target="_blank">Visit</a>
<img src="cat.jpg" alt="A grey cat on a sofa" width="300" />
```

**Rules:**
1. Put attributes in the opening tag only.
2. Put a space between the tag name and each attribute.
3. Use double quotes around values.
4. Use lowercase for attribute names.

### Boolean attributes
Some attributes have no value. If the attribute is present, it is "on".

```html
<input type="checkbox" checked />
<button disabled>Save</button>
```

### Global attributes
All elements can have these attributes:

| Attribute | Purpose |
|-----------|---------|
| `id` | A unique name for one element. |
| `class` | A group name. Many elements can share it. |
| `style` | Inline CSS. Avoid it in real projects. |
| `title` | Extra text that shows as a tooltip. |
| `lang` | The language of the element. |
| `hidden` | Hides the element. |
| `tabindex` | Controls the keyboard focus order. |
| `data-*` | Custom data for JavaScript. |

**Rule:** An `id` must be unique in one page.

## 4.5 Nesting

Nesting means to put an element inside another element. The inner element is the **child**. The outer element is the **parent**.

**Correct:**
```html
<p>This is <strong>very</strong> important.</p>
```

**Wrong (overlap):**
```html
<p>This is <strong>very</p></strong>
```

**Rule:** Close the last opened tag first. Think of boxes: the inner box must close before the outer box.

### The family tree

```html
<body>
  <main>
    <h1>Title</h1>
    <p>Text</p>
  </main>
</body>
```

```
body (parent)
 └── main (child of body, parent of h1 and p)
       ├── h1 (child, sibling of p)
       └── p  (child, sibling of h1)
```

### Indentation
Indent each child by 2 spaces. Indentation does not change the page. It helps you read the code.

## 4.6 Block elements and inline elements

| Type | Behavior | Examples |
|------|----------|----------|
| **Block** | Starts on a new line. Takes the full width. | `<div>`, `<p>`, `<h1>`, `<ul>`, `<section>` |
| **Inline** | Stays in the line of text. Takes only the space that it needs. | `<span>`, `<a>`, `<strong>`, `<em>`, `<img>` |

**Rule:** Do not put a block element inside an inline element, such as `<div>` inside `<span>`. Also, do not put block elements inside `<p>`.

## 4.7 Try It: Find the errors

This code has 5 errors. Find them and fix them.

```html
<html>
  <body>
    <h1>My page<h1>
    <p>I like <strong>HTML</p></strong>
    <img src=photo.jpg alt=My photo>
    <p id="intro">First</p>
    <p id="intro">Second</p>
  </body>
</html>
```

**Answers:**
1. `<!DOCTYPE html>` is missing.
2. `<head>` with `<title>` is missing.
3. `<h1>My page<h1>` must be `<h1>My page</h1>`. The closing tag has no slash.
4. `<strong>` and `<p>` overlap. Write `<p>I like <strong>HTML</strong></p>`.
5. The `id="intro"` is used two times. Change one to `id="second"` or use `class`.

(Bonus: attribute values should have quotes: `alt="My photo"`.)

## 4.8 Advanced Note: How the parser handles errors

- **Error recovery:** HTML does not stop on an error. The browser tries to fix it. Different parsers can fix some errors in a different way. For this reason, write valid HTML.
- **Content models:** Each element has rules for the elements it can contain. Example: `<ul>` can only contain `<li>`, `<script>`, and `<template>`. `<p>` cannot contain `<div>`. The browser closes `<p>` when it sees `<div>`.
- **Content categories:** The HTML standard does not use "block" and "inline" in its rules. It uses *flow content*, *phrasing content*, *interactive content*, and others. "Block" and "inline" are CSS display values.
- **Unquoted values:** `class=big` is valid. `class=big small` is not valid. Always use quotes.
- **Custom elements:** A custom element name must have a hyphen. Example: `<my-card>`. Module 11 teaches this.
- **Unknown elements:** The browser treats an unknown element as `HTMLUnknownElement`. It shows the content, and it has no special behavior.
- **Attribute duplicates:** If an attribute appears two times, the browser uses the first one.
- **Validation:** Use the W3C validator at `https://validator.w3.org`. You use it again in Module 12.

## 4.9 Exercises

1. Write a `<p>` with a link inside it. The link goes to `https://developer.mozilla.org`.
2. Write an `<img>` with `src`, `alt`, and `width` attributes.
3. Draw the family tree for this code:
   ```html
   <div><h2>Title</h2><p>Text with <em>emphasis</em>.</p></div>
   ```
4. Make a list of 5 void elements. Write the purpose of each one.
5. Write a `<button>` with the `disabled` attribute. Test it in the browser.
6. **Advanced:** Write `<p>One<div>Two</div></p>`. Open DevTools and look at the Elements panel. Write how the browser changed the structure, and why.

## 4.10 Check your understanding
- What is the difference between a tag and an element?
- Which elements have no closing tag?
- What is a boolean attribute?
- Why must an `id` be unique?

---

# Lesson 5: Comments, Whitespace, and Character Entities

## 5.1 Learning objectives
After this lesson, you can:
- Write HTML comments.
- Explain how the browser handles whitespace.
- Show reserved characters with entities.

## 5.2 Comments

A comment is text that the browser does not show.

```html
<!-- This is a comment -->
<p>This text is visible.</p>
```

**Use comments to:**
- Explain a section of code.
- Mark the start and end of large blocks.
- Hide code for a short time while you test.

```html
<!-- ===== Navigation start ===== -->
<nav>...</nav>
<!-- ===== Navigation end ===== -->
```

**Rules:**
- Do not put a comment inside a tag. `<p <!-- no --> >` is not valid.
- Do not write `--` inside a comment.
- Anyone can read comments with "View Source". Do not put passwords or private data in comments.
- Shortcut in VS Code: `Ctrl + /`.

## 5.3 Whitespace

Whitespace is spaces, tabs, and line breaks.

**The browser collapses whitespace.** It changes many whitespace characters to one space.

```html
<p>Hello          world
and      welcome.</p>
```

**Result in the browser:** `Hello world and welcome.`

| What you write | What the browser shows |
|----------------|------------------------|
| 5 spaces | 1 space |
| A line break | 1 space |
| A blank line | 1 space |
| A tab | 1 space |

### How to make visible spacing

| Need | Use |
|------|-----|
| A new line | `<br>` |
| A new paragraph | A new `<p>` element |
| Exact whitespace (code, poems) | `<pre>` |
| Large gaps | CSS margin and padding (Module 10) |

```html
<pre>
Line one
    Line two (indented)
</pre>
```

**Rule:** Do not use many `&nbsp;` or many `<br>` to make layout. Use CSS.

## 5.4 Character entities

Some characters have a special meaning in HTML. To show them as text, use an **entity**.

**Syntax:** `&name;` or `&#number;`

| Character | Entity | Name |
|-----------|--------|------|
| `<` | `&lt;` | less than |
| `>` | `&gt;` | greater than |
| `&` | `&amp;` | ampersand |
| `"` | `&quot;` | double quote |
| `'` | `&apos;` | apostrophe |
| (space that does not break) | `&nbsp;` | non-breaking space |
| © | `&copy;` | copyright |
| ® | `&reg;` | registered |
| € | `&euro;` | euro |
| — | `&mdash;` | long dash |

**Example: show HTML code on the page.**

```html
<p>Use the &lt;p&gt; tag to make a paragraph.</p>
```

**Result:** Use the `<p>` tag to make a paragraph.

**If you write `<p>` without the entities, the browser reads it as a tag. The text does not show.**

## 5.5 Try It: Entity practice

1. Make a page with this text:
   `5 < 10 & 10 > 5`
2. Write it with the correct entities.
3. Add a footer with `© 2026 Your Name`.
4. Write the sentence: `The <h1> tag is the main heading.` so that the tag shows as text.

## 5.6 Advanced Note: Encoding and entities

- **Use UTF-8.** With `<meta charset="UTF-8">`, you can type `©`, `€`, and `é` directly. You do not need an entity for these.
- **Must-escape characters:** In text, always escape `<` and `&`. In an attribute value inside double quotes, escape `"` and `&`.
- **Numeric entities:** Decimal: `&#169;`. Hexadecimal: `&#xA9;`. Both show ©.
- **`&nbsp;`:** It stops line breaks between two words. Example: `10&nbsp;km`. It is useful for this reason only.
- **Other no-break tools:** CSS `white-space: nowrap` gives more control. `&thinsp;` and `&#8209;` (non-breaking hyphen) are also available.
- **`white-space` in CSS:** The CSS property `white-space` changes how the browser handles whitespace. Values: `normal`, `pre`, `pre-wrap`, `nowrap`.
- **Ambiguous ampersands:** A raw `&` in a URL query, such as `?a=1&b=2`, should be written `?a=1&amp;b=2` in an HTML attribute.
- **Conditional comments:** Old Internet Explorer used special comments. Modern browsers do not use them. Do not use them.
- **Security:** When a program puts user text into HTML, it must escape `<`, `>`, `&`, and quotes. If it does not, it can cause Cross-Site Scripting (XSS).

## 5.7 Exercises

1. Write a paragraph with 10 spaces between two words. Check how it looks. Explain why.
2. Use `<pre>` to show a small ASCII drawing.
3. Write the entity for each: `<`, `>`, `&`, `©`, `€`.
4. Add comments to your `lesson-03.html` file. Mark the start and end of `<head>` and `<body>`.
5. **Advanced:** Write `10 km` with a normal space and with `&nbsp;`. Make the browser window narrow. See which one breaks across lines.

## 5.8 Check your understanding
- How does the browser handle five spaces in a row?
- How do you show `<` as text?
- Can a visitor read your HTML comments?
- When must you use `<pre>`?

---

# Lesson 6: Module Project - Hello World Page

## 6.1 Project goal
Build a clean, valid "Hello World" page. Publish it on GitHub.

## 6.2 Requirements

### Level 1: Beginner (required)
Your page must have:
- [ ] `<!DOCTYPE html>`
- [ ] `<html lang="en">`
- [ ] `<meta charset="UTF-8">`
- [ ] `<meta name="viewport" ...>`
- [ ] A `<title>` with a clear name
- [ ] One `<h1>` with the text "Hello, World!"
- [ ] At least 2 `<p>` paragraphs about you
- [ ] One `<img>` with a correct `alt`
- [ ] One link to your GitHub profile
- [ ] At least 3 comments in the code
- [ ] At least 2 character entities (for example `&copy;` and `&lt;`)
- [ ] A footer line with the year and your name
- [ ] Correct indentation (2 spaces)

### Level 2: Intermediate (recommended)
- [ ] Validate the file with `https://validator.w3.org`. Fix all errors.
- [ ] Use one `<pre>` block that shows code.
- [ ] Use `<br>` in an address or a poem.

### Level 3: Advanced (optional)
- [ ] Add `<meta name="description" ...>`
- [ ] Add an inline favicon: `<link rel="icon" href="data:,">`
- [ ] Get a Lighthouse score of 100 for Accessibility and Best Practices.
- [ ] Make a GitHub Actions workflow that checks your HTML (for example with `html-validate`).

## 6.3 Project folder

```
project/
├── index.html
├── images/
│   └── me.jpg
└── README.md
```

## 6.4 Steps

1. Make the folder `01-foundations/project/`.
2. Make `index.html`. Type the boilerplate.
3. Add the content from the requirements list.
4. Open the file with Live Server. Check each item.
5. Validate the file.
6. Write a `README.md` with: the project name, a short description, and how to open the page.
7. Commit your work:
   ```bash
   git add .
   git commit -m "Add Module 01 Hello World project"
   git push
   ```

## 6.5 Starter template

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Hello World | Your Name</title>
  </head>
  <body>
    <!-- Main heading -->
    <h1>Hello, World!</h1>

    <!-- About me -->
    <p>My name is ... I am learning HTML.</p>
    <p>I want to build ...</p>

    <!-- Picture -->
    <img src="images/me.jpg" alt="Describe the image here" width="300" />

    <!-- Link -->
    <p>See my code on <a href="https://github.com/YOUR-USERNAME">GitHub</a>.</p>

    <!-- Footer -->
    <p>&copy; 2026 Your Name</p>
  </body>
</html>
```

## 6.6 Self-check list

Ask these questions before you finish:
1. Does the page open without errors?
2. Does the browser tab show the correct title?
3. Can a screen reader user understand the image (is the `alt` text clear)?
4. Is every opening tag closed?
5. Is the code indented in the same way everywhere?
6. Does the validator show 0 errors?

## 6.7 Publish (preview of Module 12)

1. In your repository, go to **Settings > Pages**.
2. Under **Source**, select the `main` branch.
3. Save. Wait 1 to 2 minutes.
4. Open the link that GitHub shows. Your page is now online.

## 6.8 Grading guide (self-assessment)

| Area | Points |
|------|--------|
| Valid document structure | 25 |
| Correct elements and attributes | 25 |
| Comments, whitespace, entities | 15 |
| Clean code (indent, names) | 15 |
| Validator shows 0 errors | 10 |
| Git commits and README | 10 |
| **Total** | **100** |

A score of 80 or more means you are ready for Module 02.

---

# Module 01 Review

## Final quiz

**Questions**

1. What does a browser send to a server to ask for a page?
2. What is the job of DNS?
3. Which status code means "Not Found"?
4. What must be the first line of an HTML5 document?
5. Which element holds the text for the browser tab?
6. What is the difference between `<head>` and `<body>`?
7. Name 3 void elements.
8. What is wrong with `<b><i>text</b></i>`?
9. What does the browser do with 5 spaces in a row?
10. Write the entity for `<`.

**Answers**

1. An HTTP request.
2. DNS changes a domain name into an IP address.
3. 404.
4. `<!DOCTYPE html>`.
5. `<title>` (inside `<head>`).
6. `<head>` holds information about the page. `<body>` holds the visible content.
7. For example: `<br>`, `<hr>`, `<img>`, `<input>`, `<meta>`, `<link>`.
8. The tags overlap. Correct: `<b><i>text</i></b>`.
9. It collapses them to one space.
10. `&lt;`

## Common mistakes

| Mistake | Fix |
|---------|-----|
| No doctype | Always write `<!DOCTYPE html>` first. |
| Missing closing tag | Use Prettier. It shows the problem. |
| Overlapping tags | Close the last opened tag first. |
| Missing `alt` on images | Always write `alt`. Use `alt=""` for decorative images only. |
| Spaces in file names | Use hyphens. |
| Same `id` two times | Use `class` for groups. |
| Using `<br>` or `&nbsp;` for layout | Use CSS (Module 10). |
| Wrong file path for images | Check that the folder and file name are correct (case-sensitive on servers). |

## Glossary

| Term | Definition |
|------|------------|
| Attribute | Extra information in an opening tag. |
| Block element | An element that starts on a new line. |
| Child | An element inside another element. |
| Client | A device or program that requests data. |
| DOM | A tree of objects that the browser builds from HTML. |
| Element | Opening tag + content + closing tag. |
| Entity | A code that shows a special character. |
| HTML | The language for the structure of web pages. |
| HTTP | The protocol for web communication. |
| Inline element | An element that stays inside a line of text. |
| Nesting | Putting elements inside other elements. |
| Parent | An element that holds other elements. |
| Server | A computer that sends data to clients. |
| Tag | A marker that starts or ends an element. |
| URL | The address of a web resource. |
| Void element | An element with no content and no closing tag. |

## Module 01 progress checklist (copy to `PROGRESS.md`)

```markdown
## Module 01: Foundations
- [ ] Lesson 1: How the web works
- [ ] Lesson 2: Setting up
- [ ] Lesson 3: Anatomy of an HTML document
- [ ] Lesson 4: Elements, tags, attributes, nesting
- [ ] Lesson 5: Comments, whitespace, entities
- [ ] Lesson 6: Hello World project
- [ ] Final quiz (8/10 or more)
- [ ] Project validated with W3C
- [ ] Project published on GitHub Pages
```

## Cheat sheet: Module 01

```html
<!DOCTYPE html>                      <!-- HTML5 doctype -->
<html lang="en">                     <!-- root + language -->
  <head>
    <meta charset="UTF-8" />         <!-- encoding -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Page title</title>        <!-- tab text -->
  </head>
  <body>
    <!-- comment -->
    <h1 id="main" class="big">Text</h1>   <!-- element + attributes -->
    <img src="a.jpg" alt="Description" /> <!-- void element -->
    &lt; &gt; &amp; &copy; &nbsp;          <!-- entities -->
  </body>
</html>
```

## Next module
Go to **Module 02: Text and Content**. You learn headings, paragraphs, text formatting, and lists.
