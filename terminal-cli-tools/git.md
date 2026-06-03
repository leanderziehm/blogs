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





```
git filter-repo --path-glob '*.csv' --invert-paths
```



## Problems

sometimes vscode does a bunch of requests to the git server with the wrong credentials and then the  firewall blocks you for some hours. So better to use git mostly over cli with ssh. TODO research more.



