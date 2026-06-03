
# Generate Key

run:

```
ssh-keygen 
```

change passphrase:

```shell
ssh-keygen -p -f ~/.ssh/id_ed25519
```



# SSH Config

vim \~/.ssh/config

```
Host shortname
    HostName 100.100.100.100
    User ubuntu
    IdentityFile ~/.ssh/private-key-filename.key
```


# SSH Agent
save you time with passphrase automation.

check if your ssh agent is running:
```
eval "$(ssh-agent -s)"
```
add ssh key:
```
ssh-add ~/.ssh/id_ed25519
```
or set timeout period
```
ssh-add -t 8h ~/.ssh/id_ed25519
```


check loaded keys:
```
ssh-add -l
```





# Host SSH

### Install SSH Server

```
sudo apt install ssh-server
systemctl enable ssh
```

### Setup Key Access

```
scp ~/.ssh/public-key.pub user@100.100.100.100:~
mkdir .ssh/
touch ~/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys
chmod 700 ~/.ssh
```

### Harden your sshd config

(optional: backup your config)

```
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.bak
```

Search for the line that contains PasswordAuthentication and change it from yes to no and uncomment the line by removing the beginning #

you can edit sshd\_config with your favorite text editor:

{% code fullWidth="false" %}
```
sudo vim /etc/ssh/sshd_config
```
{% endcode %}

or

you can automate the process by using the sed command:

```
sudo sed -i 's/^#?PasswordAuthentication .*/PasswordAuthentication yes/' /etc/ssh/sshd_config
```

then restart ssh demon with

```
sudo systemctl restart sshd
```



<br>

















***
