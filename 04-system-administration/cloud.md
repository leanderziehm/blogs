# Cloud



## Github Actions

| Location                  | Type     | Scope                                                           | When to use                                                             |
| ------------------------- | -------- | --------------------------------------------------------------- | ----------------------------------------------------------------------- |
| **Repository secrets**    | Secret   | Entire repository                                               | Sensitive values used by all workflows (API keys, tokens, passwords)    |
| **Repository variables**  | Variable | Entire repository                                               | Non-sensitive config used by all workflows (URLs, feature flags, names) |
| **Environment secrets**   | Secret   | Specific deployment environment (`production`, `staging`, etc.) | Sensitive values that differ per environment                            |
| **Environment variables** | Variable | Specific deployment environment                                 | Non-sensitive config that differs per environment                       |





## AWS

lambda



## Azure



## GCP

[https://rclone.org/drive/#making-your-own-client-id](https://rclone.org/drive/#making-your-own-client-id)



## Oracle

1 big vsv or 4 small ones free forever

ARM: 24 GB RAM, 4 core

200GB storage



## Cloudflare

#### Cloudflare workers:

10s max execution time.

#### Cloudflare Tunnels:

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





## Supabase

2 postgres databases for free







***





## Observability Metrics&#x20;

### Grafana Stack LGTM

#### Alloy

To check the status of Alloy, run:

```
sudo systemctl status alloy.service
```

To restart Alloy, run:

```
sudo systemctl restart alloy.service
```

The config file is located at:\
`/etc/alloy/config.alloy`





### Elastic Search ELK Stack



