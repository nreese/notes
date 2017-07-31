[keeping-a-github-fork-updated](https://robots.thoughtbot.com/keeping-a-github-fork-updated)
```
git fetch upstream
git rebase upstream/master
git push origin {branch name} -f
```

### timestamps
* tag `git log -1 --format=%ai v5.5.1`
* commit `git show -s --format=%ci 9b93fbb46af9afbfc3b7f970d8fe6b86049eeb43`
