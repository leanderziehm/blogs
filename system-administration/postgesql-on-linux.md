# Postgesql

## Install

```
sudo apt install postgresql
```

## Enable postgres

```
sudo systemctl start postgresql
sudo systemctl enable postgresql
systemctl status postgresql
```

sudo -iu postgres psql

## New user and db

sudo -iu postgres createuser --interactive\
sudo -iu postgres createdb mydb\
psql -U myuser -d mydb

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

```
sudo -iu postgres psql -c "ALTER USER postgres WITH PASSWORD 'newpassword';"
```

## Expose Postgres Publicly

{% hint style="danger" %}
This action is dangerous. Only follow if you follow have strong security practices and you know what you are doing.&#x20;
{% endhint %}

```
sudo vim /etc/postgresql/16/main/postgresql.conf
```

listen\_addresses = '\*'

```
sudo vim /etc/postgresql/16/main/pg_hba.conf
```

host all all 0.0.0.0/0 md5

```
sudo systemctl restart postgresql
```



and also open firewall at 5432:

{% content-ref url="firewall.md" %}
[firewall.md](firewall.md)
{% endcontent-ref %}

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

if you have a backup on the personal computer and want it on the server:

```
scp ./pg_dumpall_2026-02-25_19-26-40.sql.gz database:~/
```

on server then load the database by:&#x20;

```
gunzip ./pg_dumpall_2026-02-25_19-26-40.sql.gz
sudo chown postgres:postgres pg_dumpall_2026-02-25_19-26-40.sql
```

```
sudo mv /home/ubuntu/pg_dumpall_2026-02-25_19-26-40.sql /var/lib/postgresql/
```

```
sudo -iu postgres
```

```
psql -f ./pg_dumpall_2026-02-25_19-26-40.sql
```



## Backup with Rclone to cloud

```
sudo apt install rclone
```

on server

```
rclone config 
```

name it dropbox and select it (13)



on personal computer:

```
rclone authorize "dropbox"
```

copy paste auth key



test:

```
rclone copy /home/ubuntu/test-backup dropbox:backups --ignore-existing --stats=1m --log-level NOTICE
```



copy file:

```
https://raw.githubusercontent.com/LeanderZiehm/devops/refs/heads/main/backup-postgres.sh
```

```
chmod +x ./backup-postgres.sh
```

test:

```
crontab -e

* * * * * ~/backup-postgres.sh >> ~/pg_backup.log 2>&1
```



## Paths

config:

```
/etc/postgres
```

data:

```
/var/lib/postgres
```





## psql

```
psql -h domain.example.com -U postgresUser -d postgresDatabase
```



| Meta-Command               | Effect                                   |
| -------------------------- | ---------------------------------------- |
| \list or \l                | list all databases                       |
| \dt                        | Lists all tables in the current database |
| \du                        | show users                               |
| \conninfo                  | connection info                          |
| \change or \c databaseName | change database                          |
| \d tableName               | show schema of table                     |
| \d+ tableName              | detailed table infos                     |
|                            |                                          |

| **`\di`** | Lists all indexes.   | Helps with performance tuning and understanding database schema.          |
| --------- | -------------------- | ------------------------------------------------------------------------- |
| **`\dv`** | Lists all views.     | Essential for understanding virtual or pre-packaged data representations. |
| **`\df`** | Lists all functions. | Crucial for projects that rely heavily on stored procedures.              |
|           |                      |                                                                           |
|           |                      |                                                                           |

[https://www.postgresql.org/docs/current/app-psql.html](https://www.postgresql.org/docs/current/app-psql.html)







## Other

sudo -iu postgres initdb --locale=C.UTF-8 --encoding=UTF8 -D /var/lib/postgres/data

/etc/postgresql/16/main/postgresql.conf

## Related Topics

High availabiltiy



#### Patroni&#x20;

[https://www.youtube.com/watch?v=cEWBC3a33ds](https://www.youtube.com/watch?v=cEWBC3a33ds)

[https://www.youtube.com/watch?v=RHwglGf\_z40](https://www.youtube.com/watch?v=RHwglGf_z40)











***
