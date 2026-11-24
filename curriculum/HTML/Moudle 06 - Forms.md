# Module 06: Forms

**Folder:** `06-forms/`
**Level:** Beginner (with Advanced notes)
**Time:** 10 to 12 hours
**Writing style:** ASD-STE100 (Simplified Technical English)
**Prerequisites:** Modules 01 to 05

---

## Module Overview

### Goal
Learn to collect data from users with HTML forms. Make forms that are easy to use, safe to submit, and accessible to all users.

### What you learn
After this module, you can:
1. Build a form with `<form>`, `action`, and `method`.
2. Use the main input types.
3. Connect labels to fields with `for` and `id`.
4. Use `<textarea>`, `<select>`, `<optgroup>`, and `<datalist>`.
5. Use checkboxes and radio buttons correctly.
6. Use the three button types.
7. Use built-in validation.
8. Group fields with `<fieldset>` and `<legend>`.
9. Build a registration form and a contact form.

### The main idea of this module
A form has two parts:
1. **The front end (HTML):** the fields that the user sees and fills in.
2. **The back end (a server):** a program that receives the data and does something with it.

This course teaches the **front end**. HTML alone cannot save or send data to you. To process a form, you need a server, or a form service (for example Formspree or Netlify Forms). Module 10 shows how JavaScript can read form data in the browser.

**Warning:** Validation in HTML helps the user. It does **not** protect your server. A user can bypass it. A server must always check the data again.

### Folder structure for this module
```
06-forms/
├── lesson-01-form-action-method.md
├── lesson-02-input-types.md
├── lesson-03-labels.md
├── lesson-04-textarea-select-datalist.md
├── lesson-05-checkboxes-radios.md
├── lesson-06-buttons.md
├── lesson-07-validation.md
├── lesson-08-fieldset-legend.md
├── lesson-09-project-registration-contact-form.md
├── examples/
├── exercises/
└── project/
```

---

# Lesson 1: `<form>`, `action`, and `method`

## 1.1 Learning objectives
After this lesson, you can:
- Write a `<form>` element.
- Explain `action` and `method`.
- Tell `GET` from `POST`.
- Explain the `name` attribute and how the browser sends data.

## 1.2 The `<form>` element

`<form>` is the container for all form controls.

```html
<form action="/submit" method="post">
  <label for="name">Name</label>
  <input type="text" id="name" name="name" />
  <button type="submit">Send</button>
</form>
```

## 1.3 Form attributes

| Attribute | Job | Example |
|-----------|-----|---------|
| `action` | The URL that receives the data. | `action="/register"` |
| `method` | The HTTP method: `get` or `post`. | `method="post"` |
| `enctype` | How the browser encodes the data (for `post`). | `enctype="multipart/form-data"` |
| `target` | Where to show the response. | `target="_blank"` |
| `autocomplete` | Lets the browser fill in values. | `autocomplete="on"` |
| `novalidate` | Turns off built-in validation. | `novalidate` |

If you omit `action`, the form sends the data to the **current page URL**. If you omit `method`, the default is `get`.

## 1.4 `GET` and `POST`

| | `GET` | `POST` |
|---|---|---|
| Where is the data? | In the **URL** (`?name=Ali&age=21`) | In the **body** of the request |
| Visible in the address bar? | Yes | No |
| Can the user bookmark it? | Yes | No |
| Size limit | Yes (about 2000 characters) | Very large |
| Changes data on the server? | **No.** Only reads. | **Yes.** Can create or change data. |
| Use for | Search, filters | Login, registration, contact, upload |

**Rules:**
- Use `GET` for **search** and other actions that do not change data.
- Use `POST` for private data (passwords) and actions that change data.
- **Never** use `GET` to send a password. The URL goes into history, logs, and shared links.

### What `GET` looks like

```html
<form action="/search" method="get">
  <label for="q">Search</label>
  <input type="search" id="q" name="q" />
  <button type="submit">Go</button>
</form>
```

When the user types `html` and submits, the browser goes to:
```
/search?q=html
```

## 1.5 The `name` attribute

The browser sends only the controls that have a `name`. The data goes as **name=value** pairs.

```html
<input type="text" name="username" />
```

If the user types `ali21`, the browser sends `username=ali21`.

| Attribute | Job |
|-----------|-----|
| `name` | The key that the **server** uses. Required to send the data. |
| `id` | A unique ID in the page. Used for labels and CSS/JS. |

`name` and `id` are **not the same**. They can have the same text, but they have different jobs.

## 1.6 What happens when you submit

1. The user clicks the submit button (or presses `Enter` in a text field).
2. The browser checks the built-in validation.
3. If all fields are valid, the browser collects each `name=value` pair.
4. The browser sends them to `action` with the chosen `method`.
5. The server answers. The browser shows the response page.

## 1.7 Try It

1. Make a form with one text field named `q` and a submit button.
2. Set `method="get"` and `action="https://www.google.com/search"`. Search for something. Look at the URL.
3. Change to `method="post"`. Submit again. Look at the result.
4. Remove `name` from the input. Submit again. What is different in the URL?
5. Open DevTools > Network. Submit a form. Click the request. Look at the **Payload**.

## 1.8 Advanced Note

- **`enctype` values:**
  - `application/x-www-form-urlencoded` is the default. Data looks like `a=1&b=2`.
  - `multipart/form-data` is **required for file uploads**.
  - `text/plain` is for debugging only.
- **Safe and idempotent:** `GET` must be *safe* (no side effects) and *idempotent*. This is part of the HTTP standard. Search robots follow `GET` links. A `GET` form that deletes data is a serious bug.
- **CSRF:** A `POST` form on your site can be copied by an attacker. Servers use **CSRF tokens** (a hidden field with a secret value) to block this.
- **Hidden fields:** `<input type="hidden" name="token" value="abc123">` sends data that the user does not see. The user can still change it. Do not trust it.
- **`method="dialog"`:** A form inside `<dialog>` with `method="dialog"` closes the dialog and gives a return value. No server is used.
- **`form` attribute:** A control outside the form can belong to it: `<input form="form-id">`.
- **`formaction`, `formmethod`, `formenctype`, `formtarget`, `formnovalidate`:** These attributes on a submit button replace the form settings for that button.
- **`FormData` API:** In JavaScript, `new FormData(formElement)` reads all values. Use it with `fetch()` to send data without a page reload.
  ```js
  form.addEventListener('submit', async (e) => {
    e.preventDefault();
    const data = new FormData(form);
    await fetch('/register', { method: 'POST', body: data });
  });
  ```
- **Autofill:** `autocomplete` values such as `name`, `email`, `username`, `new-password`, `current-password`, `tel`, and `street-address` help browsers and password managers. Use them.
- **Enter key:** Pressing `Enter` in a text field submits the form if the form has a submit button (or only one text field).
- **Privacy law:** If you collect personal data, you must follow the law (for example GDPR in Europe). Tell users why you collect it.

## 1.9 Exercises

1. Write a login form with `method="post"`. It has a username and password.
2. Write a search form with `method="get"`. Describe the URL after a search for `cats`.
3. Explain why `GET` is wrong for a login form.
4. Find the problem: `<input type="text" id="email">` inside a form that must send the email.
5. **Advanced:** Write JavaScript that logs all `name=value` pairs of a form with `FormData`.

## 1.10 Check your understanding
- What does `action` do?
- What is the difference between `GET` and `POST`?
- Why does an input need a `name`?
- Which `enctype` do you need for a file upload?

---

# Lesson 2: Input Types

## 2.1 Learning objectives
After this lesson, you can:
- Use the main `<input>` types.
- Choose the correct type for each kind of data.
- Use common input attributes.

## 2.2 The `<input>` element

`<input>` is a **void element**. The `type` attribute decides how it looks and works. The default type is `text`.

```html
<input type="text" name="username" />
```

## 2.3 Main input types

| Type | Use | Mobile keyboard / UI |
|------|-----|----------------------|
| `text` | One line of text | Normal keyboard |
| `email` | An email address | Keyboard with `@` |
| `password` | A password (hidden characters) | Normal, characters hidden |
| `number` | A number | Number keyboard, up/down arrows |
| `tel` | A phone number | Phone keypad |
| `url` | A web address | Keyboard with `/` and `.com` |
| `search` | A search term | Search key, clear button |
| `date` | A date | Date picker |
| `time` | A time | Time picker |
| `datetime-local` | A date and a time | Date and time picker |
| `month` | A month and a year | Month picker |
| `week` | A week and a year | Week picker |
| `range` | A number on a slider | Slider |
| `color` | A color | Color picker |
| `file` | A file | File chooser |
| `hidden` | Data that the user does not see | None |

## 2.4 Examples

```html
<input type="text" name="fullname" />
<input type="email" name="email" />
<input type="password" name="password" />
<input type="number" name="age" min="0" max="120" step="1" />
<input type="tel" name="phone" />
<input type="url" name="website" />
<input type="date" name="birthday" />
<input type="time" name="alarm" />
<input type="range" name="volume" min="0" max="100" value="50" />
<input type="color" name="favorite-color" value="#3b82f6" />
<input type="file" name="photo" accept="image/*" />
```

## 2.5 Details of key types

### `email`
The browser checks for a simple `name@domain` pattern. Add `multiple` to allow a list separated by commas.

### `password`
The browser hides the characters. It does **not** encrypt anything. Use HTTPS. Use `autocomplete="new-password"` on a registration form and `autocomplete="current-password"` on a login form.

### `number`
```html
<input type="number" name="quantity" min="1" max="10" step="1" value="1" />
```
| Attribute | Job |
|-----------|-----|
| `min`, `max` | The smallest and largest value. |
| `step` | The size of each step. `step="0.01"` allows 2 decimal places. `step="any"` allows any value. |

Do not use `type="number"` for numbers that are **identifiers** (phone numbers, ZIP codes, credit card numbers). Use `type="text"` with `inputmode="numeric"`.

### `date`
```html
<input type="date" name="start" min="2026-01-01" max="2026-12-31" />
```
The value is always `YYYY-MM-DD`. The display depends on the user's locale.

### `range`
```html
<label for="vol">Volume</label>
<input type="range" id="vol" name="volume" min="0" max="100" step="5" value="50" />
```
A slider does not show its value. Use JavaScript or `<output>` to show it.

### `color`
```html
<input type="color" name="theme" value="#ff0000" />
```
The value is a `#rrggbb` string.

### `file`
```html
<input type="file" name="avatar" accept="image/png, image/jpeg" />
<input type="file" name="documents" multiple />
```
| Attribute | Job |
|-----------|-----|
| `accept` | A hint about the allowed file types. |
| `multiple` | Lets the user choose many files. |
| `capture` | On mobile, opens the camera (`user` or `environment`). |

The form must have `method="post"` and `enctype="multipart/form-data"`.

## 2.6 Common input attributes

| Attribute | Job |
|-----------|-----|
| `name` | The key for the data. |
| `id` | A unique ID (for the label). |
| `value` | The starting value. |
| `placeholder` | A hint inside the empty field. |
| `required` | The field must have a value. |
| `readonly` | The user cannot change it. It is sent. |
| `disabled` | The user cannot use it. It is **not** sent. |
| `autofocus` | Puts the cursor here at page load. Use with care. |
| `autocomplete` | A hint for the browser to fill in. |
| `maxlength`, `minlength` | Text length limits. |
| `size` | The visible width in characters. |
| `list` | Links to a `<datalist>`. |
| `inputmode` | The type of keyboard on mobile. |

## 2.7 `placeholder` is not a label

| Placeholder | Label |
|-------------|-------|
| Disappears when the user types. | Always visible. |
| Low contrast. | Normal contrast. |
| Not reliable for screen readers. | Reliable. |

**Rule:** Use a `<label>` for every field. Use `placeholder` only for an extra example, such as `name@example.com`.

## 2.8 Try It

1. Make a form with one field of each type: text, email, password, number, date, range, color, file.
2. Open the page on a phone, or in Chrome device mode. See how the keyboard changes.
3. Set `min`, `max`, and `step` on a number field. Try wrong values.
4. Add `accept="image/*"` to a file input. Try to choose a text file.
5. Add a `<output>` element to show the value of a range slider (use `oninput`).

## 2.9 Advanced Note

- **Unsupported types:** If a browser does not know a type, it uses `type="text"`. This is a safe fallback.
- **`inputmode`:** Gives the keyboard type without a validation rule. Values: `text`, `numeric`, `decimal`, `tel`, `email`, `url`, `search`, `none`.
- **`enterkeyhint`:** Changes the label of the Enter key on mobile (`go`, `search`, `send`, `next`, `done`).
- **`autocapitalize`, `autocorrect`, `spellcheck`:** Control text help on mobile and desktop. Turn them off for usernames and codes.
- **`type="number"` problems:** Users can scroll the mouse wheel to change the value by mistake. It accepts `e` (for exponents). It has poor screen reader support in some cases. For many cases, `type="text" inputmode="numeric" pattern="[0-9]*"` works better.
- **Date inputs:** Appearance and support differ between browsers. Test them. Provide a clear format hint. Consider a custom date picker only if you must.
- **Values in JS:** `input.value` (string), `input.valueAsNumber`, `input.valueAsDate`, `input.files` (FileList).
- **`<output>`:** Shows a calculation result. `<output name="result" for="a b">`.
- **`webkitdirectory`:** Lets users choose a whole folder (non-standard but widely supported).
- **File security:** `accept` is only a hint. A user can send any file. The server must check the file type, size, and content. Never trust the file name.
- **Password managers:** Use `autocomplete` values and normal field order (username, then password) so that they work well. Do not block paste on password fields.
- **Credit cards:** Use `autocomplete="cc-number"`, `cc-exp`, `cc-csc`. Better: use a payment provider's hosted fields. Do not handle card data yourself.
- **`<input type="image">`:** An image used as a submit button. Rare. Use `<button>` with `<img>`.
- **`type="datetime"`:** Removed. Use `datetime-local`.

## 2.10 Exercises

1. Choose the correct `type` for: a birth date, a website address, an age, a favorite color, a CV upload, a phone number.
2. Write a number field for a quantity from 1 to 10.
3. Write a file field that accepts only PDF files, and many files at once.
4. Explain why a ZIP code should not use `type="number"`.
5. **Advanced:** Write a range slider with a live `<output>` that shows its value. Use only HTML and one small `oninput` attribute (or an event listener).

## 2.11 Check your understanding
- Which type gives a number keyboard on a phone?
- What is the difference between `readonly` and `disabled`?
- Why is `placeholder` not a replacement for a label?
- Which `enctype` does a file upload need?

---

# Lesson 3: Labels and `for`/`id` Pairing

## 3.1 Learning objectives
After this lesson, you can:
- Connect a label to a field in two ways.
- Explain why labels are important.
- Write clear label text.

## 3.2 The `<label>` element

A `<label>` tells the user what a field is for. It also tells the screen reader.

### Method 1: `for` and `id` (explicit)

```html
<label for="email">Email address</label>
<input type="email" id="email" name="email" />
```

The value of `for` must be **exactly the same** as the `id` of the field.

### Method 2: Wrapping (implicit)

```html
<label>
  Email address
  <input type="email" name="email" />
</label>
```

### Which method to use?

| Method | Good | Bad |
|--------|------|-----|
| `for` + `id` | Works in all cases. Easy to style the label and the field in different places. | You must write 2 matching names. |
| Wrapping | Short code. | Some old assistive tools have problems. Harder to style. |

**Best practice:** Use `for` + `id`. You can also wrap and add `for`.

## 3.3 Why labels are important

1. **Screen readers** read the label when the user enters the field.
2. **Larger click area:** Clicking a label puts focus in the field (or toggles a checkbox). This helps users with a mouse, a touch screen, or limited motor control.
3. **Clear meaning** for all users.
4. **Required by accessibility standards** (WCAG 1.3.1, 3.3.2, 4.1.2).

## 3.4 Rules for labels

1. Every field must have a label (except buttons, which have their own text).
2. Put the label **before** the field for text inputs, and **after** it for checkboxes and radio buttons.
3. Each `id` must be unique in the page.
4. Write short, clear text. Use nouns: "Email address", not "Type your email address here".
5. Tell the user if the field is required.
6. Do not hide labels. If the design needs it, hide them with a **visually-hidden** CSS class (not `display: none`).
7. Do not use `placeholder` instead of a label.

## 3.5 Required field marks

```html
<label for="name">Full name <span aria-hidden="true">*</span><span class="visually-hidden">(required)</span></label>
<input type="text" id="name" name="name" required />
```

Or write at the top of the form: *"Fields with * are required."* Also write "(required)" or "(optional)" in the text where it helps.

## 3.6 Help text: `aria-describedby`

Use `aria-describedby` to connect extra help text to a field.

```html
<label for="pw">Password</label>
<input type="password" id="pw" name="pw" aria-describedby="pw-help" />
<p id="pw-help">Use at least 8 characters.</p>
```

The screen reader says the label, then the help text.

## 3.7 Try It

1. Make a form with 3 fields. Use `for` and `id` for each.
2. Click on a label. See the focus move to the field.
3. Change the `for` value so that it does not match the `id`. Click the label again. What happens?
4. Make a second form with wrapped labels.
5. Add help text to a password field with `aria-describedby`.
6. In DevTools > Accessibility, look at the name of each field.

## 3.8 Advanced Note

- **Accessible name computation:** A browser calculates the name of a field in this order: `aria-labelledby`, `aria-label`, native label (`<label>`), `title`, `placeholder`. Use the native label first.
- **`aria-labelledby`:** Use it when the label is made of text from many places. `aria-labelledby="id1 id2"`.
- **`aria-label`:** Gives a name with no visible text. Use it only when a visible label is not possible (for example a search box with only a magnifier button).
- **Many labels:** A field can have more than one `<label>`. `input.labels` in JavaScript returns them.
- **Label and click targets:** A label click triggers a `click` event on the field. Be careful with click handlers on both.
- **`aria-required` and `required`:** `required` gives the same information to assistive tools. Do not add `aria-required` to a field that has `required`.
- **Error messages:** Link error messages with `aria-describedby`, and set `aria-invalid="true"` on the field. Lesson 7 teaches this.
- **Label position:** Labels above fields are easiest to read on mobile. Side labels work on wide screens. Floating labels (that move on focus) can cause problems: test them well.
- **Do not use `<label>` as a heading** or as a title of a group. Use `<legend>` (Lesson 8).
- **Duplicate IDs:** A duplicate `id` breaks the label link. Use the W3C validator to find them.
- **Internationalization:** Labels must be translated. Set `lang` on the page and on parts in other languages.

## 3.9 Exercises

1. Write a label and a field for "Username" in both methods.
2. Explain why `<input id="a">` and `<label for="b">` do not work together.
3. Rewrite this to be accessible: `<input type="text" placeholder="Your name">`
4. Add help text for a field "Phone number" ("Include the country code").
5. **Advanced:** Use DevTools to read the accessible name of 5 fields. Find one that has no name. Fix it.

## 3.10 Check your understanding
- How do `for` and `id` work together?
- Why is a click on a label useful?
- Why is `placeholder` not enough?
- What does `aria-describedby` do?

---

# Lesson 4: `<textarea>`, `<select>`, `<optgroup>`, and `<datalist>`

## 4.1 Learning objectives
After this lesson, you can:
- Use `<textarea>` for long text.
- Use `<select>` for a list of choices.
- Group options with `<optgroup>`.
- Give suggestions with `<datalist>`.

## 4.2 `<textarea>`

`<textarea>` is for text with many lines.

```html
<label for="message">Message</label>
<textarea id="message" name="message" rows="5" cols="40" maxlength="500"></textarea>
```

| Attribute | Job |
|-----------|-----|
| `rows` | The visible number of lines. |
| `cols` | The visible width in characters. |
| `maxlength`, `minlength` | Length limits. |
| `placeholder` | A hint. |
| `wrap` | `soft` (default) or `hard`. |
| `required`, `readonly`, `disabled` | The same as for `<input>`. |

**Important:**
- `<textarea>` is **not** a void element. It has a closing tag.
- The text **between** the tags is the starting value. Whitespace is kept.
- Use CSS (`width`, `height`, `resize`) to control the size, not `rows` and `cols`.

## 4.3 `<select>`

`<select>` is a drop-down list. The user picks one option (or many).

```html
<label for="country">Country</label>
<select id="country" name="country">
  <option value="">Choose a country</option>
  <option value="in">India</option>
  <option value="us">United States</option>
  <option value="uk" selected>United Kingdom</option>
</select>
```

| Element / attribute | Job |
|---------------------|-----|
| `<option>` | One choice. |
| `value` | The data that is **sent**. If you omit it, the text is sent. |
| Text of `<option>` | What the user **sees**. |
| `selected` | Chooses this option at the start. |
| `disabled` | The user cannot choose this option. |
| `multiple` | Lets the user choose many options. |
| `size` | The number of visible rows (shows a list box). |
| `required` | The user must choose a real option. |

**Tip for `required`:** The first option must have `value=""`. Then `required` makes the user choose something else.

### Multiple selection

```html
<label for="skills">Skills (hold Ctrl or Cmd to choose many)</label>
<select id="skills" name="skills" multiple size="4">
  <option value="html">HTML</option>
  <option value="css">CSS</option>
  <option value="js">JavaScript</option>
  <option value="git">Git</option>
</select>
```

The browser sends one `skills=...` pair for each chosen option. For lists with a few choices, **checkboxes** are easier to use (Lesson 5).

## 4.4 `<optgroup>`

`<optgroup>` groups options under a heading.

```html
<label for="car">Car</label>
<select id="car" name="car">
  <optgroup label="Swedish cars">
    <option value="volvo">Volvo</option>
    <option value="saab">Saab</option>
  </optgroup>
  <optgroup label="German cars">
    <option value="mercedes">Mercedes</option>
    <option value="audi">Audi</option>
  </optgroup>
</select>
```

- The `label` attribute is the group heading. The user cannot select it.
- Add `disabled` to the `<optgroup>` to disable the whole group.

## 4.5 `<datalist>`

`<datalist>` gives **suggestions** for an `<input>`. The user can choose a suggestion **or type any value**.

```html
<label for="browser">Browser</label>
<input type="text" id="browser" name="browser" list="browsers" />
<datalist id="browsers">
  <option value="Chrome"></option>
  <option value="Firefox"></option>
  <option value="Safari"></option>
  <option value="Edge"></option>
</datalist>
```

- The `list` attribute of the input must be the same as the `id` of the `<datalist>`.
- `<datalist>` is not shown on the page.

## 4.6 Which control to use?

| Need | Use |
|------|-----|
| Long text | `<textarea>` |
| One choice from 2 to 5 options | Radio buttons |
| One choice from 6 or more options | `<select>` |
| Many choices from a short list | Checkboxes |
| Many choices from a long list | `<select multiple>` (or a custom control) |
| Free text with suggestions | `<input>` + `<datalist>` |
| Yes or no | A single checkbox |

## 4.7 Try It

1. Make a message box with `<textarea>` with a 200-character limit.
2. Make a country `<select>` with a first empty option and `required`.
3. Make a `<select>` with 2 `<optgroup>` elements.
4. Make a `<select multiple>` for skills.
5. Make a text input with a `<datalist>` of 5 suggestions. Type a value that is not in the list.
6. Submit a form with each control. In DevTools > Network, look at the data that the browser sends.

## 4.8 Advanced Note

- **Textarea auto-size:** The CSS property `field-sizing: content` lets a textarea grow with its content (support is growing). Before, developers used JavaScript.
- **Textarea and line breaks:** The browser sends line breaks as `\r\n`.
- **Character counters:** Use JavaScript with the `input` event. Announce the count with `aria-live="polite"` in a careful way (not at each key press).
- **Customizable select:** New CSS (`appearance: base-select`) allows you to style `<select>` and `<option>` fully, with support in recent Chromium browsers. Always test fallback behavior.
- **`<select>` styling:** Native `<select>` has limited styling in older browsers. Do not replace it with a custom `<div>` widget unless you can make it fully accessible. Native controls give keyboard and screen reader support for free.
- **`<hr>` in `<select>`:** You can use `<hr>` between options as a separator in modern browsers.
- **`<option label="...">`:** An old attribute. Do not use it.
- **Datalist limits:** The look of the suggestion list changes between browsers. Screen reader support is uneven. Datalist does not check that the value is in the list. The server must check.
- **`<datalist>` with `type`:** It also works with `date`, `range`, `color`, and `number` input types in some browsers (for example, tick marks on a range).
- **`<selectedcontent>` and `<option>` content:** New features allow rich content in options. They are not widely supported yet.
- **JS properties:** `select.value`, `select.selectedIndex`, `select.selectedOptions`, `select.options`.
- **Autocomplete for addresses:** Use `autocomplete="country"`, `address-level1`, `postal-code` to help browsers fill in the data.
- **Combobox pattern:** An accessible custom autocomplete uses the ARIA `combobox` pattern with many details. Use a tested library.

## 4.9 Exercises

1. Make a feedback form with a `<textarea>` for comments (required, 20 to 300 characters).
2. Make a drop-down for "Month of birth" with 12 options and a placeholder option.
3. Make a `<select>` for foods in 3 groups (fruit, vegetables, grains).
4. Make an input for "City" with a datalist of 5 cities.
5. Find the problem: `<option>India<option>USA</select>` (list 2 problems).
6. **Advanced:** Add a live character counter below a `<textarea>`. Use `aria-live="polite"`. Make sure that it does not announce at every key press.

## 4.10 Check your understanding
- Is `<textarea>` a void element?
- What is the difference between the `value` and the text of an `<option>`?
- What does `<optgroup>` do?
- What is the difference between `<select>` and `<datalist>`?

---

# Lesson 5: Checkboxes and Radio Buttons

## 5.1 Learning objectives
After this lesson, you can:
- Use checkboxes for many choices or yes/no.
- Use radio buttons for one choice.
- Group radio buttons by `name`.
- Understand what the browser sends.

## 5.2 Checkboxes

A checkbox is a **yes/no** choice. Each checkbox is independent.

```html
<input type="checkbox" id="newsletter" name="newsletter" value="yes" />
<label for="newsletter">Send me the newsletter</label>
```

| Attribute | Job |
|-----------|-----|
| `name` | The key. |
| `value` | The value sent **if checked**. The default is `on`. |
| `checked` | The checkbox is on at the start. |
| `required` | The user must check it (for example "I agree"). |
| `disabled` | The user cannot change it. |

**Important:** An **unchecked** checkbox sends **nothing**. The server does not see the name.

### A group of checkboxes

Give the same `name` to related checkboxes. Each one has a different `value`.

```html
<fieldset>
  <legend>Which languages do you know?</legend>
  <input type="checkbox" id="lang-html" name="languages" value="html" />
  <label for="lang-html">HTML</label>

  <input type="checkbox" id="lang-css" name="languages" value="css" checked />
  <label for="lang-css">CSS</label>

  <input type="checkbox" id="lang-js" name="languages" value="js" />
  <label for="lang-js">JavaScript</label>
</fieldset>
```

If the user checks CSS and JavaScript, the browser sends `languages=css&languages=js`.

## 5.3 Radio buttons

Radio buttons let the user choose **only one** option from a group.

```html
<fieldset>
  <legend>Choose your plan</legend>

  <input type="radio" id="plan-free" name="plan" value="free" checked />
  <label for="plan-free">Free</label>

  <input type="radio" id="plan-pro" name="plan" value="pro" />
  <label for="plan-pro">Pro</label>

  <input type="radio" id="plan-team" name="plan" value="team" />
  <label for="plan-team">Team</label>
</fieldset>
```

### How the group works
- All radio buttons with the **same `name`** are one group.
- The user can choose only one in the group.
- Each radio button needs a **different `value`**.
- The browser sends `plan=pro` (only the chosen one).
- If none is chosen, nothing is sent.

### Rules for radio buttons

1. Always set a **default** (`checked`) if a choice is required, or use `required` on at least one button in the group.
2. Use at least 2 options.
3. A user cannot un-choose a radio button after choosing. If the user must be able to choose "none", add a "None" option.
4. Use `<fieldset>` and `<legend>` for the group (Lesson 8).

## 5.4 Checkbox or radio? Quick rule

| Question | Use |
|----------|-----|
| Can the user choose **many**? | Checkboxes |
| Can the user choose **only one**? | Radio buttons |
| Is it a single yes/no (for example terms of service)? | One checkbox |

## 5.5 Keyboard use

| Control | Keys |
|---------|------|
| Checkbox | `Tab` to move, `Space` to check or uncheck |
| Radio group | `Tab` to enter the group, **arrow keys** to change the choice |

A radio group is **one** tab stop. This is the correct behavior. Do not try to change it.

## 5.6 Try It

1. Make a checkbox group of 4 hobbies. Check 2 of them. Submit with `GET`. Look at the URL.
2. Make a radio group of 3 sizes (small, medium, large). Choose one. Look at the URL.
3. Remove the shared `name` from the radio buttons. What changes?
4. Add a required checkbox, "I accept the terms". Try to submit without it.
5. Use only the keyboard to change radio buttons.

## 5.7 Advanced Note

- **Indeterminate state:** A checkbox can be "indeterminate" (a dash) with JavaScript only: `checkbox.indeterminate = true`. It is used for "select all" boxes when some items are checked. It is not sent to the server.
- **Select all pattern:** A parent checkbox controls child checkboxes. Set `indeterminate` when only some are on. Update with JavaScript.
- **Switch role:** `<input type="checkbox" role="switch">` makes a toggle switch for assistive tools. Use it only for settings that take effect at once.
- **Hidden fallback for unchecked boxes:** Put `<input type="hidden" name="newsletter" value="no">` **before** the checkbox with the same name. The server then gets `no` when the box is unchecked, and the last value (`yes`) when checked. Many frameworks use this pattern.
- **Custom checkbox styling:** Use `accent-color: #3b82f6;` for a simple color change. For a full custom look, use `appearance: none` and style with `::before` or `:checked`. Keep the real `<input>` in the page (do not use `display: none`, because that removes keyboard focus).
- **Touch targets:** Make the label and control at least 24 by 24 CSS pixels (WCAG 2.2). 44 by 44 is better on mobile.
- **`:checked`, `:indeterminate`, `:required`, `:valid`, `:invalid`, `:disabled`:** These CSS pseudo-classes help you style form states.
- **Radio group and `required`:** One `required` radio button makes the whole group required.
- **`form.elements[name]`:** For radio buttons and grouped checkboxes, this returns a collection. Use `RadioNodeList.value` to read the chosen value of a radio group.
- **Reset behavior:** On `reset`, the browser restores the `checked` attribute state, not the last state before.
- **Choice cards:** If you design a large "card" for each option, put the whole card in a `<label>`. Keep the input inside so that a click selects it.

## 5.8 Exercises

1. Make a survey question "How did you hear about us?" with 4 radio options.
2. Make a "Choose your toppings" group with 5 checkboxes. Make 2 checked by default.
3. Write a single required checkbox for "I am over 18".
4. Explain what the server receives if the user chooses nothing in a radio group and a checkbox group.
5. **Advanced:** Build a "select all" checkbox that controls 4 child checkboxes. Use the `indeterminate` state.

## 5.9 Check your understanding
- Which control allows only one choice?
- What does an unchecked checkbox send to the server?
- What makes radio buttons a group?
- Which keys change the choice in a radio group?

---

# Lesson 6: Buttons - `submit`, `reset`, and `button`

## 6.1 Learning objectives
After this lesson, you can:
- Use `<button>` and `<input>` buttons.
- Tell `submit`, `reset`, and `button` apart.
- Avoid common button errors.

## 6.2 The `<button>` element

```html
<button type="submit">Send</button>
<button type="reset">Clear</button>
<button type="button">Show help</button>
```

| `type` | Job |
|--------|-----|
| `submit` | Sends the form. **This is the default** inside a form. |
| `reset` | Sets all fields back to their starting values. |
| `button` | Does nothing by itself. Use it with JavaScript. |

**Important:** If you omit `type`, a `<button>` inside a form is a **submit** button. This can cause errors for buttons that must not submit. Always write `type`.

## 6.3 `<button>` vs `<input type="submit">`

```html
<button type="submit">Create <strong>account</strong></button>
<input type="submit" value="Create account" />
```

| | `<button>` | `<input type="submit">` |
|---|---|---|
| Content | Text, images, icons, HTML | Text only (`value`) |
| Style with CSS | Easy (with `::before`, `::after`) | Limited |
| Closing tag | Yes | No (void element) |

**Best practice:** Use `<button>`.

## 6.4 Button text

- Write a clear action: "Create account", "Send message", "Download report".
- Avoid "Submit", "OK", and "Click here".
- Make the text match the result.

## 6.5 Buttons and links

| Use a `<button>` to... | Use an `<a>` to... |
|------------------------|--------------------|
| Do an action (send, open a dialog, toggle) | Go to another page or place |
| Run JavaScript | Give a URL |

Do not use `<a href="#">` as a button. Do not use `<div>` as a button. A real `<button>` gives keyboard and screen reader support for free.

## 6.6 `reset` buttons: use with care

A `reset` button deletes everything that the user typed. A user can click it by mistake. Many designs do not use it. If you use it, separate it from the submit button, and give it a clear label.

## 6.7 Button states

```html
<button type="submit" disabled>Send</button>
```

- `disabled` stops clicks and removes the button from the tab order.
- A disabled submit button can confuse users (they do not know why). Prefer to leave it **enabled** and show clear error messages after the click.

## 6.8 Overriding form settings

A button can replace some settings of its form.

```html
<form action="/save" method="post">
  ...
  <button type="submit">Save</button>
  <button type="submit" formaction="/save-draft">Save as draft</button>
  <button type="submit" formnovalidate>Save without checking</button>
</form>
```

| Attribute | Replaces |
|-----------|----------|
| `formaction` | `action` |
| `formmethod` | `method` |
| `formenctype` | `enctype` |
| `formtarget` | `target` |
| `formnovalidate` | validation |

## 6.9 Try It

1. Make a form with a submit button and a reset button. Type some text. Click each button.
2. Remove `type` from a button that is not meant to submit. Click it. What happens?
3. Make a `type="button"` that shows an alert with `onclick`.
4. Make a button with an icon and text (inline SVG with `aria-hidden="true"`).
5. Add a second submit button with `formaction`.

## 6.10 Advanced Note

- **`name` and `value` on buttons:** A submit button with a `name` sends its `value` **if it was used to submit**. This tells the server which button the user clicked.
  ```html
  <button type="submit" name="action" value="save">Save</button>
  <button type="submit" name="action" value="delete">Delete</button>
  ```
- **Implicit submission:** When the user presses `Enter` in a text field, the browser "clicks" the **first** submit button in the form. Put the main action first in the code.
- **`form` attribute:** `<button form="my-form">` works outside the form.
- **Double submit:** Users can click twice. Disable the button after the first click (with JavaScript, in the `submit` event), and make the server safe against duplicates.
- **Loading state:** For slow requests, show progress with text. Use `aria-busy="true"` on the form or an `aria-live` region.
- **`<button>` content model:** It can have phrasing content only. Do not put links, other buttons, or inputs inside it.
- **Toggle buttons:** Use `aria-pressed="true|false"` on a `<button type="button">` for on/off buttons (for example "Bold").
- **Popover and dialog buttons:** `popovertarget` and `commandfor` (new) let a button control a popover or dialog with no JavaScript.
- **`<input type="button">` and `<input type="reset">`:** They also exist. Prefer `<button>`.
- **Focus styles:** Never remove the focus outline (`outline: none`) without a visible replacement. Use `:focus-visible`.
- **Touch size:** Make buttons at least 44 by 44 CSS pixels on mobile.
- **Security:** Use `POST` and CSRF protection for buttons that change data.

## 6.11 Exercises

1. Write one form with Save, Save as draft, and Clear buttons. Use correct `type` values.
2. Explain why `<button>Click</button>` inside a form can be a problem.
3. Write a "Delete" and a "Save" submit button that send their `value` in `name="action"`.
4. Explain when to use `<a>` and when to use `<button>`.
5. **Advanced:** Write JavaScript that disables the submit button after the first submit and changes its text to "Sending...".

## 6.12 Check your understanding
- What is the default `type` of a `<button>` in a form?
- What does `type="reset"` do?
- Why is `<button>` better than `<div>` for a button?
- What does `formaction` do?

---

# Lesson 7: Built-in Validation

## 7.1 Learning objectives
After this lesson, you can:
- Use `required`, `pattern`, `min`, `max`, `minlength`, and `maxlength`.
- Understand the type-based checks.
- Style valid and invalid states.
- Write clear error messages.

## 7.2 What is validation?

Validation checks that the data is **correct** and **complete** before it is sent. The browser can do many checks with HTML attributes. No JavaScript is needed.

If a field is invalid, the browser:
1. Stops the submit.
2. Moves focus to the first invalid field.
3. Shows a message.

## 7.3 Validation attributes

| Attribute | Works on | Rule |
|-----------|----------|------|
| `required` | Most fields | The field must have a value. |
| `minlength` | text, textarea, email, password, url, tel, search | The minimum number of characters. |
| `maxlength` | The same | The maximum number of characters. |
| `min` | number, range, date, time, month, week | The smallest value. |
| `max` | The same | The largest value. |
| `step` | The same | The allowed step. |
| `pattern` | text, email, password, url, tel, search | A regular expression that the **whole** value must match. |
| `type` | email, url, number, date | Built-in format check. |
| `multiple` | email, file | Allows many values. |

## 7.4 Examples

```html
<!-- Required -->
<input type="text" name="name" required />

<!-- Length -->
<input type="password" name="pw" minlength="8" maxlength="64" required />

<!-- Number range -->
<input type="number" name="age" min="18" max="99" required />

<!-- Date range -->
<input type="date" name="start" min="2026-01-01" max="2026-12-31" />

<!-- Type check -->
<input type="email" name="email" required />
<input type="url" name="site" />

<!-- Pattern: exactly 6 digits -->
<input type="text" name="zip" pattern="[0-9]{6}" inputmode="numeric" title="Six digits" />
```

## 7.5 The `pattern` attribute

`pattern` uses a **regular expression** (regex).

| Pattern | Meaning |
|---------|---------|
| `[0-9]{6}` | Exactly 6 digits |
| `[A-Za-z]+` | One or more letters |
| `[A-Za-z0-9_]{3,16}` | 3 to 16 letters, digits, or underscores |
| `\+?[0-9 ]{10,15}` | A phone number with an optional `+` |
| `.{8,}` | At least 8 characters of any kind |

**Rules:**
- The pattern must match the **whole** value. You do not write `^` and `$`.
- Add a `title` that explains the format. Browsers show it in the error message.
- Pattern is checked only if the field is not empty. Use `required` to force a value.
- `pattern` does not work on `number`, `date`, or `range`.

## 7.6 Style valid and invalid states

CSS pseudo-classes:

| Pseudo-class | Matches |
|--------------|---------|
| `:required` / `:optional` | Required or optional fields |
| `:valid` / `:invalid` | Fields that pass or fail validation |
| `:in-range` / `:out-of-range` | A number or date inside or outside `min` and `max` |
| `:user-valid` / `:user-invalid` | Like `:valid` and `:invalid`, but only **after the user has used the field** |

**Problem:** `:invalid` shows red on an empty required field at page load, before the user types. Use `:user-invalid` to avoid it.

```css
input:user-invalid { border: 2px solid #b91c1c; }
input:user-valid   { border: 2px solid #15803d; }
```

For older browsers, add a class with JavaScript after the first `blur`.

## 7.7 Error messages

The default browser messages are not always clear, and the browser language sets them. You have two choices:

### Choice 1: Use the default
Add a good `title` for patterns. Use clear labels.

### Choice 2: Write custom messages
Use the Constraint Validation API.

```html
<label for="email">Email</label>
<input type="email" id="email" name="email" required aria-describedby="email-error" />
<p id="email-error" class="error" role="alert" hidden></p>
```

```js
const email = document.getElementById('email');
const error = document.getElementById('email-error');

email.addEventListener('input', () => {
  if (email.validity.valueMissing) {
    email.setCustomValidity('Please enter your email address.');
  } else if (email.validity.typeMismatch) {
    email.setCustomValidity('Please enter an address like name@example.com.');
  } else {
    email.setCustomValidity('');
  }
});
```

### Good error messages
1. Say **what** is wrong and **how** to fix it.
2. Use simple words. No codes.
3. Show the message **near** the field.
4. Do not use color alone. Add text.
5. Link the message to the field with `aria-describedby`. Set `aria-invalid="true"` when the field is invalid.

| Bad | Good |
|-----|------|
| `Invalid input` | `Enter a 6-digit ZIP code, for example 110001.` |
| `Error 5` | `Choose a password with at least 8 characters.` |

## 7.8 Turn off validation

```html
<form novalidate> ... </form>
<button type="submit" formnovalidate>Save draft</button>
```

Use `novalidate` only if you write your own validation with JavaScript.

## 7.9 Try It

1. Make a form with: required name, email, password (8 to 20 characters), age (18 to 99), and ZIP (6 digits).
2. Try to submit empty. See the messages.
3. Try wrong values in each field. See the messages.
4. Add `title` to the pattern field. See the new message.
5. Add CSS for `:user-invalid` and `:user-valid`.
6. Add a `formnovalidate` button for "Save draft".

## 7.10 Advanced Note

- **Constraint Validation API:**
  - `input.validity` returns a `ValidityState` with flags: `valueMissing`, `typeMismatch`, `patternMismatch`, `tooLong`, `tooShort`, `rangeUnderflow`, `rangeOverflow`, `stepMismatch`, `badInput`, `customError`, `valid`.
  - `input.checkValidity()` returns `true` or `false` and fires an `invalid` event.
  - `input.reportValidity()` also shows the browser message.
  - `input.setCustomValidity('text')` sets a custom error. Use `''` to clear it.
  - `input.validationMessage` is the current message.
  - `form.checkValidity()` and `form.reportValidity()` check the whole form.
- **`willValidate`:** `input.willValidate` tells if the field takes part in validation (disabled fields do not).
- **Cross-field checks:** HTML cannot check "password and confirm password match". Use JavaScript and `setCustomValidity`.
- **`pattern` flags:** Browsers compile `pattern` with the `v` flag (or `u` in older ones). Some regex features differ from JavaScript's default. Test your patterns.
- **Email validation:** `type="email"` accepts `a@b`, which is valid by the HTML rule (no dot needed). It is not a full check. The best test of an email is to send a message with a link.
- **Server-side validation is required.** The browser check is only a help. A user can use DevTools, `curl`, or a script to skip it.
- **Accessibility of errors:** After a failed submit, move focus to the first error or an error summary at the top of the form. Use `role="alert"` or `aria-live` so that screen readers announce errors. Do not announce on every key press.
- **Error summary pattern:** List all errors at the top with links to each field (`<a href="#email">Enter a valid email</a>`).
- **Inline validation timing:** Check on `blur` (when the user leaves the field), and re-check on `input` after the first error. Do not show an error while the user is still typing for the first time.
- **`aria-invalid`:** Set it with JavaScript to `true` when a field has an error. Remove it when fixed.
- **Number issues:** `type="number"` returns an empty value when the user types non-numeric text (`badInput`). Test it.
- **`inputmode` and `autocomplete`** do not validate. They only help the user.
- **Security:** Always escape user data when you show it. Validation is not protection against XSS or SQL injection.

## 7.11 Exercises

1. Write a username field: required, 3 to 16 characters, letters, digits, and underscores only. Add a `title`.
2. Write an age field for 18 to 65 and a date field for dates in 2026 only.
3. Write 3 good error messages for: a missing name, a short password, a wrong ZIP.
4. Write CSS so that errors show only after the user has used the field.
5. Find the problem: `<input type="number" pattern="[0-9]+">`
6. **Advanced:** Write JavaScript that checks that "password" and "confirm password" match. Use `setCustomValidity`. Add an error message linked with `aria-describedby`.

## 7.12 Check your understanding
- Which attribute makes a field required?
- What does `pattern` need to match?
- Why do you also validate on the server?
- What is `:user-invalid` for?

---

# Lesson 8: `<fieldset>` and `<legend>`

## 8.1 Learning objectives
After this lesson, you can:
- Group related fields with `<fieldset>`.
- Name the group with `<legend>`.
- Use them for radio buttons, checkboxes, and form sections.

## 8.2 The elements

- `<fieldset>` groups related controls.
- `<legend>` is the **title** of the group. It must be the **first child** of `<fieldset>`.

```html
<fieldset>
  <legend>Contact preference</legend>

  <input type="radio" id="pref-email" name="contact" value="email" />
  <label for="pref-email">Email</label>

  <input type="radio" id="pref-phone" name="contact" value="phone" />
  <label for="pref-phone">Phone</label>
</fieldset>
```

## 8.3 Why use them?

1. The screen reader announces the legend **with each field in the group**: *"Contact preference, Email, radio button, 1 of 2."* Without it, the user hears only "Email".
2. They show the user which fields belong together.
3. They make a long form easier to scan.
4. The browser draws a border around the group (you can change this with CSS).

## 8.4 When to use them

| Case | Use `<fieldset>` and `<legend>`? |
|------|----------------------------------|
| A group of **radio buttons** | **Yes. Always.** |
| A group of related **checkboxes** | **Yes.** |
| A section of a long form (for example "Address") | Yes. |
| A single text field | No. Use a `<label>`. |

**Rule:** The `<legend>` is the **question** for the group. The `<label>` of each radio button is the **answer**.

## 8.5 Sections of a form

```html
<form action="/register" method="post">
  <fieldset>
    <legend>Personal details</legend>
    <label for="first">First name</label>
    <input type="text" id="first" name="first" autocomplete="given-name" required />

    <label for="last">Last name</label>
    <input type="text" id="last" name="last" autocomplete="family-name" required />
  </fieldset>

  <fieldset>
    <legend>Address</legend>
    <label for="street">Street</label>
    <input type="text" id="street" name="street" autocomplete="street-address" />

    <label for="city">City</label>
    <input type="text" id="city" name="city" autocomplete="address-level2" />
  </fieldset>

  <button type="submit">Register</button>
</form>
```

## 8.6 `fieldset` attributes

| Attribute | Job |
|-----------|-----|
| `disabled` | Disables **all** controls inside the fieldset (except those in the first `<legend>`). |
| `name` | A name for scripts. |
| `form` | Links the fieldset to a form by ID. |

```html
<fieldset disabled>
  <legend>Shipping (not available)</legend>
  ...
</fieldset>
```

## 8.7 Style them

The default look has a border and a title in the border. Reset it with CSS if you need.

```css
fieldset { border: 1px solid #9ca3af; border-radius: 0.5rem; padding: 1rem; margin: 0 0 1.5rem; }
legend { font-weight: bold; padding: 0 0.5rem; }
```

For a simple style with no border:

```css
fieldset { border: 0; padding: 0; margin: 0 0 1.5rem; min-width: 0; }
legend { font-weight: bold; padding: 0; margin-bottom: 0.5rem; }
```

## 8.8 Try It

1. Make a radio group with a `<fieldset>` and `<legend>`.
2. Make a checkbox group the same way.
3. Make a form with 3 sections (Personal, Address, Account).
4. Add `disabled` to one fieldset. Try to use the fields.
5. If you can, use a screen reader. Listen to the announcement of a radio button with and without a legend.

## 8.9 Advanced Note

- **Layout problems:** `<fieldset>` and `<legend>` have special browser layout. `fieldset` has `min-inline-size: min-content`, which can make it overflow a narrow screen. Add `min-width: 0` to fix it. The `legend` is hard to position with CSS in old browsers. Modern CSS lets you use `display: contents` carefully, or wrap the legend content in an inner element.
- **`role="group"` alternative:** `<div role="group" aria-labelledby="title-id">` gives the same meaning when you cannot use `<fieldset>`. Use native `<fieldset>` first.
- **`role="radiogroup"`:** Is only needed for custom (non-native) radio buttons.
- **Nested fieldsets:** They are valid, but screen readers read each legend. Do not nest more than 2 levels.
- **`disabled` on `<fieldset>`:** This is a good way to disable a whole section with one attribute. The controls in the first `<legend>` stay enabled.
- **`elements` property:** `fieldset.elements` lists the controls inside it.
- **Multi-step forms:** For long forms, consider one section per page or step. Each step is a `<fieldset>`. Keep users informed of their progress with text (for example "Step 2 of 4").
- **Do not use `<legend>` outside a `<fieldset>`.** `<legend>` also works in `<details>` in old specs, but this is not valid.
- **Headings vs. legends:** Use a heading for a **page section**. Use a legend for a **group of controls** that form one question. Do not put a heading in place of a legend. A heading inside a legend is allowed in HTML5, but can add noise for screen readers.

## 8.10 Exercises

1. Write a radio group "T-shirt size" with 4 sizes in a `<fieldset>`.
2. Write a form with the sections "Account" and "Preferences". Use `<fieldset>` and `<legend>`.
3. Explain what a screen reader says for a radio button with a legend, and without a legend.
4. Disable a "Billing address" section with a single attribute.
5. **Advanced:** Fix an overflow problem of a `<fieldset>` on a 320 px wide screen with `min-width: 0`.

## 8.11 Check your understanding
- What is `<legend>`?
- Where must `<legend>` be in `<fieldset>`?
- Why must radio groups use `<fieldset>`?
- What does `disabled` do on a `<fieldset>`?

---

# Lesson 9: Module Project - Registration and Contact Form

## 9.1 Project goal
Build two forms in one project:
1. A **registration form** (account creation).
2. A **contact form** (send a message).

Use correct controls, labels, validation, grouping, and accessibility.

## 9.2 Form 1: Registration form

### Fields

| Section | Field | Control | Rules |
|---------|-------|---------|-------|
| Personal | First name | `text` | Required |
| Personal | Last name | `text` | Required |
| Personal | Date of birth | `date` | Required. Max = today. |
| Personal | Gender (optional) | `radio` group | Include "Prefer not to say". |
| Account | Username | `text` | Required. 3 to 16 characters. Letters, digits, `_`. |
| Account | Email | `email` | Required. |
| Account | Password | `password` | Required. 8 to 64 characters. |
| Account | Confirm password | `password` | Required. Must match. |
| Contact | Phone | `tel` | Optional. Pattern. |
| Contact | Country | `select` | Required. Use `<optgroup>`. |
| Preferences | Interests | `checkbox` group | At least 3 options. |
| Preferences | Favorite color | `color` | Optional. |
| Preferences | Profile photo | `file` | Optional. Images only. |
| Preferences | Experience level | `range` | 1 to 5 with `<output>`. |
| Legal | Accept the terms | `checkbox` | Required. |
| Actions | Register | `submit` | |
| Actions | Clear | `reset` | Optional. |

## 9.3 Form 2: Contact form

| Field | Control | Rules |
|-------|---------|-------|
| Full name | `text` | Required |
| Email | `email` | Required |
| Subject | `select` or `input` + `datalist` | Required |
| Message | `textarea` | Required. 20 to 500 characters. |
| Preferred reply | `radio` group: email or phone | |
| Send me a copy | `checkbox` | |
| Send | `submit` | |

## 9.4 Project folder

```
project/
├── registration.html
├── contact.html
├── style.css
├── script.js          (optional: Level 3)
└── README.md
```

## 9.5 Requirements

### Level 1: Beginner (required)
- [ ] Two pages with full HTML boilerplate and a clear `<title>`.
- [ ] Each form has `action` and `method` (use `method="post"` and any placeholder `action`, or a form service URL).
- [ ] Every control has a `name`.
- [ ] Every control has a `<label>` with `for` and a matching `id`.
- [ ] Use at least these controls: `text`, `email`, `password`, `date`, `tel`, `number` or `range`, `color` or `file`, `textarea`, `select` with `<optgroup>`, radio group, checkbox group.
- [ ] Use `<fieldset>` and `<legend>` for each radio group, each checkbox group, and each form section.
- [ ] Use `required`, `minlength`, `maxlength`, `min`, `max`, and one `pattern` with a `title`.
- [ ] Use `type="submit"` for the main button. Write `type` on all buttons.
- [ ] No `placeholder` used as a label.
- [ ] A short note: "Fields marked * are required."
- [ ] Use the correct `autocomplete` values on name, email, username, and password fields.
- [ ] The form has a basic style with CSS (spacing, borders, visible focus).

### Level 2: Intermediate (recommended)
- [ ] Add help text with `aria-describedby` for the password and username fields.
- [ ] Style `:user-invalid` and `:user-valid`.
- [ ] Use `inputmode` for the phone and ZIP fields.
- [ ] Use `<output>` to show the range value.
- [ ] Add `enctype="multipart/form-data"` for the file upload.
- [ ] The form is usable on a 320 px wide screen (single column).
- [ ] Validate both pages with `https://validator.w3.org`. Fix all errors.
- [ ] Use only the keyboard to fill in and submit both forms.

### Level 3: Advanced (optional)
- [ ] Write JavaScript for "confirm password" with `setCustomValidity`.
- [ ] Write an error summary at the top of the form, with links to the fields, after a failed submit.
- [ ] Use `FormData` and `fetch` to send the form to a service (for example Formspree) with no page reload. Show a success message in an `aria-live` region.
- [ ] Add a honeypot field (a hidden field that robots fill in) to reduce spam. Hide it from real users and from screen readers.
- [ ] Disable the submit button after the first click to stop double submit.
- [ ] Test with a screen reader. Write a short report in `README.md`.
- [ ] Get a Lighthouse Accessibility score of 100.

## 9.6 Steps

1. Read the field tables. Draw each form on paper. Group the fields into sections.
2. Make the files and the HTML boilerplate.
3. Build the registration form one section at a time. Test each section.
4. Add labels, `name`, `id`, and `autocomplete` as you go.
5. Add validation attributes. Test with wrong values.
6. Build the contact form.
7. Add CSS.
8. Test with the keyboard only.
9. Validate. Run Lighthouse.
10. Write `README.md`: what the project does, how to run it, and what you tested.
11. Commit and push:
    ```bash
    git add .
    git commit -m "Add Module 06 registration and contact forms"
    git push
    ```

## 9.7 Starter template (registration form, partial)

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Register | My Site</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <main>
      <h1>Create your account</h1>
      <p>Fields marked <span aria-hidden="true">*</span><span class="visually-hidden">with an asterisk</span> are required.</p>

      <form action="/register" method="post" enctype="multipart/form-data">

        <fieldset>
          <legend>Personal details</legend>

          <label for="first">First name *</label>
          <input type="text" id="first" name="first" autocomplete="given-name" required />

          <label for="last">Last name *</label>
          <input type="text" id="last" name="last" autocomplete="family-name" required />

          <label for="dob">Date of birth *</label>
          <input type="date" id="dob" name="dob" autocomplete="bday" max="2026-12-31" required />

          <fieldset>
            <legend>Gender (optional)</legend>
            <input type="radio" id="g-f" name="gender" value="female" />
            <label for="g-f">Female</label>
            <input type="radio" id="g-m" name="gender" value="male" />
            <label for="g-m">Male</label>
            <input type="radio" id="g-n" name="gender" value="none" checked />
            <label for="g-n">Prefer not to say</label>
          </fieldset>
        </fieldset>

        <fieldset>
          <legend>Account</legend>

          <label for="username">Username *</label>
          <input
            type="text" id="username" name="username"
            autocomplete="username" required
            minlength="3" maxlength="16"
            pattern="[A-Za-z0-9_]{3,16}"
            title="3 to 16 letters, digits, or underscores"
            aria-describedby="username-help"
          />
          <p id="username-help">Use 3 to 16 letters, digits, or underscores.</p>

          <label for="email">Email *</label>
          <input type="email" id="email" name="email" autocomplete="email" required />

          <label for="pw">Password *</label>
          <input
            type="password" id="pw" name="password"
            autocomplete="new-password" required
            minlength="8" maxlength="64"
            aria-describedby="pw-help"
          />
          <p id="pw-help">Use at least 8 characters.</p>

          <label for="pw2">Confirm password *</label>
          <input type="password" id="pw2" name="password2" autocomplete="new-password" required />
        </fieldset>

        <!-- Add: Contact (tel, select with optgroup), Preferences (checkboxes, color, file, range + output), Legal (terms checkbox) -->

        <button type="submit">Create account</button>
        <button type="reset">Clear form</button>
      </form>
    </main>
  </body>
</html>
```

## 9.8 Starter CSS

```css
:root { --accent: #2563eb; --error: #b91c1c; --ok: #15803d; }
body { font-family: system-ui, sans-serif; line-height: 1.5; margin: 0; padding: 1rem; }
main { max-width: 40rem; margin: 0 auto; }

form { display: grid; gap: 1.5rem; }
fieldset { border: 1px solid #9ca3af; border-radius: 0.5rem; padding: 1rem; margin: 0; min-width: 0; }
legend { font-weight: 700; padding: 0 0.5rem; }

label { display: block; margin-top: 0.75rem; font-weight: 600; }
input[type="radio"] + label,
input[type="checkbox"] + label { display: inline; font-weight: 400; margin-left: 0.25rem; }

input:not([type="radio"]):not([type="checkbox"]):not([type="color"]):not([type="range"]),
select, textarea {
  display: block; width: 100%; box-sizing: border-box;
  padding: 0.6rem; margin-top: 0.25rem;
  font: inherit; border: 1px solid #6b7280; border-radius: 0.375rem;
}

input:focus-visible, select:focus-visible, textarea:focus-visible, button:focus-visible {
  outline: 3px solid var(--accent); outline-offset: 2px;
}

input:user-invalid, select:user-invalid, textarea:user-invalid { border-color: var(--error); }
input:user-valid { border-color: var(--ok); }

button { font: inherit; padding: 0.7rem 1.2rem; border-radius: 0.375rem; border: 1px solid var(--accent); cursor: pointer; }
button[type="submit"] { background: var(--accent); color: #fff; }
button[type="reset"] { background: #fff; color: var(--accent); }

.visually-hidden {
  position: absolute; width: 1px; height: 1px; overflow: hidden;
  clip: rect(0 0 0 0); white-space: nowrap;
}
```

## 9.9 Self-check list

1. Does each control have a `name`, a `label`, and a unique `id`?
2. Does each radio and checkbox group have a `<fieldset>` and a `<legend>`?
3. Is `placeholder` used only for extra examples, not as a label?
4. Does each required field have `required` and a visible mark?
5. Do the validation rules match the rules in the field table?
6. Do the error messages tell the user how to fix the problem?
7. Can you fill in and submit the form with only the keyboard?
8. Is the focus outline always visible?
9. Does the form work on a 320 px wide screen and at 200% zoom?
10. Does the validator show 0 errors?
11. Did you remember that the server must validate again?

## 9.10 Grading guide (self-assessment)

| Area | Points |
|------|--------|
| Correct `form`, `action`, `method`, `name` | 10 |
| Correct input types and controls | 15 |
| Labels (`for`/`id`) and accessible names | 20 |
| `fieldset` and `legend` | 10 |
| Validation attributes and `pattern` | 15 |
| Buttons with correct `type` | 5 |
| CSS (layout, focus, valid/invalid states) | 10 |
| Validator shows 0 errors | 5 |
| Git commits and README | 10 |
| **Total** | **100** |

A score of 80 or more means you are ready for Module 07.

---

# Module 06 Review

## Final quiz

**Questions**

1. What is the difference between `GET` and `POST`? Which one do you use for a login form?
2. Why does an `<input>` need a `name` attribute?
3. How do you connect a `<label>` to an `<input>`?
4. Which input type shows a number keyboard on a phone, and should you use it for a ZIP code?
5. What does an unchecked checkbox send to the server?
6. How do you make radio buttons one group?
7. What is the default `type` of a `<button>` inside a form?
8. Which attribute sets a rule such as "exactly 6 digits"? What must you add so that the user understands the rule?
9. Why must radio groups use `<fieldset>` and `<legend>`?
10. Why must the server validate the data again?

**Answers**

1. `GET` puts the data in the URL and is for actions that do not change data (search). `POST` puts the data in the body and is for private data and actions that change data. Use `POST` for a login form.
2. The browser sends only controls that have a `name`. The name is the key for the data.
3. Use `for` on the label with the same value as the `id` of the input (or wrap the input in the label).
4. `type="number"` (or `tel`) gives a number keyboard. Do not use `number` for a ZIP code. Use `type="text"` with `inputmode="numeric"` and a `pattern`.
5. Nothing. The server does not receive the name.
6. Give all radio buttons the same `name`. Each button needs a different `value`.
7. `submit`.
8. `pattern` (for example `pattern="[0-9]{6}"`). Add a `title` that explains the format, and write the rule in visible help text.
9. The screen reader announces the legend (the question) with each option. Without it, the user hears only the option text and does not know the question.
10. A user can skip browser validation (with DevTools or a script). Browser validation is only a help for the user.

## Common mistakes

| Mistake | Fix |
|---------|-----|
| No `name` on a field | Add `name`. Without it, the data is not sent. |
| `placeholder` instead of `<label>` | Always write a `<label>`. |
| `for` does not match `id` | Make them exactly the same. |
| Duplicate `id` values | Make each `id` unique. |
| Radio buttons with different `name` values | Use the same `name` for the group. |
| Radio buttons with the same `value` | Give each a different `value`. |
| No `fieldset` and `legend` for radio groups | Add them. |
| `<button>` with no `type` in a form | Always write `type`. |
| `GET` for a password | Use `POST` and HTTPS. |
| File upload without `enctype="multipart/form-data"` | Add it, and use `method="post"`. |
| `type="number"` for ZIP or phone | Use `type="text"` or `tel` with `inputmode`. |
| `pattern` without `title` | Add a `title` and visible help text. |
| `pattern` with `^` and `$` | They are not needed. The pattern must match the whole value. |
| Red error before the user types | Use `:user-invalid`. |
| Removing the focus outline | Keep a visible `:focus-visible` style. |
| Only client-side validation | Validate on the server also. |
| `<a href="#">` or `<div>` as a button | Use `<button type="button">`. |
| Hiding a label with `display: none` | Use a visually-hidden class. |
| Required fields not marked | Add a visible mark and a note. |
| Disabled submit button with no reason shown | Keep it enabled and show clear errors. |

## Glossary

| Term | Definition |
|------|------------|
| `action` | The URL that receives the form data. |
| `autocomplete` | A hint that lets the browser fill in a field. |
| Constraint Validation API | A JavaScript API for form validation. |
| Control | A form element that the user can use (input, select, textarea, button). |
| CSRF | Cross-Site Request Forgery. An attack that sends a form from another site. A token protects against it. |
| `<fieldset>` | An element that groups related controls. |
| Form data | The name/value pairs that a form sends. |
| `GET` | An HTTP method that puts data in the URL. |
| `<label>` | A text that names a control. |
| `<legend>` | The title of a `<fieldset>`. |
| `method` | The HTTP method of a form (`get` or `post`). |
| `name` | The key that is sent with a control's value. |
| `pattern` | A regular expression that a value must match. |
| `placeholder` | A hint that shows in an empty field. |
| `POST` | An HTTP method that puts data in the request body. |
| Regular expression | A text pattern to match strings. |
| Validation | A check that data is correct and complete. |

## Module 06 progress checklist (copy to `PROGRESS.md`)

```markdown
## Module 06: Forms
- [ ] Lesson 1: form, action, method
- [ ] Lesson 2: Input types
- [ ] Lesson 3: Labels and for/id pairing
- [ ] Lesson 4: textarea, select, optgroup, datalist
- [ ] Lesson 5: Checkboxes and radio buttons
- [ ] Lesson 6: Buttons
- [ ] Lesson 7: Built-in validation
- [ ] Lesson 8: fieldset and legend
- [ ] Lesson 9: Registration and contact form project
- [ ] Final quiz (8/10 or more)
- [ ] Both forms tested with keyboard only
- [ ] Both pages validated with W3C
- [ ] Lighthouse accessibility check done
- [ ] Project pushed to GitHub
```

## Cheat sheet: Module 06

```html
<form action="/submit" method="post" enctype="multipart/form-data" autocomplete="on">

  <!-- Text-like inputs -->
  <label for="n">Name</label>
  <input type="text" id="n" name="name" required minlength="2" maxlength="50" autocomplete="name" />

  <input type="email"    name="email" />
  <input type="password" name="pw"    minlength="8" autocomplete="new-password" />
  <input type="tel"      name="tel"   pattern="\+?[0-9 ]{10,15}" title="Phone number" />
  <input type="url"      name="site" />
  <input type="search"   name="q" />

  <!-- Numbers, dates, other -->
  <input type="number" name="age" min="18" max="99" step="1" />
  <input type="date"   name="dob" min="1900-01-01" />
  <input type="range"  name="level" min="1" max="5" value="3" />
  <input type="color"  name="color" value="#3b82f6" />
  <input type="file"   name="photo" accept="image/*" />

  <!-- Long text and choices -->
  <textarea name="msg" rows="5" minlength="20" maxlength="500"></textarea>

  <select name="country" required>
    <option value="">Choose</option>
    <optgroup label="Asia"><option value="in">India</option></optgroup>
  </select>

  <input list="cities" name="city" />
  <datalist id="cities"><option value="Delhi"></option></datalist>

  <!-- Grouped choices -->
  <fieldset>
    <legend>Question</legend>
    <input type="radio" id="a" name="choice" value="a" checked /><label for="a">A</label>
    <input type="radio" id="b" name="choice" value="b" /><label for="b">B</label>
  </fieldset>

  <input type="checkbox" id="t" name="terms" value="yes" required />
  <label for="t">I accept the terms</label>

  <!-- Buttons -->
  <button type="submit">Send</button>
  <button type="reset">Clear</button>
  <button type="button">Help</button>
</form>
```

| Attribute | Job |
|-----------|-----|
| `required` | Must have a value |
| `minlength` / `maxlength` | Text length |
| `min` / `max` / `step` | Number, date, range limits |
| `pattern` + `title` | Regex rule and its explanation |
| `readonly` | Cannot change, is sent |
| `disabled` | Cannot use, is not sent |
| `autocomplete` | Browser autofill hint |
| `inputmode` | Mobile keyboard type |

| CSS pseudo-class | Matches |
|------------------|---------|
| `:required` `:optional` | Required / optional fields |
| `:valid` `:invalid` | Valid / invalid fields |
| `:user-valid` `:user-invalid` | The same, after the user has used the field |
| `:checked` | Checked checkbox or radio |
| `:disabled` | Disabled control |
| `:focus-visible` | Keyboard focus |

## Next module
Go to **Module 07: Semantic HTML**. You learn `<header>`, `<main>`, `<footer>`, `<section>`, `<article>`, `<aside>`, `<details>`, `<dialog>`, and how to build a blog article layout.
