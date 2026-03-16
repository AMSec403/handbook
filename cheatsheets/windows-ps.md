Perfecto, vamos a armar el **cheatsheet de PowerShell** completo, separado del de CMD, con cmdlets avanzados y ejemplos de automatización. Este documento está pensado para administradores de infraestructura que necesitan trabajar con objetos, pipelines y automatización en Windows.

```markdown
# PowerShell Cheatsheet

## 🎯 Propósito
Referencia completa de cmdlets y prácticas esenciales para administración de sistemas Windows con PowerShell.

---

## 📂 Navegación y archivos
- `Get-Location` → muestra directorio actual
- `Set-Location C:\` → cambiar de directorio
- `Get-ChildItem` → lista archivos y carpetas
- `Get-Content archivo.txt` → mostrar contenido de archivo
- `Set-Content archivo.txt "texto"` → escribir contenido en archivo
- `Copy-Item origen destino` → copiar archivo
- `Move-Item origen destino` → mover/renombrar archivo
- `Remove-Item archivo.txt` → eliminar archivo

---

## 👤 Usuarios y permisos
- `Get-LocalUser` → lista usuarios locales
- `Get-LocalGroup` → lista grupos locales
- `Get-LocalGroupMember Administrators` → miembros del grupo Administradores
- `New-LocalUser -Name "usuario" -Password (ConvertTo-SecureString "clave" -AsPlainText -Force)` → crear usuario
- `Add-LocalGroupMember -Group "Administrators" -Member "usuario"` → agregar usuario a grupo
- `Get-Acl archivo.txt` → ver permisos de archivo
- `Set-Acl archivo.txt (Get-Acl otro.txt)` → copiar permisos de otro archivo

---

## ⚙️ Información del sistema
- `Get-ComputerInfo` → información completa del sistema
- `Get-WmiObject Win32_OperatingSystem` → versión del SO
- `Get-WmiObject Win32_ComputerSystem` → detalles de hardware
- `Get-WmiObject Win32_BIOS` → información de BIOS
- `Get-HotFix` → lista actualizaciones instaladas

---

## 🔌 Red
- `Test-Connection host` → ping
- `Get-NetIPAddress` → direcciones IP
- `Get-NetIPConfiguration` → configuración de red
- `Get-NetTCPConnection` → conexiones TCP activas
- `Resolve-DnsName dominio.com` → consulta DNS
- `Get-NetRoute` → tabla de rutas

---

## 🕒 Procesos y servicios
- `Get-Process` → lista procesos
- `Stop-Process -Id <PID>` → terminar proceso
- `Start-Process notepad.exe` → iniciar proceso
- `Get-Service` → lista servicios
- `Restart-Service nombre` → reiniciar servicio
- `Set-Service nombre -StartupType Automatic` → configurar inicio automático

---

## 📦 Administración avanzada
- `Get-ScheduledTask` → lista tareas programadas
- `Register-ScheduledTask` → crear tarea programada
- `Get-EventLog -LogName Security -Newest 20` → últimos eventos de seguridad
- `Get-WinEvent -LogName System -MaxEvents 50` → eventos recientes del sistema
- `Get-ItemProperty "HKLM:\Software\Microsoft\Windows\CurrentVersion\Run"` → programas en inicio automático

---

## 🔑 Seguridad
- `Get-LocalUser | Select Name, Enabled` → usuarios y estado
- `Get-ItemProperty "HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies\System"` → políticas críticas
- `Get-Credential` → solicitar credenciales seguras
- `Export-Certificate -Cert Cert:\LocalMachine\My\<Thumbprint> -FilePath C:\cert.cer` → exportar certificado

---

## 🧹 Tips de experto
- Usa `Get-Help <cmdlet> -Detailed` para documentación completa.  
- Aprovecha `Select-Object`, `Format-Table` y `Export-Csv` para personalizar y exportar resultados.  
- Automatiza tareas con scripts `.ps1` y ejecútalos con `powershell.exe -File script.ps1`.  
- Combina pipelines (`|`) para procesar objetos de forma eficiente.  
- Usa `Import-Module` para cargar módulos adicionales y extender funcionalidades.  
```

---

### ✅ Resultado
- **`powershell.md`** → cheatsheet completo de PowerShell, separado del de CMD.  
- Incluye navegación, usuarios, sistema, red, procesos, seguridad y tips de automatización.  
- Pensado para administradores de infraestructura que trabajan con objetos y pipelines.  

👉 El siguiente paso lógico sería preparar un **cheatsheet de Active Directory en PowerShell**, ¿quieres que lo arme como complemento?
