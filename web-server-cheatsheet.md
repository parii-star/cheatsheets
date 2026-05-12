# Web Server Cheat Sheet

> **Goal:** Understand the basic commands and concepts used to run and troubleshoot a web server.

This cheat sheet is for common Linux web server tasks with Apache, Nginx, and app servers running behind them.

## How To Read This Sheet

| Pattern | Meaning |
|---|---|
| `[service]` | replace with a service name, such as `nginx` or `apache2` |
| `[domain]` | replace with a real domain name |
| `[port]` | replace with a port number such as `80` or `443` |
| `[path]` | replace with a file or directory path |

## Table Of Contents

| Section | What You Learn |
|---|---|
| [Service Control](#service-control) | manage the web server service |
| [Common Checks](#common-checks) | test connectivity and configuration |
| [Static Sites](#static-sites) | serve HTML, CSS, and JS files |
| [Reverse Proxy](#reverse-proxy) | forward requests to application servers |
| [TLS And Domains](#tls-and-domains) | handle HTTPS and hostnames |
| [Logs](#logs) | inspect access and error logs |

## Service Control

| Command | Clear Description |
|---|---|
| `sudo systemctl status [service]` | Check whether a web server is running. |
| `sudo systemctl start [service]` | Start the web server service. |
| `sudo systemctl stop [service]` | Stop the web server service. |
| `sudo systemctl restart [service]` | Restart the service after changes. |
| `sudo systemctl reload [service]` | Reload configuration without a full restart. |

Example:

```bash
sudo systemctl status nginx
sudo systemctl restart nginx
```

## Common Checks

| Command | Clear Description |
|---|---|
| `curl -I http://localhost` | Check response headers from the local server. |
| `curl -I https://[domain]` | Check an HTTPS site quickly. |
| `ss -tulnp` | See which process is listening on a port. |
| `ping [domain]` | Check if the host is reachable. |

Example:

```bash
curl -I http://localhost
ss -tulnp | grep :80
```

## Static Sites

| Command | Clear Description |
|---|---|
| `sudo mkdir -p /var/www/[site]` | Create a web root directory. |
| `sudo chown -R www-data:www-data /var/www/[site]` | Give the web server ownership if needed. |
| `index.html` | Default file served when a directory is requested. |

Example:

```bash
sudo mkdir -p /var/www/example
echo '<h1>Hello</h1>' | sudo tee /var/www/example/index.html
```

## Reverse Proxy

| Command | Clear Description |
|---|---|
| `proxy_pass http://127.0.0.1:[port];` | Forward traffic to an app server. |
| `proxy_set_header Host $host;` | Preserve the original host header. |
| `proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;` | Pass the client IP chain to the backend. |

Example:

```nginx
location / {
	proxy_pass http://127.0.0.1:3000;
	proxy_set_header Host $host;
	proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
}
```

## TLS And Domains

| Command | Clear Description |
|---|---|
| `server_name [domain];` | Match requests for a specific domain. |
| `listen 443 ssl;` | Accept HTTPS traffic on port 443. |
| `certbot --nginx` | Automatically configure HTTPS with Let’s Encrypt if available. |

Example:

```bash
sudo certbot --nginx
```

## Logs

| Command | Clear Description |
|---|---|
| `sudo tail -f /var/log/nginx/access.log` | Watch incoming requests live. |
| `sudo tail -f /var/log/nginx/error.log` | Watch server errors live. |
| `journalctl -u [service]` | Show logs for the service managed by systemd. |

Example:

```bash
sudo tail -f /var/log/nginx/access.log
```

## Where DevOps Engineers Use This

Use web server commands when you are deploying apps behind Apache or Nginx and need to keep them reachable.

- Host static sites and reverse proxy traffic to app servers.
- Check ports, config syntax, and response headers during rollout.
- Read logs quickly when a site is slow, broken, or returning errors.
