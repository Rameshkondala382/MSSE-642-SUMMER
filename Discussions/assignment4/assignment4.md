# Assignment 4 Workflow

## Branching and Cleanup Workflow

### 1. Create and switch to a new branch

```bash
git checkout -b assn4
```

### 2. Stage all changes

```bash
git add .
```

### 3. Push changes (Note: should push to 'assn4', not 'main')

```bash
git push origin assn4
```

![Initial new branch screenshot](assets/initNewBranch.jpg)

### 4. Switch back to main and pull latest changes

```bash
git switch main
git pull
```

![Local Pull/Merge](assets/vsPull.jpg)

### 5. Delete local branch after merging or completing work

```bash
git branch -D assn4
```

## Git UI PR

![GIT CreatePR](assets/gitPR.jpg)
![GIT Squash and Merge PR](assets/gitPR2.jpg)
![GIT Delete Remote Branch](assets/gitDRemote.jpg)