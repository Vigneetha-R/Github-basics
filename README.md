
# 📚 Git & GitHub Comprehensive Guide (VCS Fundamentals)

## About This Repository

This repository serves as a structured, personal reference guide for mastering Git and GitHub—essential tools for version control, collaboration, and managing code history in any technical field, especially Data Science.

## Why Version Control is Essential (Data Science Focus)

* **Reproducibility:** Tracking specific versions of data, models, and code (e.g., committing a model with its corresponding accuracy score).
* **Collaboration:** Working with engineering teams to deploy models or sharing research with collaborators via controlled branches.
* **Project Management:** Managing large-scale projects, ensuring atomic changes, and maintaining a clean history.

***

## 💡 Key Terminology

| Term | Definition |
| :--- | :--- |
| **Git** | A **Free and Open-Source Distributed Version Control System (VCS)**. It's a tool that tracks and manages changes to files over time. |
| **GitHub** | A **website/platform** used to host remote Git repositories online. It facilitates collaboration. |
| **Repository (Repo)** | The project folder, or the place where your project and its entire history are kept. Can be local or remote. |
| **Working Directory** | The current folder on your local machine where you make changes. |
| **Staging Area** | An intermediate area where you prepare changes before committing them (using `git add`). |
| **Commit** | A snapshot of your changes at a specific point in time. It's like saving a specific version of your project. |
| **CLI (Command Line Interface)** | The terminal or command line used to interact with Git via text commands. |
| **Branch** | A parallel version of the repository that allows developers to work on new features or fixes without affecting the main codebase (`master`/`main`). |

***

## ⚙️ Core Git Commands (Local Machine)

| Command | Purpose | Example |
| :--- | :--- | :--- |
| `git init` | Initializes a new Git repository in the current directory. | `git init` |
| `git clone` | Downloads a remote repository (like one hosted on GitHub) to your local machine. | `git clone <repo_url>` |
| `git add` | Tracks files and adds changes to the **Staging Area**, preparing them for the next commit. | `git add README.md` or `git add .` (for all files) |
| `git commit` | Permanently saves the staged files as a new snapshot in the Git history with a descriptive message. | `git commit -m "Updated data processing script"` |
| `git status` | Shows the state of the working directory and staging area (which files are modified, staged, or untracked). | `git status` |
| `git log` | Displays the entire commit history for the current branch, including commit IDs and messages. | `git log` |
| `cd` | **C**hange **D**irectory (a common CLI command, not Git-specific but essential). | `cd my_project_repo` |

***

## 🌳 Git Branching

👉 [View the Git Branching Diagram](./branching-diagram.md)

### Understanding the Branching Diagram Logic

* **Main Branch:** This is the **Master Branch** where all stable code lives (Commits 1, 2, 3, 4).
* **Feature Branch:** A new, longer-term project started at Commit 3 (Feature Commit 1, 2).
* **Hotfix Branch:** A quick, emergency fix started at Commit 4. The hotfix was merged **first** because it's urgent, and the Feature branch was merged **later** (Final Merge).

### Branch Commands

| Action | Command | Result |
| :--- | :--- | :--- |
| **Create & Switch** | `git checkout -b feature-readme` | Creates a new branch named `feature-readme` AND switches to it. |
| **Switch Back** | `git checkout master` | Switches your files back to the stable `master` branch. |
| **Integrate Changes** | `git merge feature-readme` | **Copies** the final changes from the feature branch onto your current branch (like the `master` branch). |
| **Check File Status** | `git status` | Shows what files you've modified in the current branch. |
| **Check Differences** | `git diff master` | Displays **what** changes you made in the current branch compared to `master`. |
| **Delete Branch** | `git branch -d feature-readme` | Deletes the local branch (after the code is safely merged). |

### Example Workflow: Testing Your Changes

1.  **Start a new branch:** `git checkout -b feature-update-readme`
2.  **Modify a file:** (e.g., edit `README.md`)
3.  **Save the change:** `git add Readme.md` then `git commit -m "updated readme"`
    * *Result:* The change is **only saved** on the feature branch.
4.  **Check master:** `git checkout master`. **You won't see the changes** in the README file on master.

### The Local-to-Remote Workflow

| Step | Location | Command / Action | Key Result |
| :--- | :--- | :--- | :--- |
| **1. Upload** | Local | `git push -u origin feature-readme` | Uploads the new branch and its commits to GitHub. |
| **2. Merge Request** | GitHub | **Make a Pull Request (PR)** | You ask for your feature to be reviewed and merged into `master`. |
| **3. Sync Master** | Local | `git checkout master` → `git pull` | Downloads the changes that were just merged on GitHub to your local `master`. |

***

## 💥 Troubleshooting (What to Do When Errors Happen)

| Error/Problem | Why it Happens | Solution (The Simple Fix) |
| :--- | :--- | :--- |
| **Cannot switch branches** | You modified files but didn't save them. Git stops the switch to prevent losing your work. | Run `git status`. Then, `git commit -am "added my changes"` to save them before switching. |
| **Merge Conflict** | Changes were made to the **SAME LINE** of the **SAME FILE** in both branches. | Manually edit the file to keep the final code you want, then run `git add <file>` and `git commit -am "resolved conflict"`. |
| **Accidental `git add`** | You added files to the staging area too early. | `git reset <file>` (Removes the file from the staging area but keeps your changes). |
| **Undo Commit** | You need to revert back to a clean state (**use with caution**). | `git reset --hard <commit ID>` |

### Forking (Contributing to External Repositories)

* **Purpose:** If you want to contribute to someone else's public repository where you don't have direct push access.
* **Action:**
    1.  **Fork:** On GitHub, click the "Fork" button on the original repository. This creates a complete copy of their repository under **your** GitHub account.
    2.  **Clone:** Clone *your forked repository* to your local machine: `git clone <your_fork_url>`.
    3.  **Develop:** Make your changes, commit them, and push them to *your forked repository*.
    4.  **Pull Request:** From your forked repository on GitHub, create a **Pull Request** back to the *original repository*. This requests the original owner to review and merge your contributions.

