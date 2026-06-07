# tar zip

```
tar -czf zipped_name.tar.gz file.name
```

* `-c` → create a new archive
* `-z` → compress it using **gzip**
* `-f` → output file name



```
tar -xzvf full_recovery_20260530_160846.tar.gz
```

* `-x` → extract
* `-z` → decompress it using **gzip**
* `-f` → file name

unpack tar:

```
tar -xzf postgresql_backup.tar.gz
```

`-v` → verbose (shows progress)



```
sudo tar -czvf postgres_backup.tar.gz -C /mnt/recovery var/lib/postgresql
```





