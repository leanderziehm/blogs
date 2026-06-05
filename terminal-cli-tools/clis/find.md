# find & grep



```
grep -R -n -i "import tornado" .
```



```
grep -R -i "import tornado" . | cut -d: -f1 | uniq | xargs -n1 vim
```



```
find . -type f -name "*.js" -exec grep -n "search_term" {} +
```
