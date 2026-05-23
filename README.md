# caddy-cloudflare-build

Custom Caddy image with the Cloudflare DNS module built in.

Automatically rebuilds and publishes a new image only when upstream Caddy updates.

---

## Image

```bash
ghcr.io/polecter/caddy-cloudflare:latest
```

Versioned tags:

```bash
ghcr.io/polecter/caddy-cloudflare:<version>
```

Example:

```bash
ghcr.io/polecter/caddy-cloudflare:2.11.3
```

---

## Included Module

```text
github.com/caddy-dns/cloudflare
```

---

## Docker Compose

```yaml
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
```

---

## Example Caddyfile

```caddy
example.com {
    tls {
        dns cloudflare {env.CLOUDFLARE_API_TOKEN}
    }

    reverse_proxy 192.168.1.10:8123
}
```
