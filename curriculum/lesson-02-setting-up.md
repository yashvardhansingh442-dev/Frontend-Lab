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
