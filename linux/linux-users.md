# Linux Users, Groups, Permissions

Add new user:

```bash
useradd -m -G wheel -s /bin/bash username
passwd username
```

Give sudo permissions:

make sure you have sudo installed and if it doest work try:

```bash
EDITOR=vim visudo
```

add user to group:

```
sudo usermod -aG google-sudoers username
```





***



### 1) Users

#### See users

* `whoami` → shows current user
* `id` → shows user ID (UID), groups, and group IDs
* `cat /etc/passwd` → list all system users

#### Create / modify users (admin required)

* `sudo useradd username` → create user
* `sudo passwd username` → set password
* `sudo usermod -aG groupname username` → add user to group
* `sudo userdel username` → delete user

***

### 2) Groups

#### View groups

* `groups` → groups of current user
* `groups username` → groups of another user
* `cat /etc/group` → all groups

#### Manage groups

* `sudo groupadd groupname` → create group
* `sudo groupdel groupname` → delete group
* `sudo usermod -aG groupname username` → add user to group

***

### 3) Permissions (core concept)

Each file has:

* **Owner (user)**
* **Group**
* **Others**

Check permissions:

* `ls -l`

Example output:

```
-rwxr-xr--
```

Meaning:

* `r` = read
* `w` = write
* `x` = execute

Breakdown:

* `rwx` → owner
* `r-x` → group
* `r--` → others

***

### 4) Changing permissions

* `chmod 755 file`
* `chmod 644 file`

Meaning:

* 7 = rwx
* 6 = rw-
* 5 = r-x
* 4 = r--

***

### 5) Changing ownership

* `sudo chown user file`
* `sudo chown user:group file`
* `sudo chgrp group file`

***

### 6) extras

* `umask` → default permission mask
* `sudo` → run commands as admin
* `getent passwd` → query system user database cleanly

***



* Users = identity
* Groups = shared access buckets
* Permissions = what each bucket can do to files

