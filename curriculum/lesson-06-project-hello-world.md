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
