# Linux Clean Storage





Step 0:&#x20;

Analyse how much storage you have free and used

```
df -h
```

```
df -h --type=ext4
```



check which folders are using most

```
sudo du -xh --max-depth=1 / | sort -h
```

```
sudo du -xh --max-depth=1 /home | sort -h
```





check how much podman is using:

```
podman system df
```

```
sudo podman system df
```



```
sudo du -xah / | sort -rh | head -30
```



```
sudo find / -xdev -type f -printf '%s %p\n' \
| sort -nr \
| head -30 \
| awk '{printf "%.2f GB\t%s\n",$1/1024/1024/1024,$2}'
```



`ncdu`





clean trash:

```
sudo rm -rf /root/.local/share/Trash/*
```

1. `sudo apt autoremove -y`
2. `sudo apt clean`
3. `sudo apt autoclean`
4. `sudo apt autoremove --purge -y`
5. `dpkg -l | awk '/^rc/ {print $2}'`
6. `sudo apt purge $(dpkg -l | awk '/^rc/ {print $2}') -y`

#### Cache cleanup

9. `rm -rf ~/.cache/*`
10. `rm -rf ~/.thumbnails/*`
11. `sudo rm -rf /var/cache/apt/archives/*`
12. `sudo rm -rf /var/cache/apt/archives/partial/*`

#### Logs cleanup

13. `sudo journalctl --vacuum-time=7d`
14. `sudo journalctl --vacuum-size=100M`
15. `sudo find /var/log -type f -name "*.log" -delete`

#### Large file discovery

16. `du -ah ~ | sort -rh | head -20`
17. `sudo du -ah /var | sort -rh | head -20`
18. `find ~ -type f -size +500M -print`

#### Temporary files

19. `sudo rm -rf /tmp/*`
20. `rm -rf ~/.local/share/Trash/*`

#### Flatpak / Snap (if installed)

21. `flatpak uninstall --unused -y`
22. `snap list --all | awk '/disabled/{print $1, $3}'`
23. `snap remove $(snap list --all | awk '/disabled/{print $1, $3}')`

#### Docker cleanup (if installed)

24. `podman system prune -af`
25. `podman volume prune -f`
26. `podman image prune -af`

#### Package metadata & orphaned cleanup

27. `sudo apt autoremove --purge`
28. `sudo deborphan | xargs sudo apt-get -y remove --purge`
29. `sudo dpkg --purge $(dpkg -l | awk '/^rc/ {print $2}')`

#### Extra safe system cleanup

30. `sudo find /var/cache -type f -delete`
