# Git & GitHub Learning Guide

A structured reference for understanding **Git fundamentals, workflows,
branching, merging, and pull requests**.

------------------------------------------------------------------------

# Table of Contents

1. [Git Identity Setup](#1-git-identity-setup)  
2. [Git Architecture (Workflow Components)](#2-git-architecture-workflow-components)  
3. [Initial Repository Setup](#3-initial-repository-setup)  
4. [Fundamental Git Commands](#4-fundamental-git-commands)  
5. [Branching Workflow](#5-branching-workflow)  
6. [Merge vs Pull Request](#6-merge-vs-pull-request)  
7. [Merge Conflicts](#7-merge-conflicts)  
8. [Best Practices](#8-best-practices)  
9. [Git Workflow Summary](#9-git-workflow-summary)

------------------------------------------------------------------------

# 1. Git Identity Setup

Before using Git, configure your username and email.

``` bash
git config --global user.name "Naveen S S"
git config --global user.email "ssnaveen696@gmail.com"
```

This ensures every commit is associated with your identity.

------------------------------------------------------------------------

# 2. Git Architecture (Workflow Components)

Git operates with four main areas.

### 1. Working Directory

The project folder where files are created or modified.

Example:

    project/
      app.py
      README.md

### 2. Staging Area (Index)

A temporary area where selected changes are prepared for commit.

Command:

``` bash
git add file_name
```

### 3. Local Repository

The `.git` database that stores commit history on your computer.

### 4. Remote Repository

A repository hosted online (GitHub, GitLab, etc).

Example:

    origin/main

------------------------------------------------------------------------

# 3. Initial Repository Setup

Create and connect a repository.

``` bash
echo "# GIT_GITHUB_learning" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/ssnaveenss/GIT_GITHUB_learning.git
git push -u origin main
```

Explanation:

  Command                     Purpose
  --------------------------- --------------------------------
  `git init`                  Initializes a repository
  `git add`                   Moves files to staging
  `git commit`                Saves snapshot
  `git branch -M main`        Renames default branch
  `git remote add origin`     Links GitHub repository
  `git push -u origin main`   Uploads code and sets upstream

After upstream is set, you can simply use:

``` bash
git push
git pull
```

------------------------------------------------------------------------

# 4. Fundamental Git Commands

| Command | Description |
|--------|-------------|
| `git init` | Initialize a Git repository |
| `git clone <url>` | Copy a remote repository |
| `git status` | Show file states |
| `git add <file>` | Stage a file |
| `git add .` | Stage all changes |
| `git commit -m "msg"` | Save staged changes |
| `git log` | View commit history |
| `git diff` | Show code differences |
| `git branch` | List branches |
| `git branch <name>` | Create branch |
| `git switch <branch>` | Switch branch |
| `git checkout <branch>` | Older branch switch command |
| `git merge <branch>` | Merge branch |
| `git remote -v` | Show remote repositories |
| `git push` | Upload commits |
| `git pull` | Fetch and merge remote updates |
| `git fetch` | Download remote changes |
| `git reset` | Undo staging or commits |

------------------------------------------------------------------------

# 5. Branching Workflow

Standard development workflow.

    main
     │
     ├── feature branch
     │       work
     │       commit
     │
     └── merge back to main

### Step 1 -- Check branches

``` bash
git branch
```

### Step 2 -- Create branch

``` bash
git branch Branch-1
```

### Step 3 -- Switch branch

``` bash
git switch Branch-1
```

### Step 4 -- Make changes

Edit files in your code editor.

### Step 5 -- Stage changes

``` bash
git add .
```

### Step 6 -- Commit changes

``` bash
git commit -m "Added feature in Branch-1"
```

### Step 7 -- Push branch

``` bash
git push -u origin Branch-1
```

### Step 8 -- Switch back to main

``` bash
git switch main
```

### Step 9 -- Merge branch

``` bash
git merge Branch-1
```

### Step 10 -- Push updated main

``` bash
git push
```

------------------------------------------------------------------------

# 6. Merge vs Pull Request

## Merge

### When to Use

Used when developers have direct repository access and want to combine
branches locally.

### Commands

``` bash
git switch main
git merge Branch_1
git push
```

------------------------------------------------------------------------

## Pull Request

### When to Use

Used when code review is required before merging.

### Process

1.  Create a branch
2.  Push the branch
3.  Open GitHub
4.  Create Pull Request
5.  Review and merge

Commands:

``` bash
git switch Branch_2
git push -u origin Branch_2
```

On GitHub:

    Base branch: main
    Compare branch: Branch_2

Click **Create Pull Request → Merge Pull Request**.

------------------------------------------------------------------------

# 7. Merge Conflicts

A merge conflict occurs when **two branches modify the same part of a
file**.

Example:

Developer A:

    Hello World
    Login feature added

Developer B:

    Hello World
    Payment feature added

Git conflict markers:

    <<<<<<< HEAD
    Login feature added
    =======
    Payment feature added
    >>>>>>> feature-payment

### Resolving

1.  Open file
2.  Choose correct code
3.  Remove markers
4.  Commit fix

``` bash
git add file
git commit
git push
```

------------------------------------------------------------------------

# 8. Best Practices

### Pull frequently

``` bash
git pull origin main
```

### Keep branches small

Short-lived branches reduce conflicts.

### Use meaningful branch names

Examples:

    feature-login
    bugfix-auth-error
    docs-update

### Commit often

Small commits improve tracking and debugging.

------------------------------------------------------------------------

# 9. Git Workflow Summary

    Working Directory
            ↓
    Staging Area
            ↓
    Local Repository
            ↓
    Remote Repository

Main workflow commands:

``` bash
git add
git commit
git push
```

------------------------------------------------------------------------

# Final Note

Git is a **distributed version control system** that allows developers
to track changes, collaborate efficiently, and maintain project history.

Mastering these workflows enables smooth **team collaboration and
reliable code management**.
