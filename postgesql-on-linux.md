# Postgesql on Linux

## Install

on arch linux:

```
sudo pacman -S postgresql
```

on debian, ubuntu and derivatives:&#x20;

```
sudo apt install postgresql
```



sudo -iu postgres initdb --locale=C.UTF-8 --encoding=UTF8 -D /var/lib/postgres/data

```
sudo systemctl start postgresql
sudo systemctl enable postgresql
systemctl status postgresql
```

sudo -iu postgres psql



sudo -iu postgres createuser --interactive\
sudo -iu postgres createdb mydb\
psql -U myuser -d mydb



change postgres admin password:

```
sudo -iu postgres psql -c "ALTER USER postgres WITH PASSWORD 'newpassword';"
```













***
