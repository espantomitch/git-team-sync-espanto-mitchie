\# Git Team Sync Workflow



\## 1. What did the rejected push error message tell you, and why did it happen?



The rejected push said that the remote repository contained changes that I did not have locally and that I needed to fetch first. This happened because Clone A and Clone B were both working on the same `feature/loyalty-points` branch. One clone pushed new commits while the other clone was still based on an older version of the branch, so Git rejected the push to prevent the newer remote changes from being overwritten.



\## 2. What's the actual difference between how you resolved Task 3 (merge) vs Task 4 (rebase)?



In Task 3, I used `git fetch` followed by `git merge`. Git combined the histories of Clone A and Clone B and created a separate merge commit after I resolved the conflict. This preserved the fact that the two copies had developed separately.



In Task 4, I used `git fetch` followed by `git rebase`. Instead of creating another merge commit, Git temporarily removed my local commit, updated my branch to the latest remote version, and then reapplied my commit on top of it. I still had to resolve a conflict, but the final history was more linear.



\## 3. What one habit would have avoided both rejected pushes in this lab?



A good habit would be to fetch or pull the latest remote changes before starting new work on a shared branch. If I had synchronized the branch before making each change, both local clones would have started from the latest version and the rejected pushes could have been avoided.



\## 4. Which approach - merge or rebase - would you default to on a shared team branch, and why?



I would normally use merge on a shared team branch because it preserves the existing shared history and does not rewrite commits that other team members may already be using. Rebase is useful for cleaning up local commits before they are shared, but rebasing commits that have already been shared can cause problems for other developers. In this lab, rebase was safe because I was rebasing my local unpushed commit onto the latest remote branch.

