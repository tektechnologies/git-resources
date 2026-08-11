# Git & GitHub — Basic Workflow

## 1. Navigate to Your Desktop

### `cd`

**Change Directory** — moves you into a different folder.

```bash
cd Desktop
```

Moves you into your Desktop folder.

### `ls`

Lists the files and folders in your current location.

```bash
ls
```

You should now see the files/folders on your Desktop.

---

# 2. Create a Projects Folder

If you don't already have one:

```bash
mkdir projects
```

Creates a folder called `projects`.

Then navigate into it:

```bash
cd projects
```

> **Note:** Your original instructions said `cd project`, but if you created `projects`, the command should be `cd projects`.

Verify you're in the correct folder:

```bash
pwd
```

`pwd` = **Print Working Directory**

---

# 3. Clone the GitHub Repository

Go to GitHub and copy the repository's URL.

Then run:

```bash
git clone "GitHub Repository URL"
```

Example:

```bash
git clone https://github.com/username/my-project.git
```

Git will download the repository into a new folder.

---

# 4. Verify the Repository Downloaded

Run:

```bash
ls
```

You should see the new repository folder.

For example:

```text
projects
├── my-project
```

---

# 5. Enter the Repository

Navigate into the repository:

```bash
cd my-project
```

Replace `my-project` with the actual repository name.

---

# 6. Check the Git Repository

Run:

```bash
git status
```

This tells you things such as:

* What branch you're currently on
* Whether you have modified files
* Whether you have uncommitted changes
* Whether your local branch is ahead/behind the remote branch

### Check Your Current Branch

To specifically see which branch you're on:

```bash
git branch
```

You'll see something like:

```text
* main
```

The `*` indicates your current branch.

> **Important:** `git status` tells you your current branch, but it doesn't specifically mean "I am on master." The repository may use `main`, `master`, `develop`, or another branch.

---

# 7. Open the Project in VS Code

From inside the repository folder:

```bash
code .
```

The `.` means **the current directory**.

This opens the current project in Visual Studio Code.

---

# 8. Before Making Changes — Get the Latest Version

This is an important step to add to your workflow.

Before you start working, make sure your local copy is up to date with GitHub.

If your main branch is called `main`:

```bash
git pull origin main
```

If your repository uses `master`:

```bash
git pull origin master
```

You can check your branch first:

```bash
git branch
```

### Why?

Someone else may have pushed changes to GitHub since you last downloaded the project.

Running `git pull` gets those changes onto your computer before you start working.

---

# 9. Make Your Changes

Now you can edit your project in VS Code.

For example, you might:

* Add a new component
* Fix a bug
* Change styling
* Add a feature
* Modify a database/API call
* Update documentation

Save your files when you're finished.

---

# 10. Check Your Changes

Run:

```bash
git status
```

Git will show you which files have been changed.

For example:

```text
modified:   src/components/MyComponent.tsx
```

At this point, your changes are **only on your computer**.

They have NOT been uploaded to GitHub yet.

---

# 11. Stage Your Changes

This is the first part of **ACP**:

**A = Add**

You can add one specific file:

```bash
git add filename
```

Example:

```bash
git add src/components/MyComponent.tsx
```

Or add all changed files:

```bash
git add .
```

The `.` means:

> Add all changes in the current directory.

---

# 12. Check the Staged Changes

Run:

```bash
git status
```

Files that have been staged will generally appear differently from unstaged changes.

A typical workflow is:

```text
Red → Modified but not staged

Green → Staged and ready to commit
```

This is a useful way to verify exactly what you're about to commit.

---

# 13. Commit Your Changes

This is the second part of **ACP**:

**C = Commit**

Run:

```bash
git commit -m "Add commit message here"
```

Example:

```bash
git commit -m "Fix visitor check-in form"
```

A commit creates a saved checkpoint of your changes in your **local Git repository**.

> The commit has NOT been uploaded to GitHub yet.

---

# 14. Check Your Status Again

Run:

```bash
git status
```

You may see something like:

```text
Your branch is ahead of 'origin/main' by 1 commit.
```

This means:

> Your computer has a commit that GitHub doesn't have yet.

This is exactly when you're ready to push.

---

# 15. Push Your Changes to GitHub

This is the third part of **ACP**:

**P = Push**

If your branch is `main`:

```bash
git push origin main
```

If your branch is `master`:

```bash
git push origin master
```

This uploads your local commits to GitHub.

---

# 16. Verify Everything Is Clean

After pushing, run:

```bash
git status
```

Ideally you'll see something similar to:

```text
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```

That means:

* Your files are committed
* Your commits have been pushed
* Your local repository matches GitHub
* You have no uncommitted changes

---

# The Basic ACP Workflow

Once the repository is already set up, your normal workflow becomes:

```text
Make Changes
     ↓
git status
     ↓
git add .
     ↓
git status
     ↓
git commit -m "Describe changes"
     ↓
git status
     ↓
git push origin main
     ↓
git status
```

Or remember:

### ACP

**A — Add**

```bash
git add .
```

**C — Commit**

```bash
git commit -m "Describe what you changed"
```

**P — Push**

```bash
git push origin main
```

---

# Complete First-Time Setup

If you're starting from scratch on a new computer:

```bash
cd Desktop
```

```bash
mkdir projects
```

```bash
cd projects
```

```bash
git clone "GitHub Repository URL"
```

```bash
ls
```

```bash
cd repository-name
```

```bash
git status
```

```bash
git branch
```

```bash
code .
```

Then, after making changes:

```bash
git status
```

```bash
git add .
```

```bash
git commit -m "Describe changes"
```

```bash
git push origin main
```

```bash
git status
```

---

# Important Commands to Know

| Command                   | What it does                            |
| ------------------------- | --------------------------------------- |
| `pwd`                     | Shows your current directory            |
| `ls`                      | Lists files/folders                     |
| `cd folder`               | Moves into a folder                     |
| `cd ..`                   | Moves up one folder                     |
| `mkdir folder`            | Creates a folder                        |
| `git clone URL`           | Downloads a GitHub repository           |
| `git status`              | Shows repository status                 |
| `git branch`              | Shows your branches                     |
| `git switch branch`       | Switches branches                       |
| `git pull`                | Downloads and integrates remote changes |
| `git add .`               | Stages all changes                      |
| `git add file`            | Stages a specific file                  |
| `git commit -m "message"` | Saves staged changes as a commit        |
| `git push`                | Uploads commits to GitHub               |
| `git log`                 | Shows commit history                    |
| `git diff`                | Shows changes that haven't been staged  |

---

# One Important Team-Development Rule

If you're working on a project with other developers, **don't automatically work directly on `main`/`master`**.

A common professional workflow is:

```bash
git switch main
git pull origin main
git switch -c my-new-feature
```

Then make your changes and use:

```bash
git add .
git commit -m "Add new feature"
git push -u origin my-new-feature
```

You can then create a **Pull Request** on GitHub to merge your feature into `main`.

This is generally safer than everyone pushing directly to `main`.

---

# Recommended Mental Model

Think of Git as having three important places:

```text
YOUR COMPUTER
     │
     │ git add
     ↓
STAGING AREA
     │
     │ git commit
     ↓
LOCAL GIT REPOSITORY
     │
     │ git push
     ↓
GITHUB
```

So:

**`git add`** = "I want these changes included."

**`git commit`** = "Save these changes as a checkpoint."

**`git push`** = "Upload my checkpoints to GitHub."

And going the other direction:

**`git pull`** = "Get the latest changes from GitHub onto my computer."
