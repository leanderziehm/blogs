# Podman

I liked docker but when researching more about securety the systematic design of podman to be rootless by default thereby making it more secure against exploits won me over.

### Install

```
sudo apt install podman
```

```
sudo apt install podman-compose
```



## Setup

if you want smoother docker compatebility change the config to default to docker repos:

```
sudo vim /etc/containers/registries.conf
```

```
unqualified-search-registries = ["docker.io"]
```





## Commands



```
podman run --name pg16 \
  -e POSTGRES_PASSWORD=postgres \
  -e POSTGRES_USER=postgres \
  -e POSTGRES_DB=postgres \
  -p 5432:5432 \
  -v pgdata:/var/lib/postgresql/data \
  -d docker.io/library/postgres:16
```

```
podman cp full_recovery_20260530_160846.sql pg16:/tmp/dump.sql
```

```
podman exec -it pg16 psql -U postgres -f /tmp/dump.sql
```

```
podman ps -a
```

```
podman logs pg16
```

```
podman exec -it pg16 bash
```





***



example oneliners:

```
podman run docker.io/library/debian:13
```



```
podman pull docker.io/kalilinux/kali-rolling
podman inspect --format='{{index .RepoDigests 0}}' kalilinux/kali-rolling
```





## Podman Compose Examples:



