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
