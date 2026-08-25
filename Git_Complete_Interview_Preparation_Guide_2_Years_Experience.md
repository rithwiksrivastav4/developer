# Git Complete Interview Preparation Guide (2 Years Experience)

## 1. What is Git?

Git is a distributed version control system used to track source code
changes, manage versions, collaborate with teams, and maintain project
history.

## Why Git?

-   Track code changes
-   Restore previous versions
-   Work with multiple developers
-   Manage feature development
-   Support CI/CD workflows

------------------------------------------------------------------------

# 2. Git Architecture

    Working Directory
            |
            |
            v
    Staging Area
            |
            |
            v
    Local Repository
            |
            |
            v
    Remote Repository

## Working Directory

Current files where developers make changes.

## Staging Area

Temporary area where changes are prepared before commit.

## Local Repository

Local Git history stored on developer machine.

## Remote Repository

Shared repository like GitHub, GitLab, Bitbucket.

------------------------------------------------------------------------

# 3. Git Installation and Configuration

Check version:

``` bash
git --version
```

Configure username:

``` bash
git config --global user.name "Your Name"
```

Configure email:

``` bash
git config --global user.email "your@email.com"
```

View configuration:

``` bash
git config --list
```

------------------------------------------------------------------------

# 4. Creating Repository

Initialize repository:

``` bash
git init
```

Clone repository:

``` bash
git clone repository_url
```

Example:

``` bash
git clone https://github.com/company/project.git
```

------------------------------------------------------------------------

# 5. Git Status

Check current changes:

``` bash
git status
```

Shows:

-   Modified files
-   New files
-   Staged files

------------------------------------------------------------------------

# 6. Git Add Commands

Add single file:

``` bash
git add filename
```

Add all files:

``` bash
git add .
```

Add modified files:

``` bash
git add -u
```

------------------------------------------------------------------------

# 7. Git Commit

Create commit:

``` bash
git commit -m "Added login feature"
```

View commits:

``` bash
git log
```

Short log:

``` bash
git log --oneline
```

------------------------------------------------------------------------

# 8. Git Branch Concepts

A branch is an independent line of development.

Create branch:

``` bash
git branch feature-login
```

List branches:

``` bash
git branch
```

Switch branch:

``` bash
git checkout feature-login
```

Modern command:

``` bash
git switch feature-login
```

Create and switch:

``` bash
git checkout -b feature-login
```

------------------------------------------------------------------------

# 9. Branching Strategy

Common company workflow:

    main
     |
    develop
     |
    feature branch
     |
    bugfix branch

Example:

    main
     |
    develop
     |
    feature/payment

------------------------------------------------------------------------

# 10. Git Merge

Merge combines branch changes.

Example:

``` bash
git checkout main

git merge feature-login
```

Types:

## Fast Forward Merge

No extra commit created.

Example:

    main
     |
     A---B---C

    after merge

    A---B---C
            |
          main

## Three Way Merge

Creates merge commit when branches have different histories.

------------------------------------------------------------------------

# 11. Merge Conflict

Occurs when Git cannot automatically combine changes.

Example:

Developer A:

    Login button text

Developer B:

    Login button color

Both changed same lines.

Resolve:

1.  Open conflict file
2.  Fix changes
3.  Add file

``` bash
git add file

git commit
```

------------------------------------------------------------------------

# 12. Git Rebase

Rebase moves commits on top of another branch.

Command:

``` bash
git rebase main
```

Difference:

Merge:

-   Creates merge commit
-   Preserves history

Rebase:

-   Creates cleaner history
-   Rewrites commits

------------------------------------------------------------------------

# 13. Git Reset

Moves HEAD pointer.

## Soft Reset

Keeps changes staged.

``` bash
git reset --soft HEAD~1
```

## Mixed Reset

Default reset.

``` bash
git reset HEAD~1
```

## Hard Reset

Deletes changes.

``` bash
git reset --hard HEAD~1
```

Warning:

    Deleted changes cannot be recovered easily

------------------------------------------------------------------------

# 14. Git Revert

Creates a new commit that reverses previous commit.

Command:

``` bash
git revert commit_id
```

Difference:

Reset:

-   Removes history

Revert:

-   Keeps history

------------------------------------------------------------------------

# 15. Git Stash

Temporarily saves changes.

Save:

``` bash
git stash
```

List:

``` bash
git stash list
```

Apply:

``` bash
git stash apply
```

Remove stash:

``` bash
git stash drop
```

------------------------------------------------------------------------

# 16. Git Cherry Pick

Copies specific commit into current branch.

Command:

``` bash
git cherry-pick commit_id
```

Example:

A bug fix exists in another branch.

Copy only that fix:

``` bash
git cherry-pick abc123
```

------------------------------------------------------------------------

# 17. Remote Repository Commands

View remote:

``` bash
git remote -v
```

Add remote:

``` bash
git remote add origin URL
```

Push:

``` bash
git push origin branch_name
```

Pull:

``` bash
git pull
```

Fetch:

``` bash
git fetch
```

Difference:

Pull:

-   Fetch + Merge

Fetch:

-   Downloads changes only

------------------------------------------------------------------------

# 18. Git Push Commands

First push:

``` bash
git push -u origin main
```

Normal push:

``` bash
git push
```

Force push:

``` bash
git push --force
```

Use carefully.

------------------------------------------------------------------------

# 19. Git Tags

Create tag:

``` bash
git tag v1.0
```

Push tag:

``` bash
git push origin v1.0
```

Used for:

-   Releases
-   Production versions

------------------------------------------------------------------------

# 20. Git Ignore

File:

    .gitignore

Example:

    node_modules/
    .env
    dist/
    build/

Purpose:

Prevent unwanted files from being committed.

------------------------------------------------------------------------

# 21. Git Diff

View changes:

``` bash
git diff
```

Staged changes:

``` bash
git diff --staged
```

------------------------------------------------------------------------

# 22. Git Log Commands

Complete history:

``` bash
git log
```

One line:

``` bash
git log --oneline
```

Graph:

``` bash
git log --graph --oneline
```

Specific author:

``` bash
git log --author="name"
```

------------------------------------------------------------------------

# 23. Git Reflog

Shows all HEAD movements.

Command:

``` bash
git reflog
```

Useful for recovering lost commits.

------------------------------------------------------------------------

# 24. Git Workflow in Companies

Typical flow:

    Developer

     |

    Feature Branch

     |

    Pull Request

     |

    Code Review

     |

    Merge Develop

     |

    Testing

     |

    Merge Main

     |

    Production Release

------------------------------------------------------------------------

# 25. Git Interview Scenario Questions

## Q1. You committed wrong code. How to undo?

Answer:

If not pushed:

``` bash
git reset --soft HEAD~1
```

If already pushed:

``` bash
git revert commit_id
```

------------------------------------------------------------------------

## Q2. Difference between reset and revert?

Reset:

-   Deletes commits
-   Changes history

Revert:

-   Creates new undo commit
-   Safe for shared branches

------------------------------------------------------------------------

## Q3. You pushed password accidentally. What will you do?

Steps:

1.  Remove secret.
2.  Revoke password/token.
3.  Remove from history using tools like git filter-repo.
4.  Force push if required.

------------------------------------------------------------------------

## Q4. Developer A and Developer B changed same file. What happens?

Answer:

Git creates merge conflict.

Resolve:

-   Review changes
-   Keep required code
-   Commit resolution

------------------------------------------------------------------------

## Q5. Difference between merge and rebase?

Merge:

-   Keeps complete history
-   Creates merge commit

Rebase:

-   Cleaner history
-   Rewrites commits

------------------------------------------------------------------------

## Q6. Accidentally deleted branch. How recover?

Use:

``` bash
git reflog
```

Find commit:

``` bash
git checkout -b branch_name commit_id
```

------------------------------------------------------------------------

## Q7. Local changes are blocking git pull. What to do?

Options:

Commit:

``` bash
git add .
git commit
git pull
```

Or stash:

``` bash
git stash
git pull
git stash pop
```

------------------------------------------------------------------------

## Q8. Difference between git pull and git fetch?

Fetch:

-   Downloads changes only

Pull:

-   Downloads and merges changes

------------------------------------------------------------------------

## Q9. Production has bug. How create hotfix?

Flow:

    main

     |

    hotfix branch

     |

    Fix

     |

    Merge

     |

    Production

Commands:

``` bash
git checkout main

git checkout -b hotfix/login

git commit

git merge hotfix/login
```

------------------------------------------------------------------------

## Q10. What happens internally during git commit?

Git:

1.  Takes staged files.
2.  Creates snapshot.
3.  Generates commit hash.
4.  Updates HEAD pointer.

------------------------------------------------------------------------

# 26. Advanced Git Concepts

## HEAD

Pointer to current branch commit.

Example:

    HEAD -> main -> commit

------------------------------------------------------------------------

## Detached HEAD

When HEAD points directly to commit.

Example:

``` bash
git checkout commit_id
```

------------------------------------------------------------------------

## Fork

Copy of repository under another account.

Used in open source.

------------------------------------------------------------------------

## Pull Request

Request to merge code changes.

Includes:

-   Code review
-   Discussions
-   Approval

------------------------------------------------------------------------

# 27. Git Best Practices

-   Create meaningful commits
-   Do not commit secrets
-   Pull before starting work
-   Use feature branches
-   Review code before merge
-   Write clear commit messages
-   Avoid force push on shared branches

------------------------------------------------------------------------

# 28. Git Commands Cheat Sheet

``` bash
git init
git clone
git status
git add
git commit
git push
git pull
git fetch
git branch
git checkout
git switch
git merge
git rebase
git reset
git revert
git stash
git cherry-pick
git tag
git log
git diff
git reflog
```

------------------------------------------------------------------------

# 29. 2 Years Experience Git Interview Expectations

Must know:

-   Git workflow
-   Branching strategy
-   Merge conflicts
-   Rebase
-   Reset vs revert
-   Cherry-pick
-   Stash
-   Pull request workflow
-   Code review process
-   Git recovery techniques
-   Git with CI/CD pipelines
