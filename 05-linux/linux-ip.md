# Linux IP

```
ping -i 0.01 10.0.0.2
```

```
sudo sysctl -w net.ipv4.ip_forward=1
```

```
echo "net.ipv4.ip_forward=1" | sudo tee /etc/sysctl.d/99-hotspot.conf
sudo sysctl --system
```

```
sudo iptables -t nat -A POSTROUTING -o UPSTREAM_IFACE -j MASQUERADE
```

```
#!/usr/bin/env bash

echo "Setting IPv6 preference in system..."

sudo sysctl -w net.ipv6.conf.all.disable_ipv6=0
sudo sysctl -w net.ipv6.conf.default.disable_ipv6=0

# Prefer IPv6 over IPv4 when both exist
echo "net.ipv6.conf.all.accept_ra=2" | sudo tee /etc/sysctl.d/40-ipv6.conf
echo "net.ipv6.conf.default.accept_ra=2" | sudo tee -a /etc/sysctl.d/40-ipv6.conf

sudo sysctl --system

echo "IPv6 preference enabled."
```

On PC A:

```
sudo ip addr add 192.168.10.1/24 dev eth0
sudo ip link set eth0 up
```

On PC B:

```
sudo ip addr add 192.168.10.2/24 dev eth0
sudo ip link set eth0 up
```

Test:

```
ping 192.168.10.2
```

## Mininet NAT

forward:

```
sudo sysctl -w net.ipv4.ip_forward=1
```

```
sudo ip route add 10.0.2.0/24 dev s1-eth1
```

```
ip route get 10.0.2.2
```

confim:

```
sudo ip addr add 10.0.2.254/24 dev s1-eth1
```

nat:

```
sudo iptables -t nat -A POSTROUTING -s 10.0.2.0/24 -o wlp4s0 -j MASQUERADE
```

```
sudo iptables -A FORWARD -i wlp4s0 -o s1-eth1 -j ACCEPT
sudo iptables -A FORWARD -o wlp4s0 -i s1-eth1 -j ACCEPT
```







ip a



ip a br

ip route



