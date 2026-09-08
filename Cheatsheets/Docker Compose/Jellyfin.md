`compose.yaml`
```yaml
services:
  jellyfin:
    image: jellyfin/jellyfin:latest
    container_name: jellyfin
    user: 1000:1000
    network_mode: host
    volumes:
      - jellyfin_config:/config
      - jellyfin_cache:/cache
      - /home/user/peliculas:/media/peliculas  # Carpeta en tu servidor donde guardarás las películas
      - /home/user/series:/media/series        # Carpeta en tu servidor donde guardarás las series
      - /home/user/cursos:/media/cursos        # Carpeta en tu servidor donde guardarás las cursos
    restart: unless-stopped

volumes:
  jellyfin_config:
  jellyfin_cache:
```