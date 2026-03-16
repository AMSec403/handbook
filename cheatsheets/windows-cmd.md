# Windows Cheatsheet (CMD)

## 🎯 Propósito
Referencia completa de comandos y utilidades en **CMD** para administración de sistemas Windows.

---

## 📂 Navegación y archivos
- `dir` → lista archivos y carpetas
- `dir /b` → lista solo nombres
- `cd <carpeta>` → cambiar de directorio
- `cd ..` → subir un nivel
- `tree` → estructura de directorios
- `type archivo.txt` → mostrar contenido de archivo

---

## 👤 Usuarios y permisos
- `whoami` → usuario actual
- `whoami /groups` → grupos del usuario
- `net user` → lista usuarios locales
- `net user <usuario>` → detalles de usuario
- `net localgroup administrators` → muestra administradores
- `icacls archivo.txt` → permisos de archivo

---

## ⚙️ Información del sistema
- `systeminfo` → información detallada del sistema
- `hostname` → nombre del host
- `ver` → versión de Windows
- `wmic os get caption, version, buildnumber` → versión del SO
- `wmic computersystem get model,name,manufacturer` → detalles de hardware

---

## 🔌 Red
- `ipconfig /all` → configuración de red
- `ping host` → prueba de conectividad
- `netstat -ano` → puertos abiertos y PID
- `tracert dominio.com` → rastrear ruta
- `nslookup dominio.com` → resolver DNS

---

## 🕒 Procesos y servicios
- `tasklist` → lista procesos en ejecución
- `taskkill /PID <pid> /F` → terminar proceso
- `sc query` → lista servicios
- `sc stop <servicio>` → detener servicio
- `sc start <servicio>` → iniciar servicio

---

## 📦 Administración avanzada
- `schtasks /query /fo LIST /v` → tareas programadas
- `reg query HKLM\Software\Microsoft\Windows\CurrentVersion\Run` → claves de inicio automático
- `reg add HKCU\Software\Microsoft\Windows\CurrentVersion\Run /v MiApp /t REG_SZ /d "C:\ruta\app.exe"` → agregar programa al inicio
- `eventvwr` → abrir visor de eventos

---

## 🔑 Seguridad
- `net accounts` → políticas de cuentas
- `secedit /export /cfg config.inf` → exportar configuración de seguridad
- `cipher /w:C:\` → limpiar espacio libre (borrado seguro)
- `gpresult /R` → políticas aplicadas al usuario y equipo

---

## 🧰 Herramientas del sistema
- `cleanmgr` → abre el Liberador de espacio en disco  
- `cleanmgr /sageset:1` → configura opciones avanzadas de limpieza  
- `cleanmgr /sagerun:1` → ejecuta limpieza con perfil configurado  
- `taskmgr` → abre el Administrador de tareas  
- `regedit` → abre el Editor del Registro  
- `eventvwr` → abre el Visor de eventos  
- `msconfig` → abre Configuración del sistema  
- `msinfo32` → abre Información del sistema  
- `resmon` → abre el Monitor de recursos  
- `mdsched` → abre Diagnóstico de memoria  
- `services.msc` → abre consola de servicios  
- `wf.msc` → abre configuración avanzada del Firewall  

---

## 🧰 Herramientas adicionales
- `perfmon /rel` → abre el **Monitor de confiabilidad**  
- `netplwiz` → abre la consola de **Cuentas de usuario avanzadas**  
- `control userpasswords2` → acceso alternativo a cuentas de usuario  
- `lusrmgr.msc` → administrador de usuarios y grupos locales (no disponible en ediciones Home)  

---

## 🧹 Tips de experto
- Usa `wmic` para consultas rápidas de hardware y sistema.  
- Documenta cambios en el registro con `reg export` antes de modificar claves críticas.  
- Automatiza tareas repetitivas con **batch scripts (.bat)**.  
- El **Monitor de confiabilidad** es clave para diagnosticar problemas recurrentes.  
- `netplwiz` permite configurar inicio de sesión automático y credenciales avanzadas.  
