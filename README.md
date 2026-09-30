# 🍓 Home Server — Raspberry Pi

Configuración (Docker Compose, gestionada con Portainer) de mi servidor casero en una Raspberry Pi.
Los secretos están fuera del repo: cada servicio con credenciales trae un `.env.example`.

## Servicios

| Servicio | Carpeta | Puerto(s) | Para qué |
|---|---|---|---|
| Pi-hole | `pihole/` | 53, 8053 | DNS y bloqueo de anuncios |
| Dashy | `dashy/` | 4000 | Dashboard de inicio |
| Beszel | `beszel/` | 8090 | Monitoreo de recursos (hub + agentes) |
| Uptime Kuma | `uptime-kuma/` | 3001 | Monitoreo de disponibilidad |
| Nginx Proxy Manager | `nginx-proxy-manager/` | 80, 81, 4443 | Reverse proxy |
| Immich | `immich/` | 2283 | Galería de fotos (almacenada en HDD externo) |
| Minecraft (Fabric) | `minecraft/` | 25565 | Servidor de juego + panel RCON |
| Cloudflared | `cloudflared/` | — | Túnel Cloudflare |
| Palworld | `palworld/` | 8211/udp | Servidor de juego |

## Uso

```bash
cd <servicio>
cp .env.example .env   # si existe; edita los valores
docker compose up -d
```

## Notas
- Almacenamiento: SD para el sistema, HDD montado en `/mnt/hdd` para datos pesados.
- Límites de CPU/RAM definidos por servicio para no saturar la Pi.
