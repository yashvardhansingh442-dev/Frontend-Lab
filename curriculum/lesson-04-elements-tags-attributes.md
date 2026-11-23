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
