# Linux Cheatsheet

## 📂 Navegación de archivos
- `pwd` → muestra el directorio actual
- `ls` → lista archivos
- `ls -la` → lista archivos con detalles, incluyendo ocultos
- `cd <dir>` → cambiar de directorio
- `cd ..` → subir un nivel

## 📄 Manipulación de archivos
- `touch file.txt` → crear archivo vacío
- `cp origen destino` → copiar archivo
- `mv origen destino` → mover/renombrar archivo
- `rm file.txt` → eliminar archivo
- `rm -r dir/` → eliminar carpeta y contenido

## 🔑 Permisos
- `chmod 755 file` → cambiar permisos
- `chown usuario:grupo file` → cambiar propietario

## ⚙️ Procesos
- `ps aux` → lista procesos
- `top` → monitor de procesos en tiempo real
- `kill <PID>` → terminar proceso
- `htop` → monitor avanzado (si está instalado)

## 🌐 Red
- `ifconfig` → mostrar interfaces de red
- `ip a` → mostrar interfaces y direcciones IP
- `ping google.com` → probar conectividad
- `netstat -tulnp` → mostrar puertos abiertos
- `curl http://example.com` → hacer petición HTTP
- `wget <url>` → descargar archivo desde la web

## 📦 Paquetes (Debian/Ubuntu)
- `apt update` → actualizar lista de paquetes
- `apt upgrade` → actualizar paquetes
- `apt install <paquete>` → instalar paquete
- `apt remove <paquete>` → eliminar paquete

## 🧹 Otros útiles
- `clear` → limpiar pantalla
- `history` → mostrar historial de comandos
- `man <comando>` → abrir manual de un comando
