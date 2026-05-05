# Git Workflow: ReadyGPT + Upstream Sync

This repository is configured so:

- `origin` points to `https://github.com/varunanusheel/ReadyGPT.git`
- `upstream` points to `https://github.com/open-webui/open-webui.git`

## Push your work to ReadyGPT

```bash
git add -A
git status
git commit -m "Your message"
git push
```

`git push` sends your branch to `origin` (ReadyGPT).

## Fetch new changes from the original repo

```bash
git fetch upstream
```

Then choose one sync method:

### Option A: Merge upstream into your branch

```bash
git merge upstream/main
git push
```

### Option B: Rebase your branch onto upstream

```bash
git rebase upstream/main
git push
```

If you rebased commits that were already pushed before, use:

```bash
git push --force-with-lease
```

## Quick update command (fetch + merge)

```bash
git fetch upstream && git merge upstream/main
```

## Optional: Preview incoming upstream commits

```bash
git fetch upstream
git log main..upstream/main --oneline
```
