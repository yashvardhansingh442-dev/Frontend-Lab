# Module 05: Tables

**Folder:** `05-tables/`
**Level:** Beginner (with Advanced notes)
**Time:** 5 to 7 hours
**Writing style:** ASD-STE100 (Simplified Technical English)
**Prerequisites:** Modules 01 to 04

---

## Module Overview

### Goal
Learn to show data in rows and columns with correct HTML. Make tables that all users can read, also users of screen readers.

### What you learn
After this module, you can:
1. Build a table with `<table>`, `<tr>`, `<th>`, and `<td>`.
2. Group table parts with `<thead>`, `<tbody>`, `<tfoot>`, and `<caption>`.
3. Join cells with `colspan` and `rowspan`.
4. Make tables accessible with `scope`, `id`, and `headers`.
5. Know when to use a table and when not to use one.
6. Build a timetable or a price chart.

### The main idea of this module
A table is for **data** that has a relation in two directions (rows and columns). A table is **not** a tool for page layout.

Use this test: *"Can I describe each cell with its row header and its column header?"* If yes, use a table. If no, use another element.

### Folder structure for this module
```
05-tables/
├── lesson-01-table-structure.md
├── lesson-02-table-sections-caption.md
├── lesson-03-colspan-rowspan.md
├── lesson-04-accessible-tables.md
├── lesson-05-project-timetable-price-chart.md
├── examples/
├── exercises/
└── project/
```

---

# Lesson 1: Table, Row, and Cell Structure

## 1.1 Learning objectives
After this lesson, you can:
- Write a basic table.
- Tell `<th>` from `<td>`.
- Explain how HTML builds a table row by row.
- Decide when to use a table.

## 1.2 The basic elements

| Element | Name | Job |
|---------|------|-----|
| `<table>` | Table | The container for the whole table. |
| `<tr>` | Table row | One horizontal row. |
| `<th>` | Table header cell | A cell that is a **heading** for a row or a column. |
| `<td>` | Table data cell | A cell that holds **data**. |

## 1.3 Your first table

```html
<table>
  <tr>
    <th>Name</th>
    <th>Age</th>
    <th>City</th>
  </tr>
  <tr>
    <td>Ali</td>
    <td>21</td>
    <td>Delhi</td>
  </tr>
  <tr>
    <td>Sara</td>
    <td>23</td>
    <td>Mumbai</td>
  </tr>
</table>
```

**Result:**

| Name | Age | City |
|------|-----|------|
| Ali | 21 | Delhi |
| Sara | 23 | Mumbai |

## 1.4 How HTML builds a table

HTML has **rows**. It does **not** have columns in the code. Each `<tr>` is one row. Each `<th>` or `<td>` inside it is one cell. Cells in the same position in each row form a column.

```
<table>
 ├── <tr>  (row 1)
 │     ├── <th>   column 1
 │     ├── <th>   column 2
 │     └── <th>   column 3
 ├── <tr>  (row 2)
 │     ├── <td>   column 1
 │     ├── <td>   column 2
 │     └── <td>   column 3
 └── <tr>  (row 3) ...
```

**Rule:** Each row must have the same number of cells (unless you use `colspan` or `rowspan`).

## 1.5 `<th>` and `<td>`

- Use `<th>` for **headings**. The browser shows `<th>` bold and centered by default.
- Use `<td>` for **data**.
- A `<th>` can be in the top row (column heading) or in the first cell of a row (row heading).

```html
<table>
  <tr>
    <th></th>
    <th>Monday</th>
    <th>Tuesday</th>
  </tr>
  <tr>
    <th>Morning</th>
    <td>Math</td>
    <td>Physics</td>
  </tr>
  <tr>
    <th>Afternoon</th>
    <td>Art</td>
    <td>Sport</td>
  </tr>
</table>
```

Here the table has column headings (days) **and** row headings (times).

## 1.6 Borders

A table has no border by default. Use CSS to add borders.

```css
table { border-collapse: collapse; }
th, td { border: 1px solid #444; padding: 0.5rem 0.75rem; }
```

| CSS property | Job |
|--------------|-----|
| `border-collapse: collapse` | Joins the borders of cells into one line. |
| `padding` | Adds space inside cells. |
| `text-align` | Aligns text in cells (`left`, `center`, `right`). |

**Do not use** the old HTML attributes `border`, `cellpadding`, `cellspacing`, `align`, `bgcolor`, and `width` on `<table>`. They are obsolete. Use CSS.

## 1.7 When to use a table

| Use a table for | Do not use a table for |
|-----------------|------------------------|
| Timetables | Page layout (columns, sidebars) |
| Price lists | A list of links (use `<ul>`) |
| Sports results | A form layout (use CSS Grid or Flexbox) |
| Comparison of features | A single list of items (use `<ul>` or `<ol>`) |
| Statistics | Positioning images |

## 1.8 Try It

1. Make a table with 3 columns and 4 rows about your favorite movies (title, year, genre).
2. Use `<th>` for the headings.
3. Add CSS so that the table has borders and padding.
4. Make a multiplication table (1 to 5) with column headings **and** row headings.
5. Open DevTools. In the Elements panel, find the `<table>`. Look at the structure.

## 1.9 Advanced Note

- **Implicit `<tbody>`:** If you do not write `<tbody>`, the HTML parser adds one. In the DOM, the `<tr>` elements are children of `<tbody>`. This can change your CSS selectors (`table > tr` does not match). Write `<tbody>` yourself.
- **Table model:** The browser builds a **grid** of cells from rows. `colspan` and `rowspan` make some cells cover many grid positions.
- **`display: table`:** CSS can make any element act like a table (`display: table`, `table-row`, `table-cell`). This is a CSS layout tool. It does not give HTML table meaning for assistive tools.
- **Layout tables:** Old websites used tables for layout. This is bad practice. It breaks accessibility and responsive design. If you must see an old layout table, `role="presentation"` removes table meaning.
- **Content model:** `<table>` can contain, in this order: `<caption>`, `<colgroup>`, `<thead>`, `<tbody>` or `<tr>`, `<tfoot>`.
- **`<td>` content:** A cell can hold text, images, lists, links, and even nested tables. Keep cells simple.
- **Nested tables:** Avoid. They are hard to read with a screen reader.
- **Sorting and filtering:** Plain HTML has no sort feature. Use JavaScript, or a library, for interactive tables.
- **Data from JavaScript:** To build a table with JavaScript, use `table.insertRow()` and `row.insertCell()`, or build with a template.
- **`<th>` default style:** The browser makes `<th>` bold and centered. Reset this with CSS if needed.

## 1.10 Exercises

1. Make a table of 5 countries with name, capital, and population.
2. Make a table for a weekly workout plan with row headings (days) and column headings (exercise, time).
3. Find the error:
   ```html
   <table>
     <tr><th>Name</th><th>Age</th></tr>
     <tr><td>Ali</td></tr>
   </table>
   ```
4. Explain why you do not use a table for a page with a sidebar and a main column.
5. **Advanced:** Open the DevTools Console. Type `document.querySelector('table').rows.length`. Write the result. Then type `document.querySelector('table').rows[0].cells.length`.

## 1.11 Check your understanding
- What is the difference between `<th>` and `<td>`?
- Does HTML have a "column" element for cells?
- Why do we use CSS and not the `border` attribute?
- Name one good and one bad use of a table.

---

# Lesson 2: `<thead>`, `<tbody>`, `<tfoot>`, and `<caption>`

## 2.1 Learning objectives
After this lesson, you can:
- Divide a table into a header, a body, and a footer.
- Add a caption.
- Style table parts with CSS.
- Use `<colgroup>` and `<col>`.

## 2.2 Table sections

| Element | Job |
|---------|-----|
| `<caption>` | The title of the table. |
| `<thead>` | The header rows (column headings). |
| `<tbody>` | The main data rows. |
| `<tfoot>` | The footer rows (totals, notes). |

```html
<table>
  <caption>Monthly sales, 2026</caption>
  <thead>
    <tr>
      <th>Month</th>
      <th>Units</th>
      <th>Revenue</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>January</td>
      <td>120</td>
      <td>$2,400</td>
    </tr>
    <tr>
      <td>February</td>
      <td>150</td>
      <td>$3,000</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <th>Total</th>
      <td>270</td>
      <td>$5,400</td>
    </tr>
  </tfoot>
</table>
```

## 2.3 Rules

1. `<caption>` must be the **first** child of `<table>`.
2. Use only one `<thead>` and only one `<tfoot>`.
3. You can use many `<tbody>` elements to group rows.
4. In HTML5, `<tfoot>` can come after `<tbody>` (the modern way). Always put it after `<tbody>` in your code.
5. Each section contains `<tr>` elements.

## 2.4 `<caption>` vs a heading

| `<caption>` | `<h2>` before the table |
|-------------|-------------------------|
| Is part of the table. | Is outside the table. |
| Screen readers announce it when they enter the table. | Gives page structure. |
| Names the table. | Names a section. |

Use `<caption>` to name the table. You can use both.

```html
<table>
  <caption>
    Monthly sales, 2026
    <small>All values in US dollars.</small>
  </caption>
  ...
</table>
```

## 2.5 Why use sections?

1. **Meaning:** The browser and assistive tools know what is the header, the body, and the footer.
2. **Printing:** Browsers can repeat `<thead>` and `<tfoot>` on each page when a table is long.
3. **Scrolling:** With CSS, you can keep `<thead>` fixed while `<tbody>` scrolls.
4. **Styling:** You can style the header, body, and footer in a different way.

```css
thead { background: #1f2937; color: white; }
tbody tr:nth-child(even) { background: #f3f4f6; }
tfoot { font-weight: bold; border-top: 2px solid #444; }
caption { font-weight: bold; text-align: left; margin-bottom: 0.5rem; }
```

## 2.6 Multiple `<tbody>` elements

Use many `<tbody>` elements to group rows with a common topic.

```html
<table>
  <caption>Class timetable</caption>
  <thead>
    <tr><th>Time</th><th>Subject</th></tr>
  </thead>
  <tbody>
    <tr><th colspan="2">Monday</th></tr>
    <tr><td>09:00</td><td>Math</td></tr>
    <tr><td>10:00</td><td>Physics</td></tr>
  </tbody>
  <tbody>
    <tr><th colspan="2">Tuesday</th></tr>
    <tr><td>09:00</td><td>Art</td></tr>
  </tbody>
</table>
```

## 2.7 Column groups: `<colgroup>` and `<col>`

Use `<colgroup>` to style or set the width of **whole columns**.

```html
<table>
  <caption>Product list</caption>
  <colgroup>
    <col />
    <col style="background: #fef3c7" />
    <col span="2" />
  </colgroup>
  <thead>
    <tr><th>Item</th><th>Price</th><th>Stock</th><th>Rating</th></tr>
  </thead>
  <tbody>
    <tr><td>Pen</td><td>$1</td><td>200</td><td>4.5</td></tr>
  </tbody>
</table>
```

- `<colgroup>` comes after `<caption>` and before `<thead>`.
- `<col>` is a void element.
- `span="2"` makes one `<col>` apply to 2 columns.
- Only a few CSS properties work on `<col>`: `background`, `border`, `width`, `visibility`.

## 2.8 Try It

1. Take your table from Lesson 1. Add `<caption>`, `<thead>`, and `<tbody>`.
2. Add a `<tfoot>` with a total or a note.
3. Style the sections with CSS (a dark header, striped rows, a bold footer).
4. Make a table with 2 `<tbody>` elements and a group heading in each.
5. Add `<colgroup>` and color one column.

## 2.9 Advanced Note

- **Sticky header:** `thead th { position: sticky; top: 0; background: white; }` keeps the header visible when the page scrolls.
- **Scrollable body:** Wrap the table in a `div` with `overflow: auto` and a fixed `max-height`.
- **Responsive tables:** On small screens, a wide table can break the layout. Put the table in a container with `overflow-x: auto`. Make the container focusable: `<div class="table-wrap" tabindex="0" role="region" aria-labelledby="cap1">`.
  ```html
  <div class="table-wrap" role="region" aria-labelledby="cap1" tabindex="0">
    <table>
      <caption id="cap1">Wide data table</caption>
      ...
    </table>
  </div>
  ```
- **Stacked tables:** Some designs turn each row into a card on phones, with CSS. If you use `display: block` on table elements, you can remove table semantics in some browsers. Add ARIA roles (`role="table"`, `role="row"`, and so on) to keep them, and test with a screen reader.
- **Footer position (history):** In HTML 4, `<tfoot>` had to come before `<tbody>`. HTML5 allows both orders.
- **Print CSS:** Use `thead { display: table-header-group; }` and `tfoot { display: table-footer-group; }` to repeat the header and footer on every printed page.
- **`<caption>` and `aria-labelledby`:** `<caption>` already names the table. Do not repeat it with `aria-label`.
- **Number alignment:** Align numbers to the right, or use `font-variant-numeric: tabular-nums` so that digits line up.
- **`table-layout: fixed`:** The browser then uses the widths of the first row. It gives faster, more predictable layout for large tables.

## 2.10 Exercises

1. Make a price list with a caption, a header, 4 rows of data, and a footer with the total.
2. Make a table with 3 `<tbody>` groups (for example 3 school terms).
3. Find the error:
   ```html
   <table>
     <thead>...</thead>
     <caption>Title</caption>
     <tbody>...</tbody>
   </table>
   ```
4. Add CSS for striped rows, and align numbers to the right.
5. **Advanced:** Make a table with a sticky header. Put the table in a scrollable container with a visible focus outline.

## 2.11 Check your understanding
- Where must `<caption>` go?
- What is the job of `<tfoot>`?
- Can a table have more than one `<tbody>`?
- What does `<colgroup>` do?

---

# Lesson 3: `colspan` and `rowspan`

## 3.1 Learning objectives
After this lesson, you can:
- Join cells across columns with `colspan`.
- Join cells across rows with `rowspan`.
- Count cells correctly in a complex table.
- Know when to avoid cell spans.

## 3.2 `colspan`

`colspan` makes one cell **wider**. It covers many columns.

```html
<table>
  <tr>
    <th colspan="3">Student Report</th>
  </tr>
  <tr>
    <th>Name</th>
    <th>Math</th>
    <th>Science</th>
  </tr>
  <tr>
    <td>Ali</td>
    <td>90</td>
    <td>85</td>
  </tr>
</table>
```

The first row has **one** cell that covers **3** columns.

## 3.3 `rowspan`

`rowspan` makes one cell **taller**. It covers many rows.

```html
<table>
  <tr>
    <th>Day</th>
    <th>Time</th>
    <th>Subject</th>
  </tr>
  <tr>
    <th rowspan="2">Monday</th>
    <td>09:00</td>
    <td>Math</td>
  </tr>
  <tr>
    <!-- No first cell here. "Monday" covers it. -->
    <td>10:00</td>
    <td>Physics</td>
  </tr>
</table>
```

**Important:** In the second row, you write only **2** cells. The `rowspan` cell from the row above takes the first position.

## 3.4 How to count cells

For each row, add up the cells. Count a `colspan="n"` cell as `n`. Count cells that come from a `rowspan` above.

**Example:** A table with 4 columns.

```html
<table>
  <tr>
    <td colspan="2">A</td>   <!-- 2 columns -->
    <td>B</td>               <!-- 1 column -->
    <td rowspan="2">C</td>   <!-- 1 column, goes down 2 rows -->
  </tr>
  <tr>
    <td>D</td>               <!-- 1 column -->
    <td>E</td>               <!-- 1 column -->
    <td>F</td>               <!-- 1 column -->
    <!-- The 4th column is "C" from the row above -->
  </tr>
</table>
```

Grid:

```
| A (colspan 2) | B | C (rowspan 2) |
| D             | E | F |  <- C fills the 4th position
```

Row 1: 2 + 1 + 1 = 4. Row 2: 1 + 1 + 1 + 1 (from C) = 4.

## 3.5 Both together

```html
<table>
  <caption>Timetable with a break</caption>
  <thead>
    <tr>
      <th>Time</th>
      <th>Monday</th>
      <th>Tuesday</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>09:00</th>
      <td>Math</td>
      <td rowspan="2">Science lab (2 hours)</td>
    </tr>
    <tr>
      <th>10:00</th>
      <td>History</td>
    </tr>
    <tr>
      <th>11:00</th>
      <td colspan="2">Break</td>
    </tr>
  </tbody>
</table>
```

## 3.6 Common errors

| Error | Result |
|-------|--------|
| Too many cells in a row after `rowspan` | The table extends to the right and the layout breaks. |
| Too few cells | Empty space at the end of the row. |
| `colspan` bigger than the table | The browser adds extra columns. |
| `rowspan` goes past the end of the section | The browser cuts the span at the end of `<thead>`, `<tbody>`, or `<tfoot>`. |

**Tip:** Draw the table on paper first. Write the number of each cell in the grid.

## 3.7 When to avoid spans

Cell spans can make a table hard to use for screen reader users. Use spans only when the data truly needs them. If you can, use a simpler structure, or divide the data into two tables.

## 3.8 Try It

1. Make a table with a title cell that has `colspan="4"`.
2. Make a timetable where a 2-hour class uses `rowspan="2"`.
3. Make a table with a merged "Break" cell across all columns.
4. Draw the grid of this table on paper. Then write the code.
5. Remove a cell on purpose. See the effect in the browser.

## 3.9 Advanced Note

- **Limits:** `colspan` max is 1000. `rowspan` max is 65534. `rowspan="0"` means "to the end of the section" (limited support, avoid it).
- **Header groups:** For multi-level headings, use `colspan` on `<th>` with `scope="colgroup"` (see Lesson 4).
- **Grid inspection:** In Firefox DevTools, the Inspector can show table cell structure. In Chrome, use the Elements panel and hover over cells.
- **Accessibility:** Screen readers move through a table cell by cell. They announce the headers of each cell. Spanning cells can give wrong or too many announcements. Test with NVDA (Windows) or VoiceOver (macOS).
- **CSS Grid alternative:** For layouts that need complex spans but are not data, use CSS Grid (`grid-column`, `grid-row`). Do not use a table.
- **Calendars:** A month calendar is a good use of a table. Each cell holds a date. Use `<th scope="col">` for day names.
- **Parsing:** The HTML spec has a table-building algorithm. It handles spans by tracking "slots" in a grid. Errors do not stop the page. The browser fixes them in a predictable way, but the result can surprise you.
- **JavaScript API:** `cell.colSpan` and `cell.rowSpan` are DOM properties. `cell.cellIndex` is the position in its row (not the grid column when spans exist).

## 3.10 Exercises

1. Build this table in HTML:

   | | Mon | Tue |
   |---|---|---|
   | AM | Math (spans AM and PM on Mon) | Art |
   | PM | (covered) | Music |

2. Make a table with a heading that spans 3 columns, and sub-headings in the next row.
3. Count the columns and write the code for this layout: one cell on top that spans 2 columns, and two cells below.
4. Find the error:
   ```html
   <table>
     <tr><td rowspan="2">A</td><td>B</td></tr>
     <tr><td>C</td><td>D</td></tr>
   </table>
   ```
5. **Advanced:** Write JavaScript that logs `colSpan` and `rowSpan` of each cell in a table.

## 3.11 Check your understanding
- What does `colspan="3"` do?
- If a cell has `rowspan="2"`, how many cells do you write in the next row?
- How can you find a span error?
- When must you avoid spans?

---

# Lesson 4: Accessible Tables - `scope`, `id`, and `headers`

## 4.1 Learning objectives
After this lesson, you can:
- Explain how a screen reader reads a table.
- Use `scope` on `<th>`.
- Use `id` and `headers` for complex tables.
- Test a table for accessibility.

## 4.2 How a screen reader reads a table

A sighted user looks at the row and column headings. A screen reader user hears the headings **with each cell**.

For this table:

```html
<table>
  <tr>
    <th></th><th>Math</th><th>Science</th>
  </tr>
  <tr>
    <th>Ali</th><td>90</td><td>85</td>
  </tr>
</table>
```

The screen reader says: *"Ali, Science, 85."* It knows the headings because of the table structure. You must give it the right information.

## 4.3 Rules for accessible tables

1. Use `<th>` for **all** header cells. Do not use `<td>` with bold text.
2. Add a `<caption>`.
3. Use `scope` on `<th>`.
4. Use `<thead>`, `<tbody>`, and `<tfoot>`.
5. Do not use empty cells in headings without a reason. Write a hidden label if the top-left cell is empty.
6. Keep the table simple. Avoid spans and nested tables.
7. Never use a table for layout.

## 4.4 The `scope` attribute

`scope` tells which cells a `<th>` is a heading for.

| Value | Meaning |
|-------|---------|
| `col` | Heading for the cells **below** it (the column). |
| `row` | Heading for the cells **to the right** (the row). |
| `colgroup` | Heading for a group of columns. |
| `rowgroup` | Heading for a group of rows. |

```html
<table>
  <caption>Test scores</caption>
  <thead>
    <tr>
      <td></td>
      <th scope="col">Math</th>
      <th scope="col">Science</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Ali</th>
      <td>90</td>
      <td>85</td>
    </tr>
    <tr>
      <th scope="row">Sara</th>
      <td>95</td>
      <td>88</td>
    </tr>
  </tbody>
</table>
```

- Use `scope="col"` for column headings.
- Use `scope="row"` for row headings.
- The empty top-left cell is a `<td>` here. It is not a heading.

## 4.5 Two levels of headings

When headings have two levels, use `colgroup`.

```html
<table>
  <caption>Sales by region and quarter</caption>
  <thead>
    <tr>
      <td rowspan="2"></td>
      <th colspan="2" scope="colgroup">North</th>
      <th colspan="2" scope="colgroup">South</th>
    </tr>
    <tr>
      <th scope="col">Q1</th>
      <th scope="col">Q2</th>
      <th scope="col">Q1</th>
      <th scope="col">Q2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Shoes</th>
      <td>120</td><td>140</td><td>90</td><td>110</td>
    </tr>
  </tbody>
</table>
```

## 4.6 `id` and `headers` (complex tables)

For tables with irregular headings, link each data cell to its headings **by hand**.

1. Give each `<th>` a unique `id`.
2. In each `<td>`, write `headers="id1 id2"` (a list of heading IDs, separated by spaces).

```html
<table>
  <caption>Sales by region and quarter</caption>
  <thead>
    <tr>
      <td rowspan="2"></td>
      <th id="north" colspan="2">North</th>
      <th id="south" colspan="2">South</th>
    </tr>
    <tr>
      <th id="n-q1" headers="north">Q1</th>
      <th id="n-q2" headers="north">Q2</th>
      <th id="s-q1" headers="south">Q1</th>
      <th id="s-q2" headers="south">Q2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th id="shoes">Shoes</th>
      <td headers="shoes north n-q1">120</td>
      <td headers="shoes north n-q2">140</td>
      <td headers="shoes south s-q1">90</td>
      <td headers="shoes south s-q2">110</td>
    </tr>
  </tbody>
</table>
```

**When to use which:**

| Table type | Method |
|------------|--------|
| Simple (one row of column headings, one column of row headings) | `scope` |
| Two-level headings, regular | `scope` with `colgroup` / `rowgroup` |
| Very complex or irregular | `id` + `headers` |
| Too complex to read | **Split into two or more simple tables** |

## 4.7 Other accessibility tips

- **Caption:** Always add it. It tells the user what the table is about, before they read it.
- **Summary text:** For a complex table, write a short text summary before it. Say what the main result is.
- **Color:** Do not use color as the only way to show meaning. Add text or an icon.
- **Contrast:** Text must have enough contrast (4.5:1 for normal text).
- **Zoom:** Test the table at 200% zoom. It must stay usable.
- **Keyboard:** If the table scrolls, the scroll container must be reachable with the keyboard (`tabindex="0"`).
- **Empty cells:** Write "No data" or a dash with a hidden label, not a blank, if the meaning is unclear.

## 4.8 Hidden text for an empty heading

```html
<th scope="col"><span class="visually-hidden">Student name</span></th>
```

```css
.visually-hidden {
  position: absolute;
  width: 1px; height: 1px;
  overflow: hidden;
  clip: rect(0 0 0 0);
  white-space: nowrap;
}
```

## 4.9 Try It

1. Take a table from Lesson 1. Add `scope="col"` and `scope="row"`.
2. Add a `<caption>`.
3. Make a two-level heading table with `colgroup`.
4. Make the same table with `id` and `headers`.
5. If you can, turn on a screen reader (NVDA, VoiceOver, or the Narrator). Move through the table cell by cell. Listen to the headings.
6. Run Lighthouse. Check the Accessibility score.

## 4.10 Advanced Note

- **Accessibility tree:** Browsers build an accessibility tree. Table elements map to roles: `table`, `rowgroup`, `row`, `columnheader`, `rowheader`, `cell`. Look at it in Chrome DevTools > Accessibility.
- **`scope` on `<td>`:** Do not use it. It is obsolete in HTML5.
- **`abbr` on `<th>`:** `<th abbr="Q1">First quarter</th>` gives a shorter name to read many times.
- **`axis` attribute:** Obsolete. Do not use it.
- **`summary` attribute:** Obsolete in HTML5. Use `<caption>` or a text before the table.
- **ARIA table roles:** `role="table"`, `role="grid"`, and `role="treegrid"` are for **interactive** widgets built with `<div>`. For static data, native `<table>` is better. Use `role="grid"` only for tables with keyboard cell navigation (like a spreadsheet).
- **Sortable columns:** Use `aria-sort="ascending"` or `"descending"` on the `<th>`. Use a `<button>` inside `<th>` as the control.
- **Live updates:** If a table updates on its own, use `aria-live` with care. Do not announce each cell.
- **WCAG:** Success Criterion 1.3.1 (Info and Relationships) requires that relations in a table are available in code.
- **Testing tools:** axe DevTools, WAVE, and Lighthouse find missing headers and captions. A manual test with a screen reader finds the real problems.
- **Layout tables:** If you must keep a layout table, add `role="presentation"` (or `role="none"`). Then do not use `<th>`, `<caption>`, or `scope`.
- **Responsive patterns:** Some patterns turn tables into lists on phones. If you do this, check that the headings are still announced.

## 4.11 Exercises

1. Add `scope` to all headings in a table with 4 columns and 5 rows.
2. Write a table with two-level column headings and `scope="colgroup"`.
3. Write a complex table with `id` and `headers`.
4. List 3 accessibility problems in this table:
   ```html
   <table>
     <tr><td><b>Name</b></td><td><b>Age</b></td></tr>
     <tr><td>Ali</td><td>21</td></tr>
   </table>
   ```
5. Add `aria-sort` and a `<button>` to a table heading for a sortable column.
6. **Advanced:** Write a short report. Test a table with 2 screen readers. Write what each one says for the same cell.

## 4.12 Check your understanding
- What does `scope="col"` do?
- When do you use `id` and `headers`?
- Why do you use `<th>` and not bold `<td>`?
- What is the best choice for a very complex table?

---

# Lesson 5: Module Project - Timetable or Price Chart

## 5.1 Project goal
Build one of two projects. Use correct table structure, spans, and accessibility.

- **Option A:** A weekly **timetable** (school, gym, work, or study plan).
- **Option B:** A **price chart** (a product list, a service plan comparison, or a menu).

You can build both. This is good practice.

## 5.2 Option A: Timetable

### Content plan

| Part | Content |
|------|---------|
| Title | `<h1>` and a short introduction. |
| Table | Days in columns, time slots in rows. |
| Caption | "Weekly timetable for ..." |
| Merged cells | A break (`colspan`), a double class (`rowspan`). |
| Notes | A `<tfoot>` with a note or a legend. |

### Starter template

```html
<table>
  <caption>Weekly timetable, Semester 1</caption>
  <thead>
    <tr>
      <td></td>
      <th scope="col">Monday</th>
      <th scope="col">Tuesday</th>
      <th scope="col">Wednesday</th>
      <th scope="col">Thursday</th>
      <th scope="col">Friday</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">09:00 - 10:00</th>
      <td>Math</td>
      <td>Physics</td>
      <td>Math</td>
      <td rowspan="2">Lab (2 hours)</td>
      <td>Art</td>
    </tr>
    <tr>
      <th scope="row">10:00 - 11:00</th>
      <td>English</td>
      <td>History</td>
      <td>English</td>
      <td>Music</td>
    </tr>
    <tr>
      <th scope="row">11:00 - 11:30</th>
      <td colspan="5">Break</td>
    </tr>
    <tr>
      <th scope="row">11:30 - 12:30</th>
      <td>Physics</td>
      <td>Math</td>
      <td>Sport</td>
      <td>English</td>
      <td>Free study</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <td colspan="6">Note: Lab sessions are in Room 12.</td>
    </tr>
  </tfoot>
</table>
```

## 5.3 Option B: Price chart

### Content plan

| Part | Content |
|------|---------|
| Title | `<h1>` and a short introduction. |
| Table | At least 5 products or plans. Columns: name, description or features, price. |
| Caption | "Price list, effective ..." |
| Group rows | Two or more `<tbody>` elements with a group heading (for example categories). |
| Footer | A `<tfoot>` with a note about tax or shipping. |

### Starter template

```html
<table>
  <caption>Cafe menu and prices</caption>
  <colgroup>
    <col />
    <col />
    <col style="text-align: right" />
  </colgroup>
  <thead>
    <tr>
      <th scope="col">Item</th>
      <th scope="col">Description</th>
      <th scope="col">Price (USD)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="colgroup" colspan="3">Hot drinks</th>
    </tr>
    <tr>
      <th scope="row">Espresso</th>
      <td>Single shot</td>
      <td>2.50</td>
    </tr>
    <tr>
      <th scope="row">Latte</th>
      <td>Espresso with steamed milk</td>
      <td>3.80</td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <th scope="colgroup" colspan="3">Cold drinks</th>
    </tr>
    <tr>
      <th scope="row">Iced tea</th>
      <td>Lemon, no sugar</td>
      <td>3.00</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <td colspan="3">Prices include tax.</td>
    </tr>
  </tfoot>
</table>
```

## 5.4 Project folder

```
project/
├── timetable.html      (Option A)
├── price-chart.html    (Option B)
├── style.css           (optional)
└── README.md
```

## 5.5 Requirements

### Level 1: Beginner (required)
- [ ] Full HTML boilerplate and a clear `<title>`.
- [ ] One `<h1>`.
- [ ] A `<table>` with `<caption>`, `<thead>`, `<tbody>`, and `<tfoot>`.
- [ ] All heading cells use `<th>` with the correct `scope`.
- [ ] At least one `colspan` or one `rowspan`.
- [ ] Every row has the correct number of cells (check with the grid).
- [ ] Table has borders and padding with CSS (no obsolete attributes).
- [ ] No layout tables.
- [ ] Code is indented with 2 spaces.

### Level 2: Intermediate (recommended)
- [ ] Use more than one `<tbody>` with group headings (`scope="rowgroup"` or `scope="colgroup"`).
- [ ] Use `<colgroup>` and `<col>`.
- [ ] Add striped rows with `tbody tr:nth-child(even)`.
- [ ] Align numbers to the right.
- [ ] Wrap the table in a scrollable container with `tabindex="0"` and `role="region"` for small screens.
- [ ] Validate the page with `https://validator.w3.org`.

### Level 3: Advanced (optional)
- [ ] Use two-level headings with `id` and `headers` in at least one table.
- [ ] Use a sticky `<thead>`.
- [ ] Use `font-variant-numeric: tabular-nums` for number columns.
- [ ] Add print CSS so that the header repeats on each page.
- [ ] Test with a screen reader. Write a short report in `README.md`.
- [ ] Get a Lighthouse Accessibility score of 100.
- [ ] Build the table from a JavaScript array.

## 5.6 Steps

1. Choose Option A or Option B (or both).
2. Draw the table grid on paper. Mark merged cells.
3. Write the headings and the data. Check the number of columns in each row.
4. Write the HTML. Start with `<table>`, `<caption>`, and `<thead>`.
5. Add `<tbody>` and `<tfoot>`.
6. Add `scope` to each `<th>`.
7. Write the CSS for borders, padding, and stripes.
8. Test with the keyboard and, if you can, a screen reader.
9. Validate the page and run Lighthouse.
10. Write `README.md` with a short description.
11. Commit and push:
    ```bash
    git add .
    git commit -m "Add Module 05 table project"
    git push
    ```

## 5.7 Starter CSS

```css
body { font-family: system-ui, sans-serif; margin: 2rem; }

table { border-collapse: collapse; width: 100%; max-width: 900px; }
caption { font-weight: bold; text-align: left; margin-bottom: 0.5rem; font-size: 1.1rem; }
th, td { border: 1px solid #9ca3af; padding: 0.5rem 0.75rem; text-align: left; }
thead th { background: #1f2937; color: #fff; }
tbody tr:nth-child(even) { background: #f3f4f6; }
tbody th[scope="row"] { background: #e5e7eb; }
tfoot td { font-style: italic; }
td.num, th.num { text-align: right; font-variant-numeric: tabular-nums; }

.table-wrap { overflow-x: auto; }
.table-wrap:focus { outline: 3px solid #2563eb; }
```

## 5.8 Self-check list

1. Does the table have a `<caption>`?
2. Does each heading cell use `<th>` with `scope`?
3. Does each row fill the grid correctly?
4. Did you use `colspan` or `rowspan` only where needed?
5. Do you use CSS for the appearance (no `border` attribute)?
6. Can a screen reader user understand each cell with its headings?
7. Does the table work at 200% zoom and on a narrow screen?
8. Does the validator show 0 errors?

## 5.9 Grading guide (self-assessment)

| Area | Points |
|------|--------|
| Correct table structure (`thead`, `tbody`, `tfoot`, `caption`) | 25 |
| Correct `colspan` and `rowspan` | 15 |
| Accessibility (`th`, `scope`, `headers`) | 25 |
| CSS styling (no obsolete attributes) | 10 |
| Clean code and indentation | 5 |
| Validator shows 0 errors | 10 |
| Git commits and README | 10 |
| **Total** | **100** |

A score of 80 or more means you are ready for Module 06.

---

# Module 05 Review

## Final quiz

**Questions**

1. What is the difference between `<th>` and `<td>`?
2. Does HTML have a "column" element for cells? How does the browser make columns?
3. Where must `<caption>` be in a table?
4. What are the jobs of `<thead>`, `<tbody>`, and `<tfoot>`?
5. A row has a cell with `rowspan="2"`. How many cells do you write in the next row (for a 4-column table, if the other cells are normal)?
6. What does `scope="row"` do?
7. When do you use `id` and `headers`?
8. Why do you not use a table for page layout?
9. Which CSS property joins cell borders into one line?
10. What is the best method for a very complex table?

**Answers**

1. `<th>` is a heading cell. `<td>` is a data cell.
2. No. The browser makes columns from the cells in the same position in each row. (`<col>` and `<colgroup>` only apply style or width to columns.)
3. As the first child of `<table>`.
4. `<thead>` holds the header rows. `<tbody>` holds the data rows. `<tfoot>` holds the footer rows (totals, notes).
5. 3 cells. The `rowspan` cell fills one position.
6. It tells assistive tools that the `<th>` is a heading for all cells in that row.
7. For complex or irregular tables, where `scope` is not enough.
8. Layout tables break accessibility and responsive design. A table is for data only.
9. `border-collapse: collapse`.
10. Split the data into two or more simple tables.

## Common mistakes

| Mistake | Fix |
|---------|-----|
| `<td>` with bold text for headings | Use `<th>`. |
| No `<caption>` | Add one as the first child of `<table>`. |
| No `scope` on `<th>` | Add `scope="col"` or `scope="row"`. |
| Rows with a different number of cells | Count the grid. Fix cells and spans. |
| Extra cell after `rowspan` | Do not write the cell that the span covers. |
| `border`, `cellpadding`, `align` attributes | Use CSS. |
| Table used for layout | Use CSS Grid or Flexbox. |
| `<tfoot>` with no `<tbody>` | Always write `<tbody>`. |
| `<caption>` not first | Move it to the start. |
| Wide table breaks the page on a phone | Wrap it in a scrollable container. |
| Color as the only meaning | Add text or an icon. |
| Nested tables | Use simple tables. |
| Using `summary` or `axis` attributes | They are obsolete. Use `<caption>` and `scope`. |

## Glossary

| Term | Definition |
|------|------------|
| Caption | The title of a table (`<caption>`). |
| Cell | One box in a table (`<td>` or `<th>`). |
| Column group | A group of columns (`<colgroup>`). |
| `colspan` | An attribute that makes a cell cover many columns. |
| Data cell | A cell that holds data (`<td>`). |
| Grid | The rows and columns of a table. |
| Header cell | A cell that is a heading (`<th>`). |
| `headers` | An attribute on `<td>` that lists the IDs of its headings. |
| Layout table | A table that is used for page layout (bad practice). |
| Row | A horizontal line of cells (`<tr>`). |
| `rowspan` | An attribute that makes a cell cover many rows. |
| `scope` | An attribute on `<th>` that tells which cells it is a heading for. |
| Table section | `<thead>`, `<tbody>`, or `<tfoot>`. |

## Module 05 progress checklist (copy to `PROGRESS.md`)

```markdown
## Module 05: Tables
- [ ] Lesson 1: Table, row, cell structure
- [ ] Lesson 2: thead, tbody, tfoot, caption
- [ ] Lesson 3: colspan and rowspan
- [ ] Lesson 4: Accessible tables (scope, headers)
- [ ] Lesson 5: Timetable or price chart project
- [ ] Final quiz (8/10 or more)
- [ ] Table tested with keyboard and zoom
- [ ] Page validated with W3C
- [ ] Lighthouse accessibility check done
- [ ] Project pushed to GitHub
```

## Cheat sheet: Module 05

```html
<table>
  <caption>Table title</caption>
  <colgroup>
    <col /><col span="2" />
  </colgroup>
  <thead>
    <tr>
      <td></td>
      <th scope="col">Column 1</th>
      <th scope="col">Column 2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Row 1</th>
      <td>Data</td>
      <td>Data</td>
    </tr>
    <tr>
      <th scope="row">Row 2</th>
      <td colspan="2">Data across 2 columns</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <th scope="row">Total</th>
      <td colspan="2">Value</td>
    </tr>
  </tfoot>
</table>
```

| Element / attribute | Job |
|---------------------|-----|
| `<table>` | The table |
| `<caption>` | The title (first child) |
| `<thead>` `<tbody>` `<tfoot>` | Header, body, footer |
| `<tr>` | Row |
| `<th>` / `<td>` | Heading cell / data cell |
| `colspan` / `rowspan` | Cover many columns / rows |
| `scope` | `col`, `row`, `colgroup`, `rowgroup` |
| `id` + `headers` | Link a cell to its headings (complex tables) |
| `<colgroup>` / `<col>` | Style whole columns |

## Next module
Go to **Module 06: Forms**. You learn `<form>`, input types, labels, validation, and how to build a registration form.
