`compose.yaml`

```yaml
version: "3.5"

services:
  db:
    image: mariadb:10.5
    container_name: librenms_db
    command:
      - --innodb-file-per-table=1
      - --lower-case-table-names=1
      - --character-set-server=utf8mb4
      - --collation-server=utf8mb4_unicode_ci
    volumes:
      - librenms_db:/var/lib/mysql
    environment:
      - TZ=America/Mexico_City
      - MYSQL_ALLOW_EMPTY_PASSWORD=yes
      - MYSQL_DATABASE=librenms
      - MYSQL_USER=librenms
      - MYSQL_PASSWORD=librenms_password
    restart: always

  redis:
    image: redis:6.2-alpine
    container_name: librenms_redis
    environment:
      - TZ=America/Mexico_City
    restart: always

  librenms:
    image: librenms/librenms:latest
    container_name: librenms
    hostname: librenms
    ports:
      - "80:8000"
    volumes:
      - librenms_data:/data
    environment:
      - TZ=America/Mexico_City
      - PUID=1000
      - PGID=1000
      - DB_HOST=db
      - DB_NAME=librenms
      - DB_USER=librenms
      - DB_PASSWORD=librenms_password
      - REDIS_HOST=redis
      - SIDE_CONTAINER=1
    depends_on:
      - db
      - redis
    restart: always

  syslogng:
    image: librenms/librenms:latest
    container_name: librenms_syslogng
    hostname: librenms-syslogng
    cap_add:
      - NET_ADMIN
      - NET_RAW
    ports:
      - "514:514/tcp"
      - "514:514/udp"
    volumes:
      - librenms_data:/data
    environment:
      - TZ=America/Mexico_City
      - PUID=1000
      - PGID=1000
      - DB_HOST=db
      - DB_NAME=librenms
      - DB_USER=librenms
      - DB_PASSWORD=librenms_password
      - REDIS_HOST=redis
      - SIDECAR_SYSLOGNG=1
    depends_on:
      - librenms
      - redis
    restart: always

volumes:
  librenms_data:
  librenms_db:

```


```bash
sudo docker compose exec -u librenms librenms php /opt/librenms/artisan user:add -p pwddblibrenms -e admin@noc.local -r admin admin
```

