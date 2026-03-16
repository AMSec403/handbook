# Linux Cheatsheet

## 🎯 Propósito
Referencia completa de comandos y prácticas esenciales para administración de sistemas Linux en entornos de infraestructura.

---

## 📂 Navegación y gestión de archivos
- `pwd` → muestra directorio actual
- `ls -la` → lista archivos con detalles, incluyendo ocultos
- `cd /path` → cambiar de directorio
- `find / -name archivo.txt` → buscar archivo en todo el sistema
- `du -sh *` → tamaño de archivos y directorios
- `df -h` → uso de disco por partición

---

## 👤 Usuarios y permisos
- `whoami` → usuario actual
- `id` → UID, GID y grupos
- `adduser usuario` → crear usuario
- `passwd usuario` → cambiar contraseña
- `usermod -aG grupo usuario` → agregar usuario a grupo
- `groups usuario` → mostrar grupos
- `chmod 640 archivo` → cambiar permisos
- `chown usuario:grupo archivo` → cambiar propietario

**Nota de experto:** usa `sudo visudo` para editar privilegios de sudo de forma segura.

---

## ⚙️ Procesos y servicios
- `ps aux` → lista procesos
- `top` / `htop` → monitor en tiempo real
- `kill -9 <PID>` → terminar proceso
- `systemctl status servicio` → estado de servicio
- `systemctl enable servicio` → habilitar servicio en arranque
- `journalctl -u servicio` → logs de un servicio

---

## 🌐 Red
- `ip a` → interfaces y direcciones IP
- `ip route` → tabla de rutas
- `ping -c 4 host` → prueba de conectividad
- `curl -I http://host` → cabeceras HTTP
- `netstat -tulnp` → puertos abiertos
- `ss -tulwn` → sockets activos
- `tcpdump -i eth0 port 80` → captura tráfico HTTP

**Nota de experto:** en sistemas modernos, `ss` reemplaza a `netstat`.

---

## 📦 Paquetes
### Debian/Ubuntu
- `apt update && apt upgrade` → actualizar sistema
- `apt install paquete` → instalar
- `apt remove paquete` → eliminar

### RHEL/CentOS
- `yum install paquete` → instalar
- `yum update` → actualizar
- `dnf install paquete` → nuevo gestor en versiones recientes

---

## 🕒 Logs y auditoría
- `tail -f /var/log/syslog` → seguimiento en tiempo real
- `less /var/log/auth.log` → autenticaciones
- `journalctl -xe` → eventos recientes
- `last` → últimos inicios de sesión
- `lastb` → intentos fallidos

---

## 🔑 Seguridad
- `ufw enable` → activar firewall (Ubuntu)
- `ufw allow 22/tcp` → permitir SSH
- `iptables -L -n -v` → reglas activas
- `fail2ban-client status` → estado de Fail2Ban

---

## 🧹 Administración avanzada
- `crontab -e` → editar tareas programadas
- `at now + 5 minutes` → ejecutar tarea en 5 minutos
- `mount /dev/sdb1 /mnt` → montar disco
- `umount /mnt` → desmontar
- `lsblk` → listar discos y particiones
- `df -Th` → uso de disco con tipo de sistema de archivos

---

## 🧰 Tips de experto
- Usa `alias` para personalizar comandos frecuentes (`alias ll='ls -la'`).  
- Aprovecha `grep`, `awk` y `sed` para manipulación avanzada de texto.  
- Documenta cambios en `/etc` y usa control de versiones para configuraciones críticas.  
- Automatiza tareas repetitivas con scripts en Bash.  
