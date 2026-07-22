# What is Git?

> **Level:** Beginner

---

# 1. Introduction

Git is a **Distributed Version Control System (DVCS)** used to track changes in files and source code during software development.

It helps developers manage different versions of a project, collaborate with other developers, and maintain a complete history of changes.

Git was created by **Linus Torvalds** in 2005 to manage the development of the Linux kernel.

---

# 2. Why Do We Need Git?

Imagine you're working on a Java project.

Day 1:
You complete the Login feature.

Day 2:
You add Registration.

Day 3:
You accidentally delete half of your project.

Without Git:
- You may lose your work permanently.
- You cannot go back to a previous working version.

With Git:
- Every saved version (commit) is stored.
- You can restore any previous version at any time.
- You always know what changed, when it changed, and who changed it.

---

# 3. What is Version Control?

Version Control is the process of managing and tracking changes made to files over time.

Every time you save an important milestone, Git creates a new version called a **Commit**.

Example:

```
Version 1 → Login Page
       ↓
Version 2 → Registration Added
       ↓
Version 3 → Forgot Password Added
       ↓
Version 4 → Dashboard Added
```

If Version 4 contains a bug, you can return to Version 3.

---

# 4. How Does Git Work?

Git maintains a complete history of your project.

Whenever you make changes and create a commit:

- Git records the changes.
- Git stores them in a local repository.
- Git allows you to restore any previous version.

Unlike cloud storage, Git stores the complete history, not just the latest files.

---

# 5. Features of Git

- Tracks every change made to files.
- Maintains complete version history.
- Allows multiple developers to work together.
- Supports branching and merging.
- Enables rollback to previous versions.
- Fast and lightweight.
- Distributed (works offline).

---

# 6. Advantages of Git

- Prevents accidental loss of code.
- Makes collaboration easier.
- Maintains project history.
- Easy to experiment using branches.
- Industry-standard version control system.

---

# 7. Real-Life Example

Imagine you're writing a book.

Instead of saving files like:

```
Book_Final.docx
Book_Final_Final.docx
Book_Final_Updated.docx
Book_Final_Last.docx
```

Git keeps all versions automatically.

Whenever you finish a chapter, you create a **Commit**.

If you make a mistake later, you can return to any previous version without creating dozens of duplicate files.

---

# 8. Common Uses of Git

- Software Development
- Web Development
- Mobile App Development
- Documentation
- Configuration Files
- DevOps Projects

---

# 9. Common Misconceptions

### Git is not GitHub.

Git is software installed on your computer.

GitHub is an online platform used to host Git repositories.

---

### Git is not cloud storage.

Git stores version history.

Cloud storage stores only the latest version of your files.

---

# 10. Interview Questions

### Basic

- What is Git?
- Why do we use Git?
- What is Version Control?
- What are the advantages of Git?

### Intermediate

- Why is Git called a Distributed Version Control System?
- How does Git track changes?

---

# 11. Key Takeaways

- Git is a Distributed Version Control System (DVCS).
- Git tracks changes in files and source code.
- Git stores complete project history.
- Git allows developers to restore previous versions.
- Git enables collaboration among multiple developers.
- Git works offline because every developer has a complete copy of the repository.

---

# Quick Revision

- Git = Version Control System
- Tracks changes in files
- Stores project history
- Supports collaboration
- Works offline
- Created by Linus Torvalds (2005)

---

# Important Note

Git is a **tool**.

It runs on your local computer and helps you manage your project's history.

Git does **not** require GitHub to work.