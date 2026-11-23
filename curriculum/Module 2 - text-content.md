# Module 02: Text and Content

**Folder:** `02-text-content/`
**Level:** Beginner (with Advanced notes)
**Time:** 6 to 8 hours
**Writing style:** ASD-STE100 (Simplified Technical English)
**Prerequisite:** Module 01: Foundations

---

## Module Overview

### Goal
Learn to write text content with correct HTML. Use the right element for the right meaning. Build a personal bio page.

### What you learn
After this module, you can:
1. Use headings in a correct order.
2. Write paragraphs and control line breaks.
3. Format text with elements that have meaning.
4. Use quotes, citations, and horizontal rules.
5. Make ordered, unordered, and description lists.
6. Build a clean personal bio page.

### The main idea of this module
HTML describes **meaning**, not **appearance**.

- Use `<h1>` because the text is a main heading. Do not use it because the text is big.
- Use `<strong>` because the text is important. Do not use it because the text is bold.
- CSS controls the appearance. You learn CSS later.

### Folder structure for this module
```
02-text-content/
├── lesson-01-headings-paragraphs.md
├── lesson-02-text-formatting.md
├── lesson-03-breaks-rules-quotes.md
├── lesson-04-lists.md
├── lesson-05-project-bio-page.md
├── examples/
├── exercises/
└── project/
```

---

# Lesson 1: Headings and Paragraphs

## 1.1 Learning objectives
After this lesson, you can:
- Use `<h1>` to `<h6>` in the correct order.
- Write paragraphs with `<p>`.
- Explain why heading order is important.

## 1.2 Headings

HTML has six heading levels. `<h1>` is the highest level. `<h6>` is the lowest level.

```html
<h1>Main title</h1>
<h2>Section title</h2>
<h3>Subsection title</h3>
<h4>Level 4 heading</h4>
<h5>Level 5 heading</h5>
<h6>Level 6 heading</h6>
```

| Element | Use |
|---------|-----|
| `<h1>` | The main title of the page. |
| `<h2>` | A main section of the page. |
| `<h3>` | A part of an `<h2>` section. |
| `<h4>` to `<h6>` | Deeper levels. Rarely used. |

### Heading rules
1. Use **one** `<h1>` on each page.
2. Do not skip levels. Go from `<h2>` to `<h3>`, not from `<h2>` to `<h4>`.
3. Do not choose a heading level because of its size. Use CSS to change the size.
4. Write headings that describe the content that follows.

### Think of an outline
A heading structure is like the outline of a book.

```
h1  My Travel Blog
 ├── h2  Trip to Japan
 │     ├── h3  Tokyo
 │     └── h3  Kyoto
 └── h2  Trip to Italy
       ├── h3  Rome
       └── h3  Venice
```

```html
<h1>My Travel Blog</h1>
<h2>Trip to Japan</h2>
<h3>Tokyo</h3>
<h3>Kyoto</h3>
<h2>Trip to Italy</h2>
<h3>Rome</h3>
<h3>Venice</h3>
```

## 1.3 Why heading order is important

- **Screen reader users** move from heading to heading to find content. A wrong order confuses them.
- **Search engines** use headings to understand the page.
- **You** can read and change the page more easily.

## 1.4 Paragraphs

Use `<p>` for a block of text.

```html
<p>This is the first paragraph. It has two sentences.</p>
<p>This is the second paragraph.</p>
```

- The browser adds space before and after each paragraph.
- Each `<p>` starts on a new line.
- Do not use empty `<p></p>` elements to make space. Use CSS.

## 1.5 Try It

1. Make a file named `lesson-01.html`. Type the boilerplate from Module 01.
2. Add an `<h1>` with the title "My Favorite Things".
3. Add two `<h2>` sections: "Food" and "Music".
4. Add a `<p>` under each `<h2>`.
5. Open the file in the browser. Look at the sizes of the headings.
6. Open DevTools. Look at the Elements panel. Find the heading elements.

## 1.6 Advanced Note

- **Default styles:** Browsers use a built-in style sheet. It sets heading sizes and margins. You can change them with CSS.
- **Sectioning and heading levels:** The HTML standard has an outline algorithm for nested `<section>` elements. No browser uses it. Use explicit heading levels (`<h1>` to `<h6>`).
- **`<hgroup>`:** Use `<hgroup>` to group a heading with a subtitle or tagline.
  ```html
  <hgroup>
    <h1>HTML Course</h1>
    <p>Learn the web from the start</p>
  </hgroup>
  ```
- **`<p>` content model:** `<p>` can have only phrasing content (text and inline elements). A block element such as `<div>` closes the `<p>`.
- **Accessibility audit:** In Chrome, use the Lighthouse tool or the "Headings" list in a screen reader (NVDA, VoiceOver) to test your heading structure.
- **`<h1>` and SEO:** One `<h1>` is not a rule of the HTML standard. It is a best practice. It makes the main topic clear.

## 1.7 Exercises

1. Write a heading outline for a recipe page. Use `<h1>`, `<h2>`, and `<h3>`.
2. Find the error:
   ```html
   <h1>Title</h1>
   <h4>Small section</h4>
   <h2>Big section</h2>
   ```
3. Write 3 paragraphs about a hobby.
4. Open a news website. Use DevTools to list all `<h1>` and `<h2>` elements.
5. **Advanced:** Use `<hgroup>` for a title and a subtitle. Test the page with a screen reader.

## 1.8 Check your understanding
- How many `<h1>` elements must a page have?
- Why must you not skip heading levels?
- What does `<p>` do?
- How do you make a bigger gap between paragraphs?

---

# Lesson 2: Text Formatting

## 2.1 Learning objectives
After this lesson, you can:
- Use inline elements to give text meaning.
- Tell `<strong>` from `<b>`, and `<em>` from `<i>`.
- Show code, subscripts, and superscripts.

## 2.2 Formatting elements

| Element | Meaning | Default look |
|---------|---------|--------------|
| `<strong>` | Strong importance | Bold |
| `<em>` | Stress emphasis | Italic |
| `<mark>` | Highlighted for reference | Yellow background |
| `<sub>` | Subscript | Small and low |
| `<sup>` | Superscript | Small and high |
| `<code>` | Computer code | Monospace font |
| `<pre>` | Preformatted text | Monospace, keeps whitespace |
| `<small>` | Side comment or fine print | Smaller |
| `<del>` | Text that was deleted | Strikethrough |
| `<ins>` | Text that was added | Underline |
| `<abbr>` | Abbreviation | Dotted underline |
| `<kbd>` | Keyboard input | Monospace |
| `<b>` | Attention, no extra importance | Bold |
| `<i>` | Alternate voice (for example a foreign word) | Italic |

## 2.3 Examples

### Strong and emphasis
```html
<p><strong>Warning:</strong> Do not touch the wire.</p>
<p>I <em>really</em> like HTML.</p>
```

- `<strong>` = this text is important.
- `<em>` = say this word with stress. The meaning of the sentence can change.

```html
<p>I did not say <em>he</em> stole the money.</p>
<p>I did not say he <em>stole</em> the money.</p>
```
The stress is on a different word. The meaning is different.

### Mark
```html
<p>Remember to <mark>save your file</mark> before you close the editor.</p>
```

### Subscript and superscript
```html
<p>Water is H<sub>2</sub>O.</p>
<p>E = mc<sup>2</sup></p>
<p>This is the 1<sup>st</sup> lesson.</p>
```

### Code
```html
<p>Use the <code>&lt;p&gt;</code> element for a paragraph.</p>
```
Remember: use entities (`&lt;` and `&gt;`) to show angle brackets.

### Preformatted text
Use `<pre>` to keep spaces and line breaks. Put `<code>` inside `<pre>` for blocks of code.

```html
<pre><code>function hello() {
  console.log("Hello");
}</code></pre>
```

### Other useful elements
```html
<p>The price is <del>$20</del> <ins>$15</ins>.</p>
<p>Use <abbr title="HyperText Markup Language">HTML</abbr> for structure.</p>
<p>Press <kbd>Ctrl</kbd> + <kbd>S</kbd> to save.</p>
<p><small>Terms and conditions apply.</small></p>
```

## 2.4 Meaning versus appearance

| Do this | Do not do this |
|---------|----------------|
| `<strong>` for important text | `<b>` only to make text bold |
| `<em>` for stress | `<i>` only to make text italic |
| CSS `font-weight: bold` for style only | `<strong>` everywhere for style |

**Test:** Ask "Does this text have a meaning?" If yes, use the meaning element. If it is only style, use CSS.

## 2.5 Try It

1. Write a sentence with a chemical formula (for example CO<sub>2</sub>).
2. Write a math sentence with a power (for example x<sup>2</sup>).
3. Write a sentence that uses `<strong>`, `<em>`, and `<mark>`.
4. Write a `<pre>` block with a short poem. Keep the line breaks.
5. Write a keyboard instruction with `<kbd>`.

## 2.6 Advanced Note

- **Nesting inline elements:** You can nest them: `<strong><em>Very important</em></strong>`. Close them in the correct order.
- **`<b>` and `<i>`:** HTML5 gives them a meaning. `<b>` is for key words in a text. `<i>` is for technical terms, thoughts, or foreign words. Use `<strong>` and `<em>` first.
- **`<samp>`, `<var>`:** `<samp>` shows computer output. `<var>` shows a variable.
- **Screen readers:** Most screen readers do not announce `<strong>` and `<em>` by default. A user can change this setting. Do not use them as the only way to show meaning.
- **`<del>` and `<ins>`:** They accept `cite` and `datetime` attributes. Example: `<del datetime="2026-01-15">`.
- **`<abbr>`:** The `title` attribute gives the full form. Touch screens do not show a tooltip. Write the full form in the text the first time.
- **`<pre>` and long lines:** `<pre>` does not wrap lines. Use CSS `overflow-x: auto` to add a scroll bar.
- **`<time>`:** Use `<time datetime="2026-05-01">1 May 2026</time>` for dates. Module 07 teaches this.
- **Do not use removed elements:** `<font>`, `<center>`, `<big>`, and `<strike>` are obsolete.

## 2.7 Exercises

1. Make a "science notes" page with 3 formulas. Use `<sub>` and `<sup>`.
2. Make a short tutorial. It must contain `<kbd>`, `<code>`, and `<pre>`.
3. Rewrite this code with elements that have meaning:
   ```html
   <p><b>Danger!</b> Do <i>not</i> open the door.</p>
   ```
4. Make a price list. Use `<del>` for the old price and `<ins>` for the new price.
5. **Advanced:** Test `<strong>` and `<em>` with a screen reader. Write what you hear.

## 2.8 Check your understanding
- What is the difference between `<strong>` and `<b>`?
- Which element do you use for H₂O?
- When do you use `<pre>`?
- Why do you not use `<center>`?

---

# Lesson 3: Line Breaks, Horizontal Rules, Blockquotes, and Citations

## 3.1 Learning objectives
After this lesson, you can:
- Use `<br>` in the correct places.
- Use `<hr>` to show a change of topic.
- Quote text from other sources with `<blockquote>` and `<q>`.
- Give credit with `<cite>`.

## 3.2 Line breaks: `<br>`

`<br>` makes a new line inside a paragraph. It is a void element.

```html
<p>
  Ali Khan<br>
  12 Main Street<br>
  Delhi, India
</p>
```

**Use `<br>` for:** addresses, poems, song lines.

**Do not use `<br>` to:**
- Make space between paragraphs. Use separate `<p>` elements, or CSS.
- Make a list. Use `<ul>` or `<ol>`.

## 3.3 Horizontal rules: `<hr>`

`<hr>` shows a thematic break. This is a change of topic in the content.

```html
<h2>Chapter 1</h2>
<p>The story starts here.</p>
<hr>
<h2>Chapter 2</h2>
<p>The story continues.</p>
```

- `<hr>` is a void element.
- Use it for a change of topic. Do not use it only to make a decorative line. Use CSS borders for decoration.

## 3.4 Block quotes: `<blockquote>`

Use `<blockquote>` for a long quote from another source.

```html
<blockquote cite="https://example.com/speech">
  <p>The only way to do great work is to love what you do.</p>
</blockquote>
```

- The `cite` attribute gives the URL of the source. The browser does not show it.
- The browser indents the quote.
- Do not use `<blockquote>` only to indent text.

### Give credit to the source
Use `<figure>` and `<figcaption>` to show who said the quote.

```html
<figure>
  <blockquote>
    <p>Stay hungry. Stay foolish.</p>
  </blockquote>
  <figcaption>— Steve Jobs, <cite>Stanford Commencement Address</cite></figcaption>
</figure>
```

## 3.5 Short quotes: `<q>`

Use `<q>` for a short quote inside a sentence. The browser adds quotation marks.

```html
<p>She said, <q>I will be there at noon.</q></p>
```

Do not add your own quotation marks. The browser adds them.

## 3.6 Citations: `<cite>`

Use `<cite>` for the **title of a creative work**: a book, a film, a song, a paper.

```html
<p>I read <cite>The Pragmatic Programmer</cite> last year.</p>
```

**Important:** `<cite>` is for the title of the work. It is not for the name of a person.

| Element | Use |
|---------|-----|
| `<blockquote>` | A long quote (block) |
| `<q>` | A short quote (inline) |
| `<cite>` | The title of a work |
| `cite` attribute | The URL of the source |

## 3.7 Try It

1. Write your address with `<br>`.
2. Write a poem of 4 lines with `<br>`. Then write it again with `<pre>`. Compare the results.
3. Add an `<hr>` between two sections.
4. Write a quote with `<blockquote>`, `<figure>`, and `<figcaption>`.
5. Write a sentence with a short `<q>` quote.

## 3.8 Advanced Note

- **`<wbr>`:** This element gives the browser a place where it can break a long word or URL.
  ```html
  <p>https://example.com/very<wbr>/long<wbr>/path</p>
  ```
- **Language and quotes:** Quotation marks change with the `lang` attribute. English uses `“ ”`. French uses `« »`. Set `lang` on the element.
- **CSS quotes:** You can change the quotation marks with the CSS property `quotes`.
- **`<hr>` and accessibility:** Screen readers announce `<hr>` as a separator. Do not use many `<hr>` elements for decoration. Use `aria-hidden="true"` only if the line has no meaning (a better choice is a CSS border).
- **`<br>` and screen readers:** A screen reader may read the lines in `<br>` text as one block. For lists of items, use list elements.
- **`<address>`:** Use it for contact information of the author of the page. Module 07 teaches this.
- **Attribution rule:** The `cite` attribute is not visible. Always give the source in visible text also.

## 3.9 Exercises

1. Make a page with a favorite quote. Include the author and the title of the source.
2. Write a short paragraph that has two `<q>` quotes.
3. Write a postal address with `<br>`.
4. Find the error:
   ```html
   <p>I love <cite>Albert Einstein</cite>.</p>
   ```
   (Answer: `<cite>` is for a title of a work, not a person's name.)
5. **Advanced:** Write a French sentence with `<q lang="fr">`. Check the quotation marks.

## 3.10 Check your understanding
- When do you use `<br>`?
- What does `<hr>` mean in HTML5?
- What is the difference between `<blockquote>` and `<q>`?
- What does `<cite>` mark?

---

# Lesson 4: Lists

## 4.1 Learning objectives
After this lesson, you can:
- Make ordered, unordered, and description lists.
- Nest lists.
- Choose the correct list type.

## 4.2 Unordered list: `<ul>`

Use an unordered list when the order of items does not matter.

```html
<ul>
  <li>Apples</li>
  <li>Bread</li>
  <li>Milk</li>
</ul>
```

- `<ul>` = unordered list.
- `<li>` = list item.
- The default marker is a bullet.

## 4.3 Ordered list: `<ol>`

Use an ordered list when the order of items is important.

```html
<ol>
  <li>Open the file.</li>
  <li>Edit the text.</li>
  <li>Save the file.</li>
</ol>
```

### Attributes of `<ol>`

| Attribute | Purpose | Example |
|-----------|---------|---------|
| `start` | The first number | `<ol start="5">` |
| `reversed` | Counts down | `<ol reversed>` |
| `type` | Marker type: `1`, `a`, `A`, `i`, `I` | `<ol type="A">` |

The `value` attribute on an `<li>` sets the number of that item.

## 4.4 Description list: `<dl>`

Use a description list for terms and their descriptions.

```html
<dl>
  <dt>HTML</dt>
  <dd>The language for the structure of web pages.</dd>

  <dt>CSS</dt>
  <dd>The language for the appearance of web pages.</dd>
</dl>
```

| Element | Meaning |
|---------|---------|
| `<dl>` | Description list |
| `<dt>` | Description term |
| `<dd>` | Description details |

One term can have many descriptions. One description can have many terms.

## 4.5 Nested lists

Put a list **inside an `<li>`**. Do not put it directly inside `<ul>`.

**Correct:**
```html
<ul>
  <li>Fruits
    <ul>
      <li>Apple</li>
      <li>Banana</li>
    </ul>
  </li>
  <li>Vegetables</li>
</ul>
```

**Wrong:**
```html
<ul>
  <li>Fruits</li>
  <ul>
    <li>Apple</li>
  </ul>
</ul>
```

## 4.6 Choose the correct list

| Question | Answer | List |
|----------|--------|------|
| Does the order matter? | No | `<ul>` |
| Does the order matter? | Yes | `<ol>` |
| Is it a term and a description? | Yes | `<dl>` |

## 4.7 Try It

1. Make an unordered list of 5 things you like.
2. Make an ordered list of the steps to make tea.
3. Make an ordered list that starts at 10.
4. Make a description list with 3 programming terms.
5. Make a nested list: 2 hobbies, and 2 details under each hobby.

## 4.8 Advanced Note

- **Content model:** `<ul>` and `<ol>` can contain only `<li>` (and script-supporting elements). `<dl>` can contain `<dt>`, `<dd>`, and `<div>` groups.
- **Group in `<dl>`:** You can put a `<dt>` and its `<dd>` in a `<div>`. This helps with styling.
  ```html
  <dl>
    <div>
      <dt>Name</dt>
      <dd>Ali</dd>
    </div>
  </dl>
  ```
- **Navigation menus:** A navigation menu is a list of links. Developers use `<ul>` inside `<nav>`. You build this in Module 03.
- **CSS markers:** Use `list-style-type`, `list-style-position`, and `::marker` to change markers. Use `list-style: none` to remove them. In Safari, `list-style: none` can remove list semantics for VoiceOver. Add `role="list"` to keep them.
- **Counters:** CSS counters give more control over numbering.
- **`<menu>`:** `<menu>` is a semantic alternative to `<ul>` for toolbars. It is rare.
- **Do not use lists for layout:** Use a list only for list content.

## 4.9 Exercises

1. Make a shopping list (unordered).
2. Make a recipe with ingredients (unordered) and steps (ordered).
3. Make a glossary with `<dl>` of 5 terms.
4. Make a list of the top 5 movies. Use `<ol reversed>` to count down from 5 to 1.
5. Fix the error:
   ```html
   <ul>
     <li>One</li>
     <ul><li>Two</li></ul>
   </ul>
   ```
6. **Advanced:** Make a table of contents with a nested ordered list (3 levels).

## 4.10 Check your understanding
- When do you use `<ol>` and not `<ul>`?
- What are `<dt>` and `<dd>`?
- Where do you put a nested list?
- Which attribute makes a list start at 5?

---

# Lesson 5: Module Project - Personal Bio Page

## 5.1 Project goal
Build a personal bio page. Use all elements from this module. Use correct meaning, order, and structure.

## 5.2 Content plan

Your page must have these sections:

| Section | Content | Elements to use |
|---------|---------|-----------------|
| Title | Your name and one-line tagline | `<h1>`, `<p>` |
| About me | 2 to 3 paragraphs | `<h2>`, `<p>`, `<strong>`, `<em>` |
| Quick facts | Age, city, job or school | `<dl>` |
| Skills | A list of skills | `<ul>` |
| Learning path | Steps in order | `<ol>` |
| Favorite quote | A quote with its source | `<blockquote>`, `<figcaption>`, `<cite>` |
| Contact | Address or email text | `<br>` |
| Footer | Copyright | `&copy;` |

## 5.3 Requirements

### Level 1: Beginner (required)
- [ ] Correct document structure (Module 01)
- [ ] One `<h1>` and at least three `<h2>` headings
- [ ] No skipped heading levels
- [ ] At least 3 paragraphs
- [ ] At least one `<strong>` and one `<em>`
- [ ] One `<ul>` and one `<ol>`
- [ ] One `<dl>` for quick facts
- [ ] One `<blockquote>` with a visible source
- [ ] At least one `<hr>` between sections
- [ ] At least 3 comments in the code
- [ ] Code is indented with 2 spaces

### Level 2: Intermediate (recommended)
- [ ] Use `<mark>`, `<sub>` or `<sup>`, and `<code>` in correct places
- [ ] Use a nested list (for example skills by group)
- [ ] Use `<abbr>` with a `title` for one abbreviation
- [ ] Validate the file with `https://validator.w3.org`. Fix all errors.

### Level 3: Advanced (optional)
- [ ] Use `<hgroup>` for the name and tagline
- [ ] Use `<q>` with a `lang` attribute for one foreign phrase
- [ ] Check heading structure with Lighthouse or a screen reader
- [ ] Do not use `<b>`, `<i>`, `<br>`, or `&nbsp;` for layout

## 5.4 Project folder

```
project/
├── index.html
└── README.md
```

## 5.5 Steps

1. Write the outline first. List your headings on paper or in a comment.
2. Make `index.html` with the boilerplate.
3. Add the content, one section at a time.
4. Save and check the page after each section.
5. Read the page again. Check the meaning of each element.
6. Validate the page.
7. Write `README.md`. Add a short description of the project.
8. Commit and push:
   ```bash
   git add .
   git commit -m "Add Module 02 personal bio page"
   git push
   ```

## 5.6 Starter template

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Your Name | Personal Bio</title>
  </head>
  <body>
    <!-- Title -->
    <h1>Your Name</h1>
    <p><em>Your tagline here</em></p>
    <hr />

    <!-- About -->
    <h2>About Me</h2>
    <p>Write who you are. Use <strong>important words</strong> only where needed.</p>
    <p>Write what you do and what you like.</p>

    <!-- Quick facts -->
    <h2>Quick Facts</h2>
    <dl>
      <dt>City</dt>
      <dd>Your city</dd>
      <dt>Study or Work</dt>
      <dd>Your study or job</dd>
    </dl>

    <!-- Skills -->
    <h2>Skills</h2>
    <ul>
      <li>Skill one</li>
      <li>Skill two</li>
    </ul>

    <!-- Learning path -->
    <h2>My Learning Path</h2>
    <ol>
      <li>Learn HTML</li>
      <li>Learn CSS</li>
      <li>Learn JavaScript</li>
    </ol>

    <!-- Quote -->
    <h2>Favorite Quote</h2>
    <figure>
      <blockquote>
        <p>Your quote here.</p>
      </blockquote>
      <figcaption>— Author, <cite>Title of source</cite></figcaption>
    </figure>

    <hr />

    <!-- Contact -->
    <h2>Contact</h2>
    <p>
      Your Name<br />
      Your City, Your Country<br />
      Email: you@example.com
    </p>

    <!-- Footer -->
    <p><small>&copy; 2026 Your Name</small></p>
  </body>
</html>
```

## 5.7 Self-check list

1. Does the page have exactly one `<h1>`?
2. Do the headings go in order, with no skipped level?
3. Did you use `<strong>` and `<em>` for meaning?
4. Does each list use the correct type?
5. Does the quote show its source in visible text?
6. Does the validator show 0 errors?
7. Can you explain why you chose each element?

## 5.8 Grading guide (self-assessment)

| Area | Points |
|------|--------|
| Correct heading structure | 20 |
| Correct text elements (meaning) | 25 |
| Correct lists | 15 |
| Quote and citation | 10 |
| Clean code and comments | 10 |
| Validator shows 0 errors | 10 |
| Git commits and README | 10 |
| **Total** | **100** |

A score of 80 or more means you are ready for Module 03.

---

# Module 02 Review

## Final quiz

**Questions**

1. How many `<h1>` elements must a page have (best practice)?
2. Why must you not skip heading levels?
3. What is the difference between `<strong>` and `<b>`?
4. Which elements do you use for H₂O and x²?
5. When do you use `<pre>`?
6. What does `<hr>` mean in HTML5?
7. What is the difference between `<blockquote>` and `<q>`?
8. What does `<cite>` mark?
9. Which list do you use for steps that must be in order?
10. Where do you put a nested list?

**Answers**

1. One.
2. Screen readers, search engines, and readers use the heading order to understand the structure.
3. `<strong>` shows strong importance. `<b>` only draws attention, with no extra importance.
4. `<sub>` and `<sup>`.
5. When you must keep spaces and line breaks (for example code or ASCII art).
6. A thematic break (a change of topic).
7. `<blockquote>` is a long block quote. `<q>` is a short inline quote.
8. The title of a creative work.
9. `<ol>`.
10. Inside an `<li>` element.

## Common mistakes

| Mistake | Fix |
|---------|-----|
| Heading level chosen for size | Choose the level for structure. Use CSS for size. |
| Many `<h1>` elements | Use one `<h1>`. |
| Skipped heading level | Go one level at a time. |
| Empty `<p>` for space | Use CSS margin. |
| Many `<br>` for layout | Use separate elements and CSS. |
| `<b>` and `<i>` for meaning | Use `<strong>` and `<em>`. |
| `<cite>` for a person's name | Use `<cite>` for titles of works. |
| Own quotation marks inside `<q>` | The browser adds them. |
| List directly inside `<ul>` | Put the nested list inside an `<li>`. |
| `<ul>` for ordered steps | Use `<ol>`. |

## Glossary

| Term | Definition |
|------|------------|
| Block quote | A long quote from another source. |
| Citation | A reference to the source of a work. |
| Description list | A list of terms and their descriptions. |
| Heading | A title for a section of content. |
| Inline element | An element inside a line of text. |
| List item | One entry in a list (`<li>`). |
| Ordered list | A list where the order is important. |
| Semantic | Related to meaning. |
| Subscript | Small text below the line. |
| Superscript | Small text above the line. |
| Thematic break | A change of topic. |
| Unordered list | A list where the order is not important. |

## Module 02 progress checklist (copy to `PROGRESS.md`)

```markdown
## Module 02: Text and Content
- [ ] Lesson 1: Headings and paragraphs
- [ ] Lesson 2: Text formatting
- [ ] Lesson 3: Line breaks, rules, quotes, citations
- [ ] Lesson 4: Lists
- [ ] Lesson 5: Personal bio page project
- [ ] Final quiz (8/10 or more)
- [ ] Project validated with W3C
- [ ] Project pushed to GitHub
```

## Cheat sheet: Module 02

```html
<h1>Main title</h1>  <h2>Section</h2>  <h3>Subsection</h3>
<p>Paragraph</p>

<strong>important</strong>   <em>stress</em>   <mark>highlight</mark>
H<sub>2</sub>O   x<sup>2</sup>   <code>code</code>   <kbd>Ctrl</kbd>
<del>old</del>   <ins>new</ins>   <abbr title="Full form">ABBR</abbr>
<pre>keeps   spaces</pre>

line<br>break      <hr>

<blockquote cite="url"><p>Long quote</p></blockquote>
<q>Short quote</q>   <cite>Title of work</cite>

<ul><li>Unordered</li></ul>
<ol start="1" reversed><li>Ordered</li></ol>
<dl><dt>Term</dt><dd>Description</dd></dl>
```

## Next module
Go to **Module 03: Links and Navigation**. You learn anchors, paths, page jumps, and `<nav>` menus.
