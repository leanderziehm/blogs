# Podman

I liked docker but when researching more about securety the systematic design of podman to be rootless by default thereby making it more secure against exploits won me over.

### Install

```
sudo apt install podman
```

```
sudo apt install podman-compose
```



if you want smoother docker compatebility change the config to default to docker repos:

```
sudo vim /etc/containers/registries.conf
```

```
unqualified-search-registries = ["docker.io"]
```
