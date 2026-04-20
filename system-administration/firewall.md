# Firewall

## iptables

```
sudo iptables-save > ~/iptables.rules
```

```
sudo vim ~/iptables.rules
```

find the line that has port 22 accept and copy it and editing the port

80, 443, 5432

```
-A INPUT -p tcp -m state --state NEW -m tcp --dport 22 -j ACCEPT
-A INPUT -p tcp -m state --state NEW -m tcp --dport 80 -j ACCEPT
-A INPUT -p tcp -m state --state NEW -m tcp --dport 443 -j ACCEPT
```

then load the new rules:

```
sudo iptables-restore < ~/iptables.rules
```

