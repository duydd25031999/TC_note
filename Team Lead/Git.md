# Git

-💡 Git is a free and open source distributed version control system

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

- 

## Git Pull

## Git Push

## Git Rebase

## Git Cherry-pick

## Git Reset

## Git Stash

# Gitflow

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

-💡 Features should never interact directly with `main`

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