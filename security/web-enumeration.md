# Web Enumeration

```
# Web search — fastest
curl "https://crt.sh/?q=%.example.com&output=json" | jq '.[].name_value' | sort -u
```

