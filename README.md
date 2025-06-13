# User Login System – Git Flow Implementation

This repo demonstrates the implementation of a **User Login System** using **Git Flow**.

---

## 📚 Task Breakdown & Git Commands

### Set Up Repository

On GitHub, Got to Repositories, Click New, Enter a valid Repository Name, then create a repository.

Then on VS Code: 

```bash
git clone "your-repository"
git init
```

### Create main branch and add file
```bash
git checkout -b main
echo "f1" >> f1
git add f1
git commit -m "Initial commit on main with f1"
git push "your-repository" main
```

### Create development branch
```bash
git checkout -b dev
git push -u "your-repository" dev
```

### Initialize Git Flow 
```bash
git flow init
```

### Create Feature branch from dev branch
```bash
git flow feature start login
echo "Implement the login functionality" >> f1
git add f1
git flow feature finish login
```
Feature branch was deleted and merged to dev.

### Create release branch from dev branch
```bash
git flow release start _version
```
### Go to feature branch and add 3 commits
```bash
git checkout -b feature

echo "Case 1" >> f1
git add f1
git commit -m "Case 1 added"

echo "Case 2" >> f1
git add f1
git commit -m "Case 2 added"

echo "Case 3" >> f1
git add f1
git commit -m "Case 3 added"

git push "your-repository" feature
```

### View History and Commits IDs
```bash
git log --oneline
```
Then, Get the Case 1 and Case 2 commits' IDs

### Merge only Case 1 and Case 2 to the release branch
First, return to the Release Branch
```bash
git checkout release_version

git merge "Case_1-commit-ID"
git merge "Case_2-commit-ID"
```

### Merge release branch into the main branch
```bash
git checkout main
git merge release_version
```

### Merge release branch (back) into the dev branch
Tried to use "git flow release finish _version", but did not work, so I did the following:
```bash
git checkout dev
git merge release_version
```

### Delete release branch
```bash
git branch -d release_version
```

### Create HotFix branch from main
```bash
git flow hotfix start issue
```

### Identify and fix a security issue in the login system
```bash
echo "Identify and fix a security issue in the login system" >> f1
git add f1
git commit -m "Issue Fixed"
```

### Merge the HotFix into both main & dev then delete it
```bash
git flow hotfix finish issue
```

### Pushing the rest branches
```bash
git push "your-repository" dev
git push "your-repository" main
```

### Delete Case 2 Commit from dev branch 
```bash
git checkout dev
git log --oneline
git rebase -i HEAD~3
```
Then, delete the Case 2 commit line.
