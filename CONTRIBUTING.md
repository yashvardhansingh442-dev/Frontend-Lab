# Contributing to Frontend Lab

Thank you for your interest in this repo. Frontend Lab is a learning project: written HTML lessons in `curriculum/` and runnable practice pages in `learning-codes/`. Contributions that make the lessons clearer and the code more correct are welcome.

## Ways to contribute

- **Fix errors:** wrong facts, typos, broken links, or code that does not work.
- **Improve explanations:** make a lesson shorter, clearer, or easier for a beginner.
- **Report broken examples:** a page that does not open, a missing asset, or an invalid HTML pattern.
- **Suggest topics or resources:** open an issue and explain why the topic fits.
- **Add exercises or examples:** new tasks that match a lesson's learning objectives.

Please open an issue before you start a large change, such as a new module or a rewrite of a lesson. This avoids wasted work.

## Report an issue

Before you open an issue, search the existing issues to see if it is already reported. Then include:

1. **Where:** the file name and, if possible, the lesson or line number.
2. **What is wrong:** describe the problem in one or two sentences.
3. **What you expected:** the correct fact, behavior, or wording.
4. **For code issues:** your browser and operating system, and the steps to see the problem.

## Submit a pull request

1. Fork the repository.
2. Create a branch from `main`. Use a short, clear name, for example `fix/forms-password-method` or `docs/module-03-typo`.
3. Make your change. Keep each pull request about **one topic**.
4. Check your change (see the checklists below).
5. Commit with a clear message (see [Commit messages](#commit-messages)).
6. Push your branch and open a pull request. Explain what you changed and why. Link the related issue, if there is one.

I will review your pull request as soon as I can. I might ask for changes. Please be patient, because this is a personal project.

## Style guide: curriculum (`curriculum/*.md`)

The lessons use **ASD-STE100 Simplified Technical English**. This keeps them easy to read for beginners and for readers who use English as a second language.

- Write short sentences. Use one idea in each sentence.
- Use simple words. Use the same word for the same thing every time.
- Use the active voice and the present tense when you can.
- Give commands directly: "Open the file." Not: "You might want to open the file."
- Explain each new term the first time you use it, and add it to the lesson's **Key terms** table.
- Keep the lesson structure. Each lesson has: learning objectives, key terms, the main content, **Try It**, **Advanced Note**, **Exercises**, and **Check your understanding**.
- Put code in fenced code blocks and name the language, for example ` ```html `.
- Teach current HTML only. Do not recommend obsolete elements such as `<font>`, `<center>`, `<big>`, or `<marquee>`. You can mention them to explain why not to use them.

**Checklist for lesson changes**

- [ ] The facts are correct. Check them against [MDN Web Docs](https://developer.mozilla.org/) or the [HTML Standard](https://html.spec.whatwg.org/).
- [ ] The sentences are short and the words are simple.
- [ ] Every code example is valid and works in a modern browser.
- [ ] Links work.

## Style guide: practice code (`learning-codes/`)

Each practice page shows one concept. Write it so a beginner can read it.

- Start with `<!DOCTYPE html>`, and add `<html lang="en">`, `<meta charset="UTF-8">`, and the viewport meta tag.
- Give each page a **descriptive** `<title>`, for example `Forms demo`. Do not use numbers such as "My 15th Website".
- Use **4 spaces** for indentation. Use lowercase for tag and attribute names.
- Add short comments that explain what each important tag or attribute does.
- Use semantic elements, such as `<nav>`, `<main>`, and `<figure>`, when they fit.
- Always add `alt` text to images and a `<label>` to every form control.
- Do not use obsolete elements or attributes.
- Use `POST`, not `GET`, for forms that send passwords or other private data.
- Do not nest interactive elements, for example a `<button>` inside an `<a>`.
- Put media and other files in an `assets/` folder. Use relative paths. Keep files small: **no media file larger than 1 MB**.
- Do not add files that you do not have the right to share. Use your own work or content with a free license, and say where it came from.

**Checklist for code changes**

- [ ] The page opens in a browser with no errors in the console.
- [ ] The HTML passes the [W3C Markup Validator](https://validator.w3.org/) with no errors.
- [ ] All linked files exist, and the paths are correct.
- [ ] The comments are correct and match the code.

## Commit messages

Write a short summary line in the imperative mood, with a type at the start:

- `fix:` for a correction
- `docs:` for a change in a lesson or the README
- `feat:` for a new example, exercise, or module
- `chore:` for file moves, renames, and cleanup

Examples:

```
fix: use POST for registration form
docs: correct URL example in module 01
feat: add exercises to module 05 lesson 3
```

## Be respectful

Be kind and patient. Give feedback on the work, not on the person. Beginners are welcome here, and no question is too basic. Harassment or abusive language is not accepted, and I can remove comments or block users who do not follow this rule.

## License

When you contribute to this project, you agree that your contribution is licensed under the [MIT License](./LICENSE), the same as the rest of the repo.

## Questions

If you are not sure about something, open an issue and ask. Thank you for helping to improve Frontend Lab.
