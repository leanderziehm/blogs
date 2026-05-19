# git



remove files from a commit that wasn't pushed yet:

```
git reset --soft HEAD~1
```

if the change was already pushed then you can use `git push -f` but its quite dangerous because it could delete progress of other contributors so be careful when using force push.







basics:

```
git add .
git commit -m "write commit message here"
git push
```





setup:

```
git config --global user. email "you@example.com"
git config --global user.name "yourusername"
```



