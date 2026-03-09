```markdown
# MERGE CONFLICT

## What it is

A **merge conflict** occurs when two branches modify the same part of a file and Git cannot automatically decide which change should be kept.

Git normally merges changes automatically when developers edit **different parts of the code**.  
But when **the same line or section of a file is modified in multiple branches**, Git cannot determine which version is correct.

In such cases, Git stops the merge process and asks the developer to **manually resolve the conflict**.

---

# Understanding with Two Branches

## Initial state in main branch

Branch: **main**

File: `app.txt`

```

Hello World

```

This is the original state of the project.

---

# Developer A creates a branch

Branch created from `main`:

```

feature-login

```

Developer A edits the file to add a login feature.

File becomes:

```

Hello World
Login feature added

```

Developer A commits and pushes this branch.

---

# Developer B creates another branch from main

Branch created from `main`:

```

feature-payment

```

Developer B edits the same file to add a payment feature.

File becomes:

```

Hello World
Payment feature added

```

Developer B commits and pushes this branch.

---

# Both developers create Pull Requests

Now two pull requests exist:

```

PR 1 : feature-login  →  main
PR 2 : feature-payment → main

```

Both developers want their changes merged into the **main branch**.

---

# PR 1 gets merged first

The maintainer reviews and merges **feature-login**.

Now the `main` branch becomes:

```

Hello World
Login feature added

```

The project now contains Developer A's change.

---

# When PR 2 tries to merge

Developer B's branch was created from the **older version of main**.

Developer B expected the file to look like:

```

Hello World

```

But the current **main branch** now contains:

```

Hello World
Login feature added

```

Since **both developers edited the same section of the file**, Git cannot automatically combine them.

This situation creates a **merge conflict**.

---

# How Git Shows the Conflict

Git marks the conflicting area inside the file.

`app.txt` will look like this:

```

<<<<<<< HEAD
Hello World
Login feature added
===================

Hello World
Payment feature added

> > > > > > > feature-payment

```

Meaning:

**HEAD**

This represents the current code in the branch you are merging into (usually `main`).

```

Hello World
Login feature added

```

**=======**

Separator between the two versions.

**feature-payment**

The incoming change from the branch being merged.

```

Hello World
Payment feature added

```

Git is asking the developer to decide **which code should remain**.

---

# How Developers Resolve the Conflict

**Step 1**  
Open the conflicting file.

**Step 2**  
Analyze both changes and determine the correct final version.

Example final code:

```

Hello World
Login feature added
Payment feature added

```

**Step 3**  
Remove the conflict markers:

```

# <<<<<<<

> > > > > > >

````

**Step 4**  
Stage the corrected file.

```bash
git add app.txt
````

**Step 5**
Complete the merge commit.

```bash
git commit
```

**Step 6**
Push the resolved changes.

```bash
git push
```

After this, the pull request can be merged successfully.

---

# Why Merge Conflicts Happen

1. Two developers modify the **same line of code**.
2. One branch deletes a file while another branch modifies it.
3. Two branches modify the **same section of a file**.
4. Developers work on branches for a **long time without syncing with main**.
5. Multiple developers work on the **same feature or module simultaneously**.

---

# How Developers Avoid Conflicts

## 1. Pull latest changes frequently

Before starting work, update your branch.

```bash
git pull origin main
```

This ensures your code is based on the **latest version of the project**.

---

## 2. Keep branches small and short-lived

Instead of working for weeks on a branch, developers usually:

* Create a branch
* Complete a small feature
* Merge it quickly

This reduces the chance of conflicts.

---

## 3. Communicate with the team

If two developers plan to modify the same file, they should coordinate their work.

Example:

```
Developer A → login system
Developer B → payment system
```

Both should know which files they are modifying.

---

## 4. Merge main into feature branches regularly

Updating your feature branch with the latest main branch helps detect conflicts early.

```bash
git merge main
```

or

```bash
git pull origin main
```

This prevents large conflicts later.

---

# Key Concept to Remember

Git merges automatically **when changes occur in different parts of the code**.

Example (No conflict)

```
Line 1 changed by Developer A
Line 50 changed by Developer B
```

Git can combine these safely.

But conflict occurs when:

```
Line 10 changed by Developer A
Line 10 changed by Developer B
```

Git cannot decide which change is correct, so it asks the developer to resolve it manually.

```
```
