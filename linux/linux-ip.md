# Linux IP

```
ping -i 0.01 10.0.0.2
```





On PC A:

```
sudo ip addr add 192.168.10.1/24 dev eth0sudo ip link set eth0 up
```

On PC B:

```
sudo ip addr add 192.168.10.2/24 dev eth0sudo ip link set eth0 up
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
