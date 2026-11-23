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
