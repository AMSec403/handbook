`compose.yaml`

```yaml
services:
  plex:
    image: lscr.io/linuxserver/plex:latest
    container_name: plex
    network_mode: host
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=America/Mexico_City
      - VERSION=docker
      - ALLOWED_NETWORKS=192.168.1.0/24,127.0.0.1/32
    volumes:
      # Cambiado a una ruta local en tu home para poder meter el archivo si falla
      - /home/user/plex_config:/config
      - /home/user/peliculas:/movies
      - /home/user/series:/tv
      - /home/user/cursos:/other
    restart: unless-stopped
```