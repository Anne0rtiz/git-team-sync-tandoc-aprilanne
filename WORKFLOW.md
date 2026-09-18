# Git Team Sync Workflow

### 1. What did the rejected push error message tell you, and why did it happen?
The error message (`non-fast-forward` / `fetch first`) warned that the remote repository contained work that did not exist locally. It happened because another teammate (our other clone) had already pushed new commits to the same branch on GitHub. Git rejected the push to prevent us from accidentally overwriting or erasing their work.

### 2. What's the actual difference between how you resolved Task 3 (merge) vs Task 4 (rebase)?
*   **Merge (Task 3):** Git created a brand new "merge commit" to tie the two diverging timelines together. It preserved the exact chronological history of when both changes were made, but created a branching "diamond" shape in the commit graph.
*   **Rebase (Task 4):** Git set our local commit aside, downloaded the remote changes, and then re-applied our local commit directly on top of them. This avoided a merge commit and kept the history in a single, perfectly straight line.

### 3. What one habit would have avoided both rejected pushes in this lab?
Running `git pull` (or fetching and merging) at the start of every work session and right before committing/pushing. Staying synced with the remote branch prevents you from doing work on an outdated foundation.

### 4. Which approach - merge or rebase - would you default to on a shared team branch, and why?
I would default to **merge** on a shared team branch (like `main`). Rebase rewrites project history by changing commit IDs, which can cause massive headaches if teammates have already pulled the old history. Merging is non-destructive and preserves the true historical context of how the code evolved.