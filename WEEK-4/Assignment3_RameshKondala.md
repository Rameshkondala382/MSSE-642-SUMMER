# WEEK-4 :  ASSIGNMENT #3


# ACTIVITY 1:


 # Configuratinon

1. What are the commands to configure your user.name and your user.email. Should this be configured globally or in your repo. Why or why not?
 configure  Git username and email




```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```




**Should this be configured globally or in your repo. Why or why not?**

Use `--global` to set this for all repositories on your system.
To set only for a specific repository for different identities for different projects.

```bash
git config user.name "Your Name"
git config user.email "your.email@example.com"
```



How do you configure the core editor for git?
```bash
To set the default text editor for Git
git config --global core.editor "nano"
```
Replace `"nano"` with your preferred editor, e.g., `"vim"`, `"code --wait"` for VS Code.


How do you view your global config and your local (for the repo) config?
global config:
```bash
git config --global --list
```

local config:
```bash
git config --list --local
```
all effective config:
```bash
git config --list
```
only username/email:
```bash
git config user.name
git config user.email
```


# Working with a local repo

What are the steps to create a new local repo via the CLI?
To Create a New Local Repo
```bash
mkdir my-new-repo
cd my-new-repo
git init
```
How do you clone a repo and what's the difference between cloning and creating a new repo from scratch? Practice cloning a public repo from somewhere.
```bash
git clone https://github.com/user/repo.git
```
Cloning copies an existing remote repository including its history to the local machine.
Creating a new repo (`git init`) starts a fresh, empty repository.

How do you look at the status of your repo? What information does this give you?
Shows changes staged for commit, changes not staged, and untracked files.
```bash
git status
```

How do you stage changes to your local repo in prepartion for a commit?
```bash
git add filename.txt
```
stage all changes:
```bash
git add .
```

How do you commit changes to your local repo?
```bash
git commit -m "Describe your changes"
```

Include an example of a file that will allow you to "ignore" files in your repo. What kinds of files should not be part of your version control?
Create a `.gitignore` file:
```bash
# .gitignore example
*.log
node_modules/
.DS_Store
```

When files are under version control, you can't delete them using the OS commands. How do you delete files using git.
file is deleted from both  working directory and version control.
```bash
git rm unwanted-file.txt
git commit -m "Remove unwanted file"
```

# Working with a remote

How do you view the remote repo that is associated with your local repo?
```bash
git remote -v
```
Lists the URLs of remotes associated with the local repo.


What is the function of the git fetch command?
        Downloads new data from the remote but does not merge it into your current branch.

What is the difference between fetch and pull. Practice using both and show the results?
    Difference: Fetch vs Pull
        Downloads changes, does NOT update working branch
        Downloads and merges changes into current branch

Make some changes in your repo and using the command line to sync those changes with your remote repo. Show the results?
```bash
git add .
git commit -m "Your changes"
git push
```



# Branches

How do you view the local and the remote branches for your repositories?
```bash
git branch        # Local branches
git branch -r     # Remote branches
git branch -a     # All branches
```

View the local branches and create a new branch. Look again. Show before and after.
Create and View New Branch
```bash
git branch        # Before
git checkout -b feature-branch
git branch        # After
```

What are different ways to switch to a new branch?
```bash
git checkout branch-name
```
```bash
git switch branch-name
```


Delete your local branch without pushing to a remote or merging to your main branch. Show that it's gone.
```bash
git branch -d branch-name
#  -D to force delete if branch is not merged
git branch        # it's gone
```


