# GitHub Branches: Concept, Commands, and Pushing

## What Is a Branch?

A **Git branch** is essentially a separate line of development within a Git repository.

Think of your main project as the **main road**. A branch creates a **side road** where you can work on a new feature, fix a bug, or experiment without changing the main codebase.

```text
                    ┌── Feature Branch ── Work ── Work ──┐
                    │                                     │
Main ── Work ───────┼─────────────────────────────────────┼──
                    │                                     │
                    └────────────── Other Work ───────────┘
```

The important idea is that **your branch gives you a safe place to make changes**. Once your work is ready, you can merge those changes back into the main branch.

---

# Why Use Branches?

Branches are one of the most important parts of collaborating with Git and GitHub.

Imagine a team working on the same application:

* One developer is building a login feature.
* Another is fixing a bug.
* Another is updating the documentation.
* Another is working on the user interface.

Instead of everyone changing the `main` branch directly, each developer can create their own branch.

```text
                    ┌── login-feature
                    │
                    ├── bug-fix
main ───────────────┼── documentation
                    │
                    └── ui-update
```

Each developer can work independently and then eventually bring their changes back into `main`.

This is a major part of what makes GitHub useful for **collaboration**.

---

# Creating a Branch

First, you can see what branch you are currently on:

```bash
git branch
```

The branch with the `*` is your current branch.

To create a new branch:

```bash
git branch feature-login
```

This **creates** the branch, but it does not move you onto it.

To switch to the branch:

```bash
git checkout feature-login
```

Or, using the newer and more straightforward command:

```bash
git switch feature-login
```

---

# Create and Switch to a Branch at the Same Time

Instead of creating the branch and switching separately, you can do both with:

```bash
git checkout -b feature-login
```

Or:

```bash
git switch -c feature-login
```

The `-b` or `-c` essentially means:

> Create this branch and switch me to it.

So:

```bash
git switch -c feature-login
```

does two things:

```text
Create branch
     ↓
feature-login
     ↓
Switch to feature-login
```

---

# Making Changes on Your Branch

Once you are on your branch, you can work normally.

For example:

```bash
git switch -c feature-login
```

Then you edit your files.

After making your changes, check what Git sees:

```bash
git status
```

You might see something like:

```text
modified: login.html
modified: styles.css
```

---

# Add Your Changes

Next, stage your changes:

```bash
git add .
```

The `.` means:

> Add all changes in the current directory.

You can also add individual files:

```bash
git add login.html
```

Or multiple specific files:

```bash
git add login.html styles.css
```

---

# Commit Your Changes

Once your changes are staged:

```bash
git commit -m "Add login page"
```

A commit is essentially a **saved snapshot of your work**.

Think of it like:

```text
Working files
     ↓
   git add
     ↓
Staged changes
     ↓
  git commit
     ↓
Saved Git history
```

---

# Pushing Your Branch to GitHub

This is where GitHub comes into the picture.

Your branch currently exists **on your computer**.

```text
Your Computer

Repository
    │
    └── feature-login
```

GitHub does not automatically know about your new branch.

You need to **push** it.

---

# The First Time You Push a New Branch

One common command is:

```bash
git push -u origin HEAD
```

This is a very useful command to understand.

### What does `origin` mean?

`origin` is normally the name Git gives to the remote GitHub repository.

Conceptually:

```text
Your Computer                  GitHub

feature-login  ──────────────→  feature-login
                  origin
```

### What does `HEAD` mean?

`HEAD` represents **where you currently are in Git**.

If you are currently on:

```text
feature-login
```

then:

```bash
git push -u origin HEAD
```

essentially means:

> Push the branch I am currently on to the `origin` remote.

This means you don't have to type the branch name.

Instead of:

```bash
git push -u origin feature-login
```

you can use:

```bash
git push -u origin HEAD
```

---

# What Does `-u` Do?

The `-u` stands for `--set-upstream`.

```bash
git push -u origin HEAD
```

The first time you push your branch, Git can establish a relationship between your **local branch** and the **remote branch** on GitHub.

Conceptually:

```text
Local branch
feature-login
      │
      │ upstream
      ▼
GitHub branch
feature-login
```

After that relationship is established, you can usually just use:

```bash
git push
```

instead of specifying the remote and branch every time.

---

# Different Ways to Push

There are several ways you may see developers push branches.

## Option 1: Explicitly Name the Branch

```bash
git push -u origin feature-login
```

This says:

> Push my local `feature-login` branch to `origin` and set it as the upstream branch.

This is very explicit and easy to understand when learning Git.

---

## Option 2: Use `HEAD`

```bash
git push -u origin HEAD
```

This says:

> Push the branch I'm currently on.

This is convenient because you don't have to type the branch name.

For example, if you're currently on:

```text
feature-login
```

then:

```bash
git push -u origin HEAD
```

pushes `feature-login`.

If you're currently on:

```text
bug-fix
```

the same command pushes `bug-fix`.

---

## Option 3: Push Without `-u`

You can also do:

```bash
git push origin feature-login
```

This pushes the branch, but it does **not necessarily establish the upstream tracking relationship**.

You may therefore need to specify the branch again later.

---

# After the First Push

Once you have done:

```bash
git push -u origin HEAD
```

you can generally use:

```bash
git push
```

for future pushes.

For example:

```text
Make changes
     ↓
git add .
     ↓
git commit -m "Update login form"
     ↓
git push
     ↓
GitHub
```

You don't need to keep typing:

```bash
git push origin feature-login
```

because Git now knows which remote branch your local branch is tracking.

---

# Pulling Changes

You will also commonly see:

```bash
git pull
```

`git pull` brings changes from the remote repository into your local repository.

Conceptually:

```text
GitHub
   │
   │ git pull
   ▼
Your computer
```

Whereas:

```bash
git push
```

goes in the opposite direction:

```text
Your computer
   │
   │ git push
   ▼
GitHub
```

---

# A Typical Branch Workflow

A common workflow might look like this:

```bash
# Make sure you're starting from main
git switch main

# Get the latest version
git pull

# Create a new branch
git switch -c feature-login

# Work on your files...

# See what changed
git status

# Stage your changes
git add .

# Commit your changes
git commit -m "Add login feature"

# First push
git push -u origin HEAD
```

After making more changes:

```bash
git add .
git commit -m "Improve login validation"
git push
```

---

# The Big Picture

The entire process can be thought of like this:

```text
                    GITHUB
                       ▲
                       │
                    git push
                       │
                       │
              ┌────────┴────────┐
              │  Local Branch   │
              │ feature-login   │
              └────────┬────────┘
                       │
                 Make changes
                       │
                       ▼
                  git add .
                       │
                       ▼
              git commit -m "..."
                       │
                       ▼
                 Git history
```

And eventually, your branch can be merged back into `main`:

```text
                         ┌── feature-login ── Work ── Work ──┐
                         │                                   │
main ── Work ────────────┴───────────────────────────────────┴──
                                                               │
                                                               ▼
                                                            MERGE
                                                               │
                                                               ▼
                                                              main
```

## The Commands to Remember

| Purpose             | Command                     |
| ------------------- | --------------------------- |
| See current branch  | `git branch`                |
| See current status  | `git status`                |
| Create branch       | `git branch branch-name`    |
| Switch branch       | `git switch branch-name`    |
| Create + switch     | `git switch -c branch-name` |
| Stage changes       | `git add .`                 |
| Commit changes      | `git commit -m "message"`   |
| First push          | `git push -u origin HEAD`   |
| Push future changes | `git push`                  |
| Download changes    | `git pull`                  |

## The Simple Mental Model

```text
BRANCH
   ↓
Create your own workspace
   ↓
MAKE CHANGES
   ↓
git add .
   ↓
STAGE
   ↓
git commit -m "message"
   ↓
SAVE A SNAPSHOT
   ↓
git push -u origin HEAD
   ↓
PUSH TO GITHUB
   ↓
COLLABORATE
   ↓
Pull Request → Review → Merge
```

The key idea is that **Git manages the history and branches on your computer, while GitHub provides the shared space where those branches and commits can be stored, reviewed, and collaborated on with other developers.**
