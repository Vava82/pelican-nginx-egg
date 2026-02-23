# Nginx Cloudflare Egg

A versatile **Pelican Panel Egg** featuring Nginx, PHP 8.x, WordPress, Git, Composer, Cronjob, ionCube Loader, Auto-Update, and Cloudflare Tunnel support.

**Fork by Vava22**, originally adapted from [Ym0T's Pterodactyl Nginx Egg](https://github.com/Ym0T/pterodactyl-nginx-egg).

## Features

- 🔄 **Auto-Update**: Automatically checks for and applies updates via Tavuru API
- 🧹 **LogCleaner**: Cleans `/tmp` and old logs (dry-run supported)
- 🌱 **Git Module**: Auto `git pull` on restart
- 📦 **Composer Module**: Installs packages from `composer.json` or a fallback variable
- 🔐 **ionCube Loader**: Auto-detected and enabled for encrypted PHP
- 🌐 **Cloudflare Tunnel**: Secure tunnel with token validation
- 🚀 **PHP-NGINX Startup**: Auto-detects PHP-FPM version, runs NGINX in foreground
- 🖥️ **Multi-arch support**: AMD64 & ARM64
- 🎯 **Selectable PHP Versions**:
  - ✅ 8.5
  - ✅ 8.4
  - ☑️ 8.3 (security-only)
  - ☑️ 8.2 (security-only)
  - ❌ 8.1 (EOL)

[PHP Supported Versions](https://www.php.net/supported-versions.php)

## Installation

1. Download the egg file (`egg-pelican-nginx.json`).
2. In your **Pelican Panel**, navigate to **Nests** in the sidebar.
3. Click **Import Egg**.
4. Create a new server and select the **Pelican Nginx** egg.
5. Choose the Docker image matching your desired PHP version.
6. Fill in all required variables, including whether **WordPress** is desired and the PHP version field (must be set explicitly).

## Configuration

| Variable | Default | Description |
| :--- | :--- | :--- |
| `AUTOUPDATE_STATUS` | `1` | Enable (`1`) or disable (`0`) auto-update checks |
| `AUTOUPDATE_FORCE` | `1` | Automatically apply updates (`1`) or just check (`0`) |
| `PHP_VERSION` | - | **Required**. Must match the Docker image tag (e.g., `8.4`) |
| `WORDPRESS` | `0` | Set to `1` to install WordPress automatically |
| `CLOUDFLARED_STATUS` | `0` | Enable Cloudflare Tunnel (`1`) |
| `CLOUDFLARED_TOKEN` | - | Your Cloudflare Tunnel token (starts with `ey...`) |

### Cloudflare Tunnel Setup

1. Create a tunnel in your [Cloudflare Zero Trust Dashboard](https://one.dash.cloudflare.com/).
2. Copy the token provided by Cloudflare.
3. Set `CLOUDFLARED_STATUS` to `1` (or `true`) in the server Startup settings.
4. Paste the token into the `CLOUDFLARED_TOKEN` variable.
5. Start the server.

### SSL with Certbot

To enable automatic SSL via Let's Encrypt:
1. Set `CERTBOT_STATUS` to `1`.
2. Configure `CERTBOT_EMAIL` and `CERTBOT_DOMAIN`.
3. Follow the instructions in the server console to add the required DNS TXT record.

## Credits

- **Fork & Adaptation for Pelican**: Vava22
- **Original Author**: [Ym0T](https://github.com/Ym0T)
- **Original Repository**: [pterodactyl-nginx-egg](https://github.com/Ym0T/pterodactyl-nginx-egg)

## License

[MIT License](https://choosealicense.com/licenses/mit/)
