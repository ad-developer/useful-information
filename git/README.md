# Git Commands Cheat Sheet

## Basic Git Commands

### 1. Initialize a Repository
```sh
git init
```
Initializes a new Git repository.

### 2. Clone a Repository
```sh
git clone <repository_url>
```
Clones an existing repository from a URL.

### 3. Check Repository Status
```sh
git status
```
Displays the state of the working directory and staging area.

### 4. Add Files to Staging Area
```sh
git add <file_name>
```
Adds a file to the staging area. Use `git add .` to add all files.

### 5. Commit Changes
```sh
git commit -m "commit message"
```
Commits the staged changes with a message.

### 6. View Commit History
```sh
git log
```
Shows the commit history.

### 7. Create a New Branch
```sh
git branch <branch_name>
```
Creates a new branch.

### 8. Switch to a Branch
```sh
git checkout <branch_name>
```
Switches to the specified branch.

### 9. Create a New Branch and Switch to New Branch
```sh
git checkout -b <branch_name>
```
Creates a new branch and switches to new branch.

### 10. Merge a Branch
```sh
git merge <branch_name>
```
Merges the specified branch into the current branch.

### 11. Push Changes to Remote Repository
```sh
git push origin <branch_name>
```
Pushes the changes to the remote repository.

### 12. Pull Changes from Remote Repository
```sh
git pull
```
Fetches and merges changes from the remote repository.

### 13. Fetch a Branch
```sh
git fetch <branch_name>
```
Fetch the specified branch.


### 14. Delete a Branch
```sh
git branch -d <branch_name>
```
Deletes the specified branch.



## Additional Resources
- [Official Git Documentation](https://git-scm.com/doc)
- [GitHub Guides](https://guides.github.com/)
