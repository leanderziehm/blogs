# Cloudflare

## Cloudflare workers

10s max execution time.







## Cloudflare Tunnels

[https://dash.cloudflare.com/{userid}/one/networks/connectors/cloudflare-tunnels/add/cfd\_tunnel](https://dash.cloudflare.com/%7Buserid%7D/one/networks/connectors/cloudflare-tunnels/add/cfd_tunnel)

```
# Add cloudflare gpg key
sudo mkdir -p --mode=0755 /usr/share/keyrings
curl -fsSL https://pkg.cloudflare.com/cloudflare-public-v2.gpg | sudo tee /usr/share/keyrings/cloudflare-public-v2.gpg >/dev/null

# Add this repo to your apt repositories
echo 'deb [signed-by=/usr/share/keyrings/cloudflare-public-v2.gpg] https://pkg.cloudflare.com/cloudflared any main' | sudo tee /etc/apt/sources.list.d/cloudflared.list

# install cloudflared
sudo apt-get update && sudo apt-get install cloudflared
```

```
sudo cloudflared service install sdkjksdjf-code-here
```
