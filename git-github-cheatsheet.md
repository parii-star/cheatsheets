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

## Complete Git Commands Reference

| Command | Short Description | Example Usage | Expected Output |
| --- | --- | --- | --- |
| `cd folder-name` | Move into folder | `cd ~/Documents/cheatsheets` | Terminal moves into folder |
| `git init` | Initialize Git repository | `git init` | `Initialized empty Git repository` |
| `git status` | Check repo status | `git status` | Shows staged/unstaged files |
| `git add .` | Stage current files | `git add .` | No output if successful |
| `git add -A` | Stage all changes including deletions | `git add -A` | No output |
| `git commit -m "msg"` | Create commit | `git commit -m "Initial commit"` | `[main abc123] Initial commit` |
| `git config --global user.name "name"` | Set username globally | `git config --global user.name "parii-star"` | No output |
| `git config --global user.email "email"` | Set email globally | `git config --global user.email "abc@gmail.com"` | No output |
| `git config --list` | Show all configs | `git config --list` | Displays Git settings |
| `git remote -v` | Show connected remotes | `git remote -v` | Shows origin fetch/push URLs |
| `git remote add origin URL` | Connect GitHub repo | `git remote add origin https://github.com/parii-star/cheatsheets.git` | No output |
| `git push -u origin main` | First push to GitHub | `git push -u origin main` | Upload progress + branch tracking |
| `git push` | Push latest changes | `git push` | `Everything up-to-date` or upload |
| `git pull` | Download latest changes | `git pull` | Fetch + merge messages |
| `git clone URL` | Download repository | `git clone https://github.com/parii-star/cheatsheets.git` | Creates local repo copy |
| `git branch` | Show branches | `git branch` | `* main` |
| `git branch dev` | Create branch | `git branch dev` | No output |
| `git checkout dev` | Switch branch | `git checkout dev` | `Switched to branch 'dev'` |
| `git checkout -b feature` | Create & switch branch | `git checkout -b feature` | `Switched to a new branch` |
| `git log` | Show commit history | `git log` | Commit details list |
| `git diff` | Show file changes | `git diff` | Displays changed lines |
| `git restore file.md` | Undo file changes | `git restore README.md` | No output |
| `git rm file.md` | Delete tracked file | `git rm README.md` | `rm 'README.md'` |
| `git rm --cached file.md` | Unstage/remove from Git only | `git rm --cached secret.txt` | Removes from staging |
| `git reset` | Unstage files | `git reset` | Unstaged files message |
| `git reset --hard` | Remove all local changes | `git reset --hard` | `HEAD is now at...` |
| `git fetch` | Download remote updates | `git fetch` | Download objects info |
| `git merge dev` | Merge branch | `git merge dev` | Merge summary |
| `git stash` | Save temporary changes | `git stash` | `Saved working directory` |
| `git stash pop` | Restore stash | `git stash pop` | Restored changes |
| `git remote remove origin` | Remove remote repo | `git remote remove origin` | No output |
| `git mv old new` | Rename file | `git mv old.md new.md` | No output |
| `git show` | Show commit details | `git show` | Commit diff/details |
| `git tag v1.0` | Create version tag | `git tag v1.0` | No output |
| `git commit --amend` | Edit last commit | `git commit --amend` | Opens editor/update commit |
| `git clean -f` | Delete untracked files | `git clean -f` | Removed files list |
| `git reflog` | Show Git history actions | `git reflog` | List of HEAD changes |
| `git help status` | Open help page | `git help status` | Git manual/help page |

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
