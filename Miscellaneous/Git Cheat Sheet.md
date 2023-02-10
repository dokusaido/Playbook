# Git Cheat Sheet

-   Create new git
```
```
git init
git add -all
git commit -m "message"
git remote add https://.../<git>.git

-   Git local changes

git status
git add --all
git add -p <file>

-   Git history

git log
git log -p <file>
git blame <file>

-   Git branch

git branch -av
git branch <new-branch>
git checkout <branch>

-   Git undo

git reset --hard HEAD
git checkout HEAD <file>
git revert <commit-id>