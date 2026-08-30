# Git Resources

* [Learn Git Branching](https://learngitbranching.js.org/) — Interactive visual tutorial for learning Git.
* [GitHub Status History](https://www.githubstatus.com/history) — Check GitHub's historical service status and incidents.
* [Oh Shit, Git!?](https://ohshitgit.com/) — Practical solutions for common Git mistakes.
* [posh-git](https://github.com/dahlbyk/posh-git) — PowerShell environment for Git with enhanced prompts and tab completion.
* [awesome-readme-template](https://github.com/Louis3797/awesome-readme-template) - awesome-readme-template
* [blog.udemy](https://blog.udemy.com/git-tutorial-a-comprehensive-guide/) - git-tutorial-a-comprehensive-guide

A collection of beginner-friendly guides for learning Git and GitHub fundamentals, including repository management, team workflows, and merge conflict resolution.

## Contents

### 📚 Learning Materials

#### 📘 Learn Git (`learn-git/`)

**Core Guides:**

* **`git-and-github-basics-guide.md`** - Fundamentals of Git and GitHub, including repository creation, tracking files, committing changes, and connecting to GitHub.
  
* **`git-repo-setup-acp.md`** - Introduction to core Git concepts and the Add-Commit-Push (ACP) workflow, with explanations of Git vs GitHub and version control.

* **`git-branching-part-2.md`** - Comprehensive guide to Git branches, their purpose, creation, pushing to remote repositories, and best practices for collaborative development.

* **`git-forking-repos.md`** - Learn about forking repositories, when to use forks, and how to contribute to projects you don't own through the forking workflow.

**Supporting Assets:**
* `git-branching-A.png` & `git-branching-B.png` - Visual diagrams illustrating branching concepts
* `github-pages-guide.pdf` - Guide to publishing projects with GitHub Pages

---

#### 🔄 Manage Git (`manage-git/`)

* **`github-workflow.md`** - Step-by-step guide to developer workflows including command line navigation, cloning repositories, and common Git commands.

* **`git-team-workflow.md`** - Learn collaborative Git practices for working with multiple developers, including pulling updates, creating branches, and coordinating efforts.

* **`pull_request_template.md`** - Standard pull request template with release readiness checklist and documentation requirements for team contributions.

---

#### ⚠️ Handling Merge Conflicts (`git-issues-conflicts/`)

* **`handle-merge-conflicts.md`** - Learn to identify and resolve merge conflicts, including understanding conflict markers, editing strategies, and best practices.

* **`merge-conflict-exercise.md`** - Hands-on lab exercise for practicing merge conflict resolution with team scenarios and role-based exercises.

---

#### 🎓 Introduction to Git Slides (`intro-to-git-slideDeck-wip/`)

A comprehensive slide deck covering Git and GitHub concepts:

* Slides 1-29 covering topics from ice breakers through advanced Git concepts
* Includes visual diagrams and interactive exercises
* Multiple supporting images for reference
* Designed for classroom instruction and self-paced learning

**Note:** This is a work-in-progress (WIP) slide deck and may be updated regularly.

---

#### ⚙️ Configuration Files (`github-config-files/`)

Ready-to-use configuration files for development projects:

* `.eslintrc.json` - ESLint configuration for JavaScript/TypeScript linting
* `.gitignore` - Standard gitignore patterns for common project types
* `.markdownlint.json` - Markdown linting configuration

---

## Prerequisites

Before using these guides, make sure you have:

* Git installed on your computer
* A GitHub account
* A code editor such as VS Code
* Basic familiarity with using a terminal or command prompt

---

## Recommended Learning Path

If you are new to Git and GitHub, follow these guides in this order:

### Beginner Track

1. **`learn-git/git-and-github-basics-guide.md`** - Start with the fundamentals
2. **`learn-git/git-repo-setup-acp.md`** - Learn the Add-Commit-Push workflow
3. **`manage-git/github-workflow.md`** - Understand day-to-day development workflow

### Intermediate Track

1. **`learn-git/git-branching-part-2.md`** - Master branching and collaboration
2. **`manage-git/git-team-workflow.md`** - Learn team collaboration practices
3. **`git-issues-conflicts/handle-merge-conflicts.md`** - Understand conflict resolution

### Advanced / Practice Track

1. **`git-issues-conflicts/merge-conflict-exercise.md`** - Hands-on practice with merge conflicts
2. **`learn-git/git-forking-repos.md`** - Contribute to projects through forking

### Supplementary Resources

* **Slides:** Review `intro-to-git-slideDeck-wip/` for visual instruction and classroom materials
* **Templates:** Use `manage-git/pull_request_template.md` for team submissions
* **Configuration:** Apply files from `github-config-files/` to your projects

---

## Useful Git Commands

### Basic Workflow (Add-Commit-Push)

```bash
git status                    # Check current repository status
git add <filename>            # Stage specific file
git add .                     # Stage all changes
git commit -m "message"       # Commit staged changes
git push origin main          # Push commits to remote repository
```

### Branching

```bash
git branch                    # List local branches
git branch <branch-name>      # Create new branch
git checkout <branch-name>    # Switch to branch
git checkout -b <branch-name> # Create and switch to new branch
git push origin <branch-name> # Push branch to remote
```

### Pulling & Merging

```bash
git pull origin main          # Fetch and merge remote main branch
git pull origin <branch-name> # Fetch and merge specific branch
git merge <branch-name>       # Merge branch into current branch
```

### Resolving Conflicts

```bash
git status                    # Identify conflicted files
git diff                      # View detailed conflict markers
git add <resolved-file>       # Stage resolved file
git commit -m "Resolve conflicts" # Finalize merge
```

### Forking & Contributing

```bash
git clone <fork-url>          # Clone your fork to local machine
git remote add upstream <original-url> # Add original repo as upstream
git fetch upstream            # Fetch changes from original repository
git merge upstream/main       # Merge upstream changes into your branch
```
