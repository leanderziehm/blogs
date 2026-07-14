# Nginx setup

install nginx:

```
sudo apt install nginx
```

activate nginx:

```
nginx -v
systemctl status nginx
sudo systemctl start nginx
sudo systemctl enable nginx
```

## Certbot

```
sudo snap install --classic certbot

sudo ln -s /snap/bin/certbot /usr/bin/certbot

sudo certbot --nginx
```

## Script

[https://github.com/LeanderZiehm/devops/blob/main/setup-nginx.sh](https://github.com/LeanderZiehm/devops/blob/main/setup-nginx.sh)

```
curl -O https://raw.githubusercontent.com/LeanderZiehm/devops/refs/heads/main/setup-nginx.sh
```

download and run:

```
sh setup-nginx.sh
```







## manually check

```
sudo vim /etc/nginx/sites-available/example.com
```

```
sudo ln -s /etc/nginx/sites-available/example.com /etc/nginx/sites-enabled/
```

```
sudo nginx -t && sudo systemctl reload nginx
```

/etc/nginx/sites-available/\
/etc/nginx/sites-enabled/





***
