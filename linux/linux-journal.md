# Linux Journal

todo journal







***

### 1) Basic journal viewing

* `journalctl` → show all logs (can be very long)
* `journalctl -b` → logs from current boot
* `journalctl -b -1` → previous boot logs
* `journalctl -f` → follow logs live (like `tail -f`)

***

### 2) Filtering logs

#### By service (very common)

* `journalctl -u ssh`
* `journalctl -u nginx`
* `journalctl -u systemd-networkd`

#### By time

* `journalctl --since "today"`
* `journalctl --since "1 hour ago"`
* `journalctl --since "2026-06-01 10:00:00"`
* `journalctl --until "2026-06-01 12:00:00"`

***

### 3) Priority / severity filtering

* `journalctl -p 0` → emergencies only
* `journalctl -p 3` → errors and above
* `journalctl -p warning`
* `journalctl -p info`

Priority levels:

* 0 = emergency
* 1 = alert
* 2 = critical
* 3 = error
* 4 = warning
* 5 = notice
* 6 = info
* 7 = debug

***

### 4) Kernel logs

* `journalctl -k` → kernel messages
* `journalctl -k -b` → kernel logs from current boot

***

### 5) Output formatting

* `journalctl -o short` → default readable format
* `journalctl -o verbose` → detailed fields
* `journalctl -o json` → machine-readable JSON

***

### 6) Searching logs

* `journalctl | grep ssh`
* `journalctl -u ssh | grep "Failed"`

Better option:

* `journalctl -u ssh --grep "failed"`

***

### 7) Disk usage & maintenance

* `journalctl --disk-usage` → size of logs
* `sudo journalctl --vacuum-time=7d` → keep only 7 days
* `sudo journalctl --vacuum-size=100M` → limit log size

***

#### Debug a service crash

```bash
journalctl -u nginx -b --no-pager
```

#### Watch live system errors

```bash
journalctl -p 3 -f
```

#### Check boot issues

```bash
journalctl -b -1 -p 3
```

***

`journalctl`

* `-u` = service-focused debugging
* `-b` = boot history analysis
* `-f` = real-time monitoring

