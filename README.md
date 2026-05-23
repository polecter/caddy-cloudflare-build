# caddy-cloudflare-build

Custom Caddy image with the Cloudflare DNS module.

Automatically rebuilds and publishes a new image only when upstream Caddy updates.

Image:
ghcr.io/polecter/caddy-cloudflare:latest

Versioned tags:
ghcr.io/polecter/caddy-cloudflare:<version>

Included module:
github.com/caddy-dns/cloudflare

Docker Compose:

services:
  caddy:
    image: ghcr.io/polecter/caddy-cloudflare:latest
    container_name: caddy
    restart: unless-stopped

    ports:
      - "80:80"
      - "443:443"

    environment:
      CLOUDFLARE_API_TOKEN: your_token_here

    volumes:
      - ./Caddyfile:/etc/caddy/Caddyfile
      - ./data:/data
      - ./config:/config
