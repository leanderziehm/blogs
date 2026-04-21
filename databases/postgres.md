---
description: postgres version 16
---

# Postgres



## Install

```
sudo apt install postgresql
```

## Expose Postgres Publicly

{% hint style="danger" %}
This action is dangerous. Only follow if you follow have strong security practices and you know what you are doing.&#x20;
{% endhint %}

sudo apt install postgres

sudo vim /etc/postgresql/16/main/postgresql.conf

```jsx
listen_addresses = '*'
```

sudo vim /etc/postgresql/16/main/pg\_hba.conf

```
host    all    all    0.0.0.0/0    md5
```



## Change passowrd

```
sudo -i -u postgres psql
```

```
ALTER USER postgres WITH PASSWORD 'new_password';
\q
```

```
sudo systemctl restart postgresql
```

## Backup:

```
pg_dumpall -U postgres -f all_databases_backup.sql
```

Copy to local storage

```
scp ./oracle-2_all_databases_backup.sql oracle:~/
"or"
rsync -avz -P oracle:/var/lib/postgresql/oracle-2_all_databases_backup.sql ~/
```

or archive in s3 compatible storage

## Restore Backup

```
sudo chown postgres:postgres pg_dumpall_2026-02-25_19-26-40.sql
sudo -u postgres psql -f ~/pg_dumpall_2026-02-25_19-26-40.sql
scp ./oracle-2_all_databases_backup.sql oracle:~/
```

## Files

/etc/postgresql/16/main/postgresql.conf



## Related Topics

High availabiltiy

Patroni
