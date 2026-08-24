# Understanding Git and GitHub

## What Is Git?

Git is a version control system that allows you to store and manage different versions of files on your computer.

## What Is GitHub?

GitHub is a cloud-based service where you can store and share Git repositories online.

## How to Save Versions on Your Computer

### 1. Create or Move into Your Project Directory

Navigate to the directory you want Git to track.

### 2. Initialize Git

In the terminal, run:

```bash
git init
```

This creates a hidden `.git` folder that Git uses to track changes in your project.

You can verify that the folder exists with:

```bash
ls -a
```

### 3. Check Git Status

Run:

```bash
git status
```

The output should indicate that you are on the `master` branch (or `main`, depending on your Git configuration) and display any untracked files.

### 4. Add Files to Be Tracked

Run:

```bash
git add <filename>
```

Example:

```bash
git add README.md
```

This tells Git to begin tracking the file and any future changes made to it.

### 5. Commit Your Changes

Run:

```bash
git commit -m "add a message here"
```

Example:

```bash
git commit -m "Created initial project files"
```

The message should briefly describe the changes made since the previous commit.

At this point, Git has saved a snapshot of your project. You can continue making changes and repeat the process whenever you want to save a new version.

---

## How to Add a Local Repository to GitHub

### 1. Create a GitHub Repository

1. Log in to GitHub.
2. Click the **+** icon in the upper-right corner.
3. Select **New Repository**.
4. Enter a repository name.
5. Choose whether the repository should be **Public** or **Private**.
6. Click **Create Repository**.

### 2. Connect Your Local Repository to GitHub

If you have already initialized Git locally, run:

```bash
git remote add origin https://github.com/<yourUserName>/<yourRepoName>.git
```

Example:

```bash
git remote add origin https://github.com/craig/sample-project.git
```

This tells Git where your remote GitHub repository is located.

### 3. Push Your Commits to GitHub

Run:

```bash
git push -u origin master
```

If your repository uses the `main` branch instead of `master`, use:

```bash
git push -u origin main
```

This uploads your local commits to GitHub.

### 4. Verify the Upload

Refresh the repository page on GitHub. You should now see the files from your local repository.

---

## Typical Git Workflow

After your repository has been connected to GitHub, your day-to-day workflow will usually look like this:

```bash
git status
git add <filename>
git status
git commit -m "your message here"
git status
git push origin master
```

Or, if your default branch is `main`:

```bash
git status
git add <filename>
git status
git commit -m "your message here"
git status
git push origin main
```

Repeat this process whenever you want to save and publish new changes to your project.

---

## Common Git Commands

| Command | Purpose |
|----------|----------|
| `git init` | Initialize a Git repository |
| `git status` | View the current repository status |
| `git add <filename>` | Stage a file for commit |
| `git commit -m "message"` | Create a snapshot of changes |
| `git push origin master` | Upload commits to GitHub |
| `git pull origin master` | Download updates from GitHub |
| `git log` | View commit history |