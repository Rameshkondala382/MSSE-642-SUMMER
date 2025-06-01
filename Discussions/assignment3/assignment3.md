# Assignment 3 – Git Activities

## Configuration

1. **Set user name and email:**

    ```bash
    git config --global user.name "Your Name"
    git config --global user.email "your@email.com"
    ```

    *Configure globally if you use the same identity across all repos. Use local config if identity differs per project.*

2. **Set core editor:**

    ```bash
    git config --global core.editor "code --wait"
    ```

3. **View config settings:**

    ```bash
    git config --global --list
    git config --local --list
    ```

---

## Working with a Local Repo

4. **Create a new local repo:**

    ```bash
    mkdir my-repo
    cd my-repo
    git init
    ```

5. **Clone a public repo:**

    ```bash
    git clone https://github.com/octocat/Hello-World.git
    ```

    *Cloning copies an existing repo. Creating starts a new, empty repo.*

6. **Check status:**

    ```bash
    git status
    ```

    *Shows modified, staged, or untracked files.*

7. **Stage changes:**

    ```bash
    git add filename.txt
    ```

    *OR to add all changes:*

    ```bash
    git add .
    ```

8. **Commit changes:**

    ```bash
    git commit -m "Commit message"
    ```

9. **Ignore files using `.gitignore`:**

    ```plaintext
    # .gitignore
    *.log
    node_modules/
    .env
    ```

    *Ignore temp files, secrets, and build artifacts.*

10. **Delete tracked files using Git:**

    ```bash
    git rm filename.txt
    git commit -m "Deleted filename.txt"
    ```

---

## Working with a Remote

11. **View remote:**

    ```bash
    git remote -v
    ```

12. **Function of `git fetch`:**

    ```bash
    git fetch
    ```

    *Downloads updates from remote but does not merge.*

13. **Fetch vs Pull:**

    ```bash
    git fetch
    git pull
    ```

    *`fetch` only downloads; `pull` = `fetch` + `merge`.*

14. **Sync local changes to remote:**

    ```bash
    git checkout -b week4
    # Switched to a new branch 'week4'

    git status
    # On branch week4
    # Untracked files:
    #   Discussions/assignment3/

    git add .

    git commit -m "Initial assignment3 push"
    # [week4 568890d] Initial assignment3 push
    # 1 file changed, 158 insertions(+)
    # create mode 100644 Discussions/assignment3/assignment3.md

    git push origin week4
    ```

---

## Branches

15. **View branches and create new one:**

    ```bash
    git branch        # Before
    git branch feature-branch
    git branch        # After
    # or 
    git checkout -b feature-branch # Creates a new branch and switches to it
    ```

16. **Switch to branch:**

    ```bash
    git checkout feature-branch
    git switch feature-branch
    ```

17. **Delete local branch:**

    ```bash
    git branch -d feature-branch
    git branch        # Confirm deletion
    ```
