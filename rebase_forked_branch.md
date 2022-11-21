[keeping-a-github-fork-updated](https://robots.thoughtbot.com/keeping-a-github-fork-updated)
```
git fetch upstream
git rebase upstream/main
git push origin {branch_name} -f
```

Using pull has an advantage in that the commit history is preserved

```
git fetch upstream
git pull upstream main
git push origin {branch_name}
```

Revert branch to origin
```
git reset --hard origin/{branch_name}
```

### Merging via command line

```
// Branch name: thomasneirynck:maps/tracktileloadstatus
// username: thomasneirynck
git checkout -b thomasneirynck-maps/tracktileloadstatus master
git pull https://github.com/thomasneirynck/kibana.git maps/tracktileloadstatus --rebase
```

### Fix branch after messed up merge/rebase

```
git reset --hard {hash of last good commit}
git push -f origin {branch name}
```

### timestamps
* tag `git log -1 --format=%ai v5.5.1`
* commit `git show -s --format=%ci 9b93fbb46af9afbfc3b7f970d8fe6b86049eeb43`

### sort branches by commit time
```
git branch --sort=-committerdate
```
