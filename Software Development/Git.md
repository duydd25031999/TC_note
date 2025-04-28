# Git

### Questions

[1. What is Git and why is it important in software development?](./Developing_Questions.md#git-concept-1)

[2. In Git, what does a commit represent?](./Developing_Questions.md#git-concept-2)

[3. What happens when you run the git commit command?](./Developing_Questions.md#git-concept-3)

[4. What is a branch in Git and why do we use it?](./Developing_Questions.md#git-concept-4)

[5. What does the git branch command do?](./Developing_Questions.md#git-concept-5)

[6. What is a pull request and why is it used in team collaboration?](./Developing_Questions.md#git-concept-6)

[7. What is a remote repository in Git?](./Developing_Questions.md#git-concept-7)

[8. What is the purpose of the git add command?](./Developing_Questions.md#git-concept-8)

[9. What does git fetch do?](./Developing_Questions.md#git-concept-9)

[10. What does the git merge command accomplish?](./Developing_Questions.md#git-concept-10)

[11. What happens when you run git pull?](./Developing_Questions.md#git-concept-11)

[12. What does the git push command do?](./Developing_Questions.md#git-concept-12)

[13. What is the purpose of using git rebase?](./Developing_Questions.md#git-concept-13)

[14. What does git cherry-pick do in Git?](./Developing_Questions.md#git-concept-14)

[15. What is the git reset command used for?](./Developing_Questions.md#git-concept-15)

[16. What is git stash and when would you use it?](./Developing_Questions.md#git-concept-16)

## Concept

- 💡 Git is a free and open source distributed version control system
- Git tracks the changes of each file in a working directory.
- It saves change history
- It synchronizes that history with all members
- It helps to fix change conflicts in 1 file.
- It groups changes to each version to release easily.

## Git Commit 

- Commit a snapshot of all changes in the working directory.

## Git Branch

- A branch in Git is simply a lightweight movable pointer to one of these commits
- Git branch is a branch of the commit tree

## Pull request

- Request to merge commit from a branch to another
- It have title and description to make changes meaningful
    - Describe task relate to those changes
- Easy to track and revert if necessary

## Remote Repository

- Cloud storage to save project

# Git Command

## Git Add

- Add file change into a commit

## Git Fetch

- Retrieves commits, files, branches, and tags from a remote repository.

## Git Merge

- Combines commit changes from one branch into another branch.

## Git Pull

- Fetches updates from a remote repository and immediately merges them into your local branch.

## Git Push

- Sends your local commits to a remote repository.

## Git Rebase

- Moves or re-applies commits from one branch onto another, creating a cleaner commit history.
- Moves or "replays" commits from one branch onto another branch.
- Creates a linear history by eliminating the branch point.
- Git Merge:
    - Combines two branches together by creating a new "merge commit."
    - Keeps the history of both branches, showing where they diverged and joined.


## Git Cherry-pick

- Applies a specific commit from one branch to another branch.

## Git Reset

- Moves the current branch pointer to a previous commit and optionally changes staged/working directory state.
- Git Reset --soft:
    - Moves the branch pointer to another commit.
    - Keeps all your changes in the staging area (ready to commit).
- Git Reset --hard:
    - Moves the branch pointer to another commit.
    - Deletes all changes in both the staging area and the working directory (completely clean).

## Git Stash

- Temporarily saves changes that are not ready to commit, allowing you to work on something else.

# Gitflow

### Questions

[1. What is Gitflow and why is it used in software development?](./Developing_Questions.md#gitflow-1)

[2. How does Gitflow work with CI/CD pipelines?](./Developing_Questions.md#gitflow-2)

[3. What is a Feature branch in Gitflow and when do you use it?](./Developing_Questions.md#gitflow-3)

[4. What is a Release branch in Gitflow and what is its purpose?](./Developing_Questions.md#gitflow-4)

[5. What is a Hotfix branch in Gitflow and when is it needed?](./Developing_Questions.md#gitflow-5)

## Concept

- Gitflow is a Git workflow for managing Git branches.
- Based on trunk-based workflows.
    - The best practices for modern continuous software development and DevOps practices.
- Gitflow also can be challenging to use with CI/CD.
- Instead of a single `main` branch, this workflow uses a lot of branches to record the history of the project.
- It has at least 2 important branches.
    - The `main` branch stores the official release history
    - The `develop` branch serves as an integration branch for features.
- It's also convenient to tag all commits in the `main` branch with a version number.

## Feature branch

- Each new feature should reside in its own branch.
1. `feature` branches use `develop`as their parent branch.
2. `feature` branches are generally created off to the latest `develop` branch.
3. When a feature is complete, it gets merged back into `develop`.

- 💡 Features should never interact directly with `main`

## Release branch

1. Fork a `release` branch off of `develop`.
    - Once `develop` has acquired enough features for a release (or a predetermined release date is approaching)
2. Do test on `release` branch to ensure quality before merging into `main` branch
3. We can continue to do other features in backlogs with its own branch.
    - But we aren’t able to merge new features into the `develop` branch until the tester team finishing test execution.
4. Testers find the bug list of that release and let the developer fix them.
    - Developer fix bug on independent branch created off `develop` branch
    - Merge into `develop` branch
    - After fix all bugs, `develop` branch is merged into that `release` branch.
    - Notify the tester to check again
    - This loop will repeat until the release is complete to put into production
5. `release` branch is merge to `main` branch.

## Hotfix branch

1. If an issue in `main` is detected a `hotfix` branch is created from `main`
2. Once the `hotfix` is completed it is merged to both `develop` and `main`