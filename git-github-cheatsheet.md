# Git and GitHub Cheat Sheet

> **Goal:** Understand how Git and GitHub work together so you can save code locally, share it online, and work with others.

Git is the tool on your computer that tracks changes.
GitHub is the website where you store Git projects, review changes, and collaborate.

## The Short Version

| Tool | What It Does |
|---|---|
| Git | Tracks changes on your machine |
| GitHub | Stores Git projects online and helps teams work together |

If you remember one thing, remember this: **Git saves the work, GitHub shares the work**.

## How The Two Work Together

1. You make changes in a project.
2. Git tracks those changes and saves them as commits.
3. You push the commits to GitHub.
4. Other people review the work, open pull requests, and merge it.

## Git Basics

| Command | Clear Description |
|---|---|
| `git init` | Start a new Git repository here. |
| `git clone [url]` | Copy a project from a URL. |
| `git status` | Show what changed. |
| `git add [file]` | Prepare one file to save. |
| `git add .` | Prepare all changes to save. |
| `git commit -m "message"` | Save what you prepared. |
| `git branch` | Show your branches. |
| `git switch [branch]` | Go to a different branch. |
| `git switch -c [branch]` | Create and go to a new branch. |
| `git merge [branch]` | Combine another branch here. |
| `git log` | See past commits. |
| `git diff` | Show changes you have not prepared yet. |
| `git push [remote] [branch]` | Send your commits online. |
| `git pull [remote] [branch]` | Get and merge changes from online. |

## GitHub Basics

| Item | Clear Description |
|---|---|
| `Repository` | Online home for a project. |
| `Pull request` | Ask to merge changes from one branch into another. |
| `Issue` | Track a bug, task, or idea. |
| `Review` | Read code and leave feedback. |
| `Approve` | Say a change is ready to merge. |
| `Branch protection` | Add rules so important branches are harder to break. |
| `GitHub Actions` | Run automated tests and builds. |

## Most Useful Extras For DevOps

These are the extra topics that help most when you are working on deployments, releases, and production issues.

| Topic | Clear Description |
|---|---|
| `Merge conflict` | Happens when Git cannot combine two sets of changes automatically. |
| `git rebase` | Replays your commits on top of another branch to keep history cleaner. |
| `git revert` | Creates a new commit that undoes an old commit. Safer for shared branches. |
| `Tag` | A label for a specific commit, often used for releases. |
| `Release` | A GitHub page that groups a version, notes, and attached files. |
| `Environment` | A GitHub target such as dev, staging, or production. |

## When To Use These

| Situation | Best Tool |
|---|---|
| Fix a bad commit on a shared branch | `git revert` |
| Clean up your local branch before merge | `git rebase` |
| Mark version `v1.2.0` for deployment | `git tag` |
| Explain what changed in a deployment | GitHub Release |
| Handle a conflict during a merge | Resolve the merge conflict and commit the result |

Example:

```bash
git tag v1.2.0
git push origin v1.2.0
git revert [commit]
```

## Merge Conflicts In Simple Words

If two people change the same lines, Git may stop and ask you to choose the final version.

1. Open the file with the conflict.
2. Keep the correct lines.
3. Remove the conflict markers.
4. Save the file and commit the result.

## Rebase, Revert, And Reset

| Command | Clear Description |
|---|---|
| `git rebase [branch]` | Move your work on top of another branch. Good for a cleaner history. |
| `git revert [commit]` | Undo a commit safely by adding a new commit. |
| `git reset HEAD~1` | Move your branch back one commit. Use only when you know it is safe. |

## Common Workflow

1. Clone the repository from GitHub.
2. Create a branch for your work.
3. Make changes and commit them with Git.
4. Push the branch to GitHub.
5. Open a pull request.
6. Review, approve, and merge the change.

Example:

```bash
git clone [url]
git switch -c feature-login
git add .
git commit -m "Add login screen"
git push origin feature-login
```

## Git vs GitHub

| Question | Git | GitHub |
|---|---|---|
| Do I need it on my computer? | Yes | No |
| Does it track file changes? | Yes | It stores them |
| Does it help with pull requests? | No | Yes |
| Does it work offline? | Yes | Not fully |
| Is it a website? | No | Yes |

## Where DevOps Engineers Use This

Use Git and GitHub together when you want a safe history of infrastructure, deployment, and application changes.

- Track Terraform, Ansible, Kubernetes, and app code in Git.
- Review pull requests before production changes are merged.
- Run CI/CD pipelines with GitHub Actions.
- Roll back or compare releases when something breaks.
- Use tags and releases to mark production versions.
- Resolve merge conflicts when several people change the same file.

## Fast Summary

| If You Want To... | Use |
|---|---|
| save code on your machine | Git |
| share code online | GitHub |
| review changes with others | GitHub |
| keep a history of work | Git |
