# Forking a GitHub Repository

## What Is a Fork?

A **fork** is your own copy of someone else's repository on GitHub.

Forking is especially useful when you want to contribute to a project that you **do not own or have direct write access to**.

Instead of working directly on the original repository, you create your own copy:

```text
                    ORIGINAL REPOSITORY
                    github.com/company/project
                              │
                              │ Fork
                              ▼
                    YOUR FORK
                    github.com/you/project
                              │
                              │ Clone
                              ▼
                       YOUR COMPUTER
```

You can then make changes to your copy without affecting the original repository.

---

# Why Fork?

Imagine someone has a project on GitHub:

```text
Original Repository
        │
        ├── main
        ├── feature-a
        └── feature-b
```

You want to contribute, but you don't have permission to push directly to it.

You can **fork** the repository:

```text
Original Repository
        │
        │ Fork
        ▼
Your GitHub Repository
        │
        │ Clone
        ▼
Your Computer
```

Now you have your own copy where you can safely make changes.

When you're ready, you can submit a **Pull Request** asking the original project to review and potentially merge your changes.

---

# Fork vs Clone

These two concepts are easy to confuse.

### Fork

A **fork happens on GitHub**.

It creates your own GitHub copy of someone else's repository.

```text
GitHub

Original Repo
      │
      │ Fork
      ▼
Your Repo
```

### Clone

A **clone happens on your computer**.

It downloads a repository from GitHub to your local machine.

```text
GitHub
   │
   │ git clone
   ▼
Your Computer
```

So a typical workflow is:

```text
Original GitHub Repository
          │
          │ Fork
          ▼
Your GitHub Repository
          │
          │ Clone
          ▼
Your Computer
```

---

# Step 1: Fork the Repository

On GitHub, open the repository you want to contribute to and select **Fork**.

GitHub creates a copy under your account.

For example:

```text
Original:

github.com/company/project

Your fork:

github.com/your-username/project
```

You now have two repositories:

```text
ORIGINAL                         YOUR FORK
company/project                  your-username/project
      │                                  │
      │                                  │
      └────────── Related ───────────────┘
```

They are separate repositories.

---

# Step 2: Clone Your Fork

You generally want to clone **your fork**, not the original repository.

```bash
git clone https://github.com/your-username/project.git
```

Then:

```bash
cd project
```

You now have the repository on your computer.

---

# Step 3: Check Your Remote

This is one of the **most important steps** when working with forks.

Run:

```bash
git remote -v
```

You might see:

```text
origin  https://github.com/your-username/project.git (fetch)
origin  https://github.com/your-username/project.git (push)
```

This tells you where `origin` points.

In this example:

```text
origin → YOUR fork
```

That means:

```bash
git push
```

will push to **your repository**.

---

# Why Checking Your Remote Matters

This is extremely important when working with forks.

You don't want to accidentally do this:

```text
Your Computer
     │
     │ git push
     ▼
Original Repository
```

especially if the original repository is **not protected** and you have permission to push to it.

Instead, you generally want:

```text
Your Computer
     │
     │ git push
     ▼
YOUR FORK
     │
     │ Pull Request
     ▼
ORIGINAL REPOSITORY
```

Before you push, get into the habit of checking:

```bash
git remote -v
```

Ask yourself:

> **Where is my `origin` pointing?**

---

# Understanding Remotes

When working with a fork, it is common to have **two remotes**:

```text
origin
upstream
```

They represent two different repositories.

### `origin`

Usually represents **your fork**.

```text
origin
   ↓
Your GitHub Repository
```

### `upstream`

Usually represents the **original repository**.

```text
upstream
    ↓
Original GitHub Repository
```

The complete setup looks like this:

```text
                  ORIGINAL REPOSITORY
                  github.com/company/project
                           ▲
                           │
                       upstream
                           │
                           │
                    YOUR COMPUTER
                           │
                           │
                        origin
                           │
                           ▼
                     YOUR FORK
                github.com/you/project
```

This setup is extremely useful because you can:

* **pull updates from the original project**
* **push your changes to your own fork**
* **create Pull Requests back to the original project**

---

# Setting Up `upstream`

If you cloned your fork, your `origin` should already point to your fork.

You can verify it:

```bash
git remote -v
```

Then add the original repository as `upstream`:

```bash
git remote add upstream https://github.com/company/project.git
```

Now check again:

```bash
git remote -v
```

You might see:

```text
origin    https://github.com/your-username/project.git (fetch)
origin    https://github.com/your-username/project.git (push)

upstream  https://github.com/company/project.git (fetch)
upstream  https://github.com/company/project.git (push)
```

Now Git knows about both repositories.

---

# Why Have Two Remotes?

This gives you a clean separation:

```text
                    ORIGINAL REPO
                         ▲
                         │
                      upstream
                         │
                         │
                    YOUR COMPUTER
                         │
                         │
                       origin
                         │
                         ▼
                      YOUR FORK
```

You generally **pull from `upstream`** and **push to `origin`**.

For example:

```bash
git fetch upstream
```

gets information from the original repository.

And:

```bash
git push origin my-branch
```

sends your branch to your fork.

---

# Creating a Branch

Once your fork is set up, create a branch for your work:

```bash
git switch -c feature-login
```

Now you have:

```text
main
 │
 └── feature-login
```

You can make your changes without changing `main`.

---

# Add and Commit Your Changes

After making changes:

```bash
git status
```

Then stage them:

```bash
git add .
```

Commit:

```bash
git commit -m "Add login feature"
```

At this point, your changes are saved locally.

---

# Push Your Branch to Your Fork

For the first push:

```bash
git push -u origin HEAD
```

Remember:

```text
origin → YOUR FORK
```

So this command means:

> Push my current branch to my fork and remember this relationship.

After that, you can generally use:

```bash
git push
```

---

# Create a Pull Request

Once your branch is on your fork:

```text
YOUR COMPUTER
      │
      │ git push
      ▼
YOUR FORK
      │
      │ Pull Request
      ▼
ORIGINAL REPOSITORY
```

You create a **Pull Request** on GitHub.

The original project can then:

1. Review your changes
2. Comment on your code
3. Request changes
4. Approve the Pull Request
5. Merge your changes

Your changes don't go directly into the original repository just because you pushed them.

---

# Keeping Your Fork Up to Date

The original project will continue to change while you're working.

For example:

```text
ORIGINAL REPOSITORY
       │
       │ New commits
       ▼
     main
```

Your fork might be behind:

```text
Original main:    A ── B ── C ── D
Your main:        A ── B ── C
```

You can retrieve the latest information from the original repository with:

```bash
git fetch upstream
```

Then you can update your local `main` branch.

One common approach is:

```bash
git switch main
git merge upstream/main
```

Then update your fork:

```bash
git push origin main
```

Now:

```text
Original Repository
        │
        │ upstream
        ▼
Your Local Repository
        │
        │ origin
        ▼
Your Fork
```

---

# The Most Important Safety Habit

When working with multiple remotes, **always know where you are pushing**.

Before pushing, run:

```bash
git remote -v
```

Look for:

```text
origin
```

and verify that it points to **your fork**.

For example:

```text
origin    https://github.com/your-username/project.git
```

Good.

But if you see:

```text
origin    https://github.com/company/project.git
```

**Stop and investigate before pushing.**

Your remote configuration determines where commands such as:

```bash
git push
```

can send your commits.

---

# A Safe Fork Workflow

Here's a typical workflow from beginning to end:

```bash
# Clone YOUR fork
git clone https://github.com/your-username/project.git

# Enter the project
cd project

# Check your remote
git remote -v

# Add the original repository
git remote add upstream https://github.com/company/project.git

# Check both remotes
git remote -v

# Get the latest information from the original project
git fetch upstream

# Create your feature branch
git switch -c feature-login

# Make your changes...

# Stage your changes
git add .

# Commit your changes
git commit -m "Add login feature"

# First push of the branch
git push -u origin HEAD

# Create a Pull Request on GitHub
```

---

# The Mental Model

Think about the three locations:

```text
              ORIGINAL REPOSITORY
                     │
                     │
                  upstream
                     │
                     ▼
              ┌──────────────┐
              │ YOUR COMPUTER│
              └──────────────┘
                     │
                     │
                   origin
                     │
                     ▼
                YOUR FORK
```

### Remember:

**`upstream` = where the original project lives**

**`origin` = where your fork lives**

**`git fetch upstream` = get information from the original project**

**`git push origin` = send your work to your fork**

**Pull Request = ask the original project to bring your changes in**

---

# Quick Reference

| Task                            | Command                         |
| ------------------------------- | ------------------------------- |
| Clone repository                | `git clone <url>`               |
| See remotes                     | `git remote -v`                 |
| Add original repo               | `git remote add upstream <url>` |
| Get updates from original       | `git fetch upstream`            |
| Create branch                   | `git switch -c branch-name`     |
| Check changes                   | `git status`                    |
| Stage changes                   | `git add .`                     |
| Commit changes                  | `git commit -m "message"`       |
| First push                      | `git push -u origin HEAD`       |
| Future pushes                   | `git push`                      |
| Push specifically to fork       | `git push origin branch-name`   |
| Update local main from original | `git merge upstream/main`       |

## The Big Picture

Forking is really about creating a **safe collaboration boundary**:

```text
                    ORIGINAL PROJECT
                           ▲
                           │
                     Pull Request
                           │
                           │
                      YOUR FORK
                           ▲
                           │
                       git push
                           │
                           │
                    YOUR BRANCH
                           ▲
                           │
                  git add / commit
                           │
                           │
                    YOUR COMPUTER
```

The most important thing to remember is:

> **Fork → Clone → Check your remotes → Add `upstream` → Create a branch → Make changes → Add → Commit → Push to `origin` → Pull Request.**

And before you ever push, **check your remote**. You want to be absolutely certain that `origin` points to **your fork**, not the original repository.
