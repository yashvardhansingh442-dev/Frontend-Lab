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
