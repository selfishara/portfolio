# 🐙 Git cheatsheet

## Mental model
```
working directory ──git add──▶ staging area ──git commit──▶ local repo ──git push──▶ GitHub
                  ◀────────────────────── git pull / git fetch ──────────────────────
```

## Setup (once per machine)
```bash
git config --global user.name "Sara Martínez"
git config --global user.email "you@example.com"
git config --global init.defaultBranch main
git config --global pull.rebase false      # pull = fetch + merge
git config --global core.editor "code --wait"
```

## Daily workflow (one branch per issue)
```bash
git switch main                            # go to main
git pull                                   # bring main up to date
git switch -c feat/US-2.3-rent-ratio       # new branch for the issue
# ... work ...
git status                                 # what changed?
git diff                                   # see the changes line by line
git add <file>        # or: git add .      # stage
git commit -m "feat(money): add rent-to-income ratio"
git push -u origin feat/US-2.3-rent-ratio  # first push of the branch (-u links it to the remote)
git push                                   # following pushes
# → open a PR on GitHub with "Closes #N" in the description
```

## Looking around
```bash
git log --oneline --graph --all            # history as a tree
git show <hash>                            # what a commit changed
git branch -a                              # local and remote branches
git remote -v                              # where origin points
```

## Undoing (calmly)
| Situation | Command |
|---|---|
| Discard changes to a file (not staged) | `git restore <file>` |
| Unstage a file | `git restore --staged <file>` |
| Fix the last commit message (not pushed yet) | `git commit --amend` |
| Undo a commit that's already pushed | `git revert <hash>` (creates an "undo" commit) |
| Put work aside for a moment | `git stash` / `git stash pop` |

> ⚠️ Avoid `git push --force` on shared branches. On your own branch, use `--force-with-lease`.

## Conventional Commits
`<type>(<scope>): <description>` in imperative mood and lowercase.

| Type | When |
|---|---|
| `feat` | New functionality |
| `fix` | Bug fix |
| `docs` | Documentation only |
| `test` | Tests |
| `refactor` | Code change that doesn't alter behaviour |
| `chore` | Build, config, dependencies |
| `ci` | Pipelines |

Examples: `docs: add sprint 0 backlog` · `feat(auth): validate google id token` · `test(money): cover amber threshold`

## Branch naming
`feat/US-x.y-short-name` · `fix/short-name` · `docs/short-name` · `spike/S0-3-apis`

## 🧠 My own words
> *What's the difference between `git fetch` and `git pull`? Between `restore` and `revert`?*
