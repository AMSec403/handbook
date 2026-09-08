
# Guía de Instalación de Plex Media Server (100% Local / Offline) en Docker

Esta guía detalla el procedimiento para levantar un servidor de Plex en **Ubuntu Server (CLI)** utilizando **Docker Compose / Portainer**, configurado de manera que permita el acceso administrativo local **sin necesidad de iniciar sesión ni crear una cuenta en plex.tv**.

## 🚀 Requisitos Previos
* Tener Docker y Portainer instalados.
* Conocer el rango de tu red local (ej. `192.168.1.0/24`).
* Estar utilizando un navegador en modo **Incógnito** para evitar redirecciones guardadas en caché.

---

## 📝 Paso 1: Configurar el Docker Compose (Stack en Portainer)

Para evitar problemas de aislamiento de red y forzar el comportamiento local, es fundamental usar el modo de red `host` y mapear la configuración a una ruta física del usuario en lugar de un volumen oculto de Docker.

Crea un nuevo Stack con el siguiente contenido:

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
      # Define las redes que tendrán acceso de administrador sin loguearse:
      - ALLOWED_NETWORKS=192.168.1.0/24,127.0.0.1/32
    volumes:
      # Ruta local para el control total de la configuración:
      - /home/user/plex_config:/config
      # Carpetas de medios:
      - /home/user/peliculas:/movies
      - /home/user/series:/tv
      - /home/user/cursos:/other
    restart: unless-stopped
```
*(Nota: Recuerda reemplazar `/home/user/` por la ruta real de tu usuario en Ubuntu).*

---

## 🛠️ Paso 2: Inyectar Configuración Offline (Preferences.xml)

Si el contenedor arranca e intenta forzar la redirección web a internet, se debe inyectar manualmente la propiedad de red permitida en el archivo de preferencias nativo de Plex antes de inicializar la interfaz.

1. **Detén** el contenedor desde Portainer.
2. Abre la terminal CLI de tu Ubuntu Server y crea la estructura de carpetas necesaria:
   ```bash
   sudo mkdir -p "/home/user/plex_config/Library/Application Support/Plex Media Server/"
   ```
3. Crea y edita el archivo de preferencias:
   ```bash
   sudo nano "/home/user/plex_config/Library/Application Support/Plex Media Server/Preferences.xml"
   ```
4. Pega exactamente la siguiente configuración inicial y guarda el archivo (`Ctrl+O`, `Enter`, `Ctrl+X`):
   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Preferences allowedNetworks="192.168.1.0/24" AcceptedEULA="1"/>
   ```
5. **Inicia** nuevamente el contenedor desde Portainer.

---

## 🌐 Paso 3: Primer Acceso y Configuración

1. Cierra todas las pestañas previas y abre una ventana de **Incógnito / Navegación Privada** en tu navegador web actual.
2. Accede directamente a la URL local del servidor utilizando el puerto por defecto de Plex:
   ```text
   http://IP_DE_TU_SERVER:32400/web/index.html
   ```
3. Plex detectará que tu IP se encuentra dentro del rango autorizado en `Preferences.xml`. Te mostrará el asistente de bienvenida local donde podrás nombrar tu servidor y añadir las bibliotecas mapeadas (`/movies`, `/tv`, `/other`) directamente.

---

## ⚠️ Notas Importantes de Mantenimiento
* **Evita cerrar sesión:** Si en la interfaz web de Plex local ves un botón que te invita a "Iniciar sesión" arriba a la derecha, **ignóralo**. Si inicias sesión por accidente, el servidor se vinculará a la nube y perderás el acceso offline estricto.
* **Actualizaciones:** Al usar la imagen de `linuxserver/plex:latest`, puedes actualizar el contenedor de forma segura desde Portainer recreando la imagen; tus configuraciones locales en `/home/user/plex_config` se mantendrán intactas.
