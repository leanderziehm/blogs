# Nginx

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

```
curl -O https://raw.githubusercontent.com/LeanderZiehm/devops/refs/heads/main/setup-nginx.sh
```

[https://github.com/LeanderZiehm/devops/blob/main/setup-nginx.sh](https://github.com/LeanderZiehm/devops/blob/main/setup-nginx.sh)

```
#!/bin/bash

# CLI to set up a new web app

# Ask for full domain
read -p "Enter your full domain (e.g., example.website.com): " DOMAIN

# Then ask for port
read -p "Enter the port your app will run on (e.g., 5014): " APP_PORT

NGINX_AVAILABLE="/etc/nginx/sites-available/$DOMAIN"
NGINX_ENABLED="/etc/nginx/sites-enabled/$DOMAIN"

# Create Nginx config
echo "Creating Nginx config for $DOMAIN..."
sudo tee $NGINX_AVAILABLE > /dev/null <<EOF
server {
    listen 80;
    server_name $DOMAIN;

    location / {
        proxy_pass http://localhost:$APP_PORT;
        proxy_http_version 1.1;

        # Required for WebSocket support
        proxy_set_header Upgrade \$http_upgrade;
        proxy_set_header Connection "upgrade";
        
        proxy_set_header Host \$host;
        proxy_set_header X-Real-IP \$remote_addr;
        proxy_set_header X-Forwarded-For \$proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto \$scheme;

        # Optional: increase timeout for long-lived WebSocket connections
        proxy_read_timeout 86400;
        proxy_send_timeout 86400;
    }
}
EOF

# Enable site
sudo ln -sf $NGINX_AVAILABLE $NGINX_ENABLED

# Test Nginx config
echo "Testing Nginx configuration..."
sudo nginx -t && sudo systemctl reload nginx

# Enable HTTPS via Certbot
echo "Enabling HTTPS with Certbot..."
sudo certbot --nginx -d $DOMAIN

echo "Setup complete! Your app is available at https://$DOMAIN"
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
