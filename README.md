# Scripts

Daily-use CLI scripts for git and GitHub workflows.

## Prerequisites

- **Bash**
- **Git** (with `co` and `b` aliases for `checkout` and `branch`, or adjust the scripts)
- For **review**: [GitHub CLI](https://cli.github.com/) (`gh`), [fzf](https://github.com/junegunn/fzf), [jq](https://jqlang.github.io/jq/)

## Scripts

### `review`

Unified PR review across multiple GitHub repos. Fetches open PRs, lets you pick one or more in **fzf**, then for each PR you can:

- **Approve**
- **Approve and squash merge**
- **Review in browser**
- **Review in terminal** (metadata + diff)
- **Close PR**
- **Back** to pick again

Repos are configured at the top of the script (default: `Dimensiondev/firefly-social`, `Dimensiondev/firefly-wallet`). Edit the `REPOS` array to match your own.

```bash
./review
```

Uses TAB to select, ENTER to confirm, ESC to exit without choosing.

---

### `up` / `update_branch`

Sync a local branch with its remote. Fetches, then resets the branch to `origin/<branch>` so your local copy matches the remote.

- With a branch name: updates that branch (and checks it out if needed).
- With no args: updates the **current** branch.

Requires Git aliases: `git co` = `checkout`, `git b` = `branch`. If you don’t use those, replace `co`/`b` in the script with `checkout`/`branch`.

```bash
./up                  # update current branch
./up main             # update main
./update_branch feat  # update branch feat
```

---

## Setup

1. Clone and (optionally) put the repo or symlinks in your `PATH`:

   ```bash
   git clone git@github.com:guanbinrui/scripts.git
   cd scripts
   chmod +x review up update_branch
   ```

2. For `review`, ensure you’re logged in: `gh auth login`.
3. For `up`/`update_branch`, add Git aliases if you use them:

   ```bash
   git config --global alias.co checkout
   git config --global alias.b branch
   ```
