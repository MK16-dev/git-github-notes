# Working Directory



---

# 1. Introduction

The **Working Directory** is the place on your computer where you actively work on your project.

It contains all your project files, such as source code, images, documents, configuration files, and folders.

Whenever you create, edit, rename, or delete a file, those changes happen first in the **Working Directory**.

In simple words:

> **The Working Directory is where you do your actual work before telling Git about it.**

---

# 2. Why Do We Need a Working Directory?

Every project needs a place where developers can freely make changes.

The Working Directory allows you to:

- Create new files
- Edit existing files
- Delete unwanted files
- Rename files
- Organize folders

Git does **not** automatically save these changes.

You decide when Git should start tracking them.

---

# 3. How Does the Working Directory Work?

Suppose your project looks like this:

```
SpringProject/
│
├── src/
├── pom.xml
├── README.md
└── application.properties
```

You open `README.md` and add new content.

At this moment:

- The file has changed.
- Git knows the file is modified.
- The change exists only in the **Working Directory**.

It has **not** been added to Git's history yet.

---

# 4. Internal Workflow

```
Create File
      │
Edit File
      │
Delete File
      │
Rename File
      │
      ▼
Working Directory
```

Git simply watches these changes.

Nothing is saved permanently until you stage and commit them.

---

# 5. Real-Life Example

Imagine you're writing an assignment.

Before submitting it, you keep editing it on your laptop.

Your laptop is the **Working Directory**.

The assignment isn't submitted yet.

You're still making changes.

Similarly, files in the Working Directory are **not yet saved into Git's history**.

---

# 6. Working Directory Example

Suppose you create:

```
Student.java
```

Git Status:

```bash
git status
```

Output:

```
Untracked files:

Student.java
```

This means:

- The file exists.
- It is inside the Working Directory.
- Git has not started tracking it yet.

---

Now edit:

```
Student.java
```

Git Status:

```
modified: Student.java
```

The file has changed, but the changes are still only in the Working Directory.

---

# 7. Workflow Diagram

```mermaid
flowchart LR
A[Create/Edit/Delete File] --> B[Working Directory]
B --> C[git add]
C --> D[Staging Area]
```

---

# 8. Key Characteristics

- It is your current project folder.
- You work here every day.
- Changes are temporary until staged.
- Git detects changes but does not save them automatically.

---

# 9. Common Mistakes

### Mistake 1

Thinking that saving a file also saves it in Git.

❌ Wrong

Saving a file only updates the Working Directory.

You still need:

```bash
git add
git commit
```

---

### Mistake 2

Thinking Git automatically tracks new files.

❌ Wrong

Git only starts tracking a file after:

```bash
git add filename
```

or

```bash
git add .
```

---

# 10. Interview Questions

### Basic

- What is the Working Directory?
- Where do file changes occur first?

### Intermediate

- Does Git automatically save changes from the Working Directory?
- What does `git status` show?

### Advanced

- Explain the Working Directory using the Git workflow.

---

# 11. Key Takeaways

- The Working Directory is your current project folder.
- All file changes happen here first.
- Git detects changes but does not save them automatically.
- Files must be staged before they can be committed.

---

# Quick Revision

✔ Working Directory = Where you work

✔ Changes happen here first

✔ Git detects changes

✔ Changes are **not** committed yet

✔ Next Step → `git add`

---

# Remember This

```
Working Directory
        │
        ▼
    git add
        │
        ▼
 Staging Area
```

Every Git project starts from the **Working Directory**.