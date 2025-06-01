# Git Concept

### Questions

[3. {Interrogate} What happens when you run the git commit command?](./Developing_Questions.md#git-concept-3)

[5. {Interrogate} What does the git branch command do?](./Developing_Questions.md#git-concept-5)

## Concept

[1. {Scan} What is Git and why is it important in software development?](./Developing_Questions.md#git-concept-1)

- 💡 Git is a free and open source distributed version control system
- Git tracks the changes of each file in a working directory.
- It saves change history
- It synchronizes that history with all members
- It helps to fix change conflicts in 1 file.
- It groups changes to each version to release easily.

## Git Commit 

[2. {Scan} In Git, what does a commit represent?](./Developing_Questions.md#git-concept-2)

- Commit a snapshot of all changes in the working directory.

## Git Branch

[4. {Scan} What is a branch in Git and why do we use it?](./Developing_Questions.md#git-concept-4)

- A branch in Git is simply a lightweight movable pointer to one of these commits
- Git branch is a branch of the commit tree

### Pull request

[6. {Scan} What is a pull request and why is it used in team collaboration?](./Developing_Questions.md#git-concept-6)

- Request to merge commit from a branch to another
- It have title and description to make changes meaningful
    - Describe task relate to those changes
- Easy to track and revert if necessary

## Remote Repository

[7. {Scan} What is a remote repository in Git?](./Developing_Questions.md#git-concept-7)

- Cloud storage to save project

# Git Command

## Git Add

[8. {Scan} What is the purpose of the git add command?](./Developing_Questions.md#git-concept-8)

- Add file change into a commit

## Git Fetch

[9. {Scan} What does git fetch do?](./Developing_Questions.md#git-concept-9)

- Retrieves commits, files, branches, and tags from a remote repository.

## Git Merge

[10. {Scan} What does the git merge command accomplish?](./Developing_Questions.md#git-concept-10)

- Combines commit changes from one branch into another branch.

## Git Pull

[11. {Scan} What happens when you run git pull?](./Developing_Questions.md#git-concept-11)

- Fetches updates from a remote repository and immediately merges them into your local branch.

## Git Push

[12. {Scan} What does the git push command do?](./Developing_Questions.md#git-concept-12)

- Sends your local commits to a remote repository.

## Git Rebase

[13. {Scan} What is the purpose of using git rebase?](./Developing_Questions.md#git-concept-13)

- Moves or re-applies commits from one branch onto another, creating a cleaner commit history.
- Moves or "replays" commits from one branch onto another branch.
- Creates a linear history by eliminating the branch point.
- Git Merge:
    - Combines two branches together by creating a new "merge commit."
    - Keeps the history of both branches, showing where they diverged and joined.


## Git Cherry-pick

[14. {Scan} What does git cherry-pick do in Git?](./Developing_Questions.md#git-concept-14)

- Applies a specific commit from one branch to another branch.

## Git Reset

[15. {Scan} What is the git reset command used for?](./Developing_Questions.md#git-concept-15)

- Moves the current branch pointer to a previous commit and optionally changes staged/working directory state.
- Git Reset --soft:
    - Moves the branch pointer to another commit.
    - Keeps all your changes in the staging area (ready to commit).
- Git Reset --hard:
    - Moves the branch pointer to another commit.
    - Deletes all changes in both the staging area and the working directory (completely clean).

## Git Stash

[16. {Scan} What is git stash and when would you use it?](./Developing_Questions.md#git-concept-16)

- Temporarily saves changes that are not ready to commit, allowing you to work on something else.

# Gitflow

### Questions

[2. {Interrogate} How does Gitflow work with CI/CD pipelines?](./Developing_Questions.md#gitflow-2)

## Concept

[1. {Scan} What is Gitflow and why is it used in software development?](./Developing_Questions.md#gitflow-1)

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

[3. {Scan} What is a Feature branch in Gitflow and when do you use it?](./Developing_Questions.md#gitflow-3)

- Each new feature should reside in its own branch.
1. `feature` branches use `develop`as their parent branch.
2. `feature` branches are generally created off to the latest `develop` branch.
3. When a feature is complete, it gets merged back into `develop`.

- 💡 Features should never interact directly with `main`

## Release branch

[4. {Scan} What is a Release branch in Gitflow and what is its purpose?](./Developing_Questions.md#gitflow-4)

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

[5. {Scan} What is a Hotfix branch in Gitflow and when is it needed?](./Developing_Questions.md#gitflow-5)

1. If an issue in `main` is detected a `hotfix` branch is created from `main`
2. Once the `hotfix` is completed it is merged to both `develop` and `main`