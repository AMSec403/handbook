# FortiGate Cheatsheet (CLI)

## 🎯 Propósito
Referencia completa de comandos esenciales para administración de firewalls FortiGate con FortiOS.

---

## 📂 Modos de operación
- `config system global` → entrar a configuración global
- `config system interface` → configurar interfaces
- `config firewall policy` → configurar políticas de firewall
- `end` → salir de modo de configuración
- `show` → mostrar configuración actual
- `execute reboot` → reiniciar dispositivo
- `execute backup config flash` → respaldar configuración

---

## 🌐 Interfaces y red
- `config system interface`  
  - `edit port1`  
  - `set ip 192.168.1.1/24`  
  - `set allowaccess ping https ssh`  
  - `next`  
  - `end`  
- `diagnose netlink interface list` → estado de interfaces
- `execute ping 8.8.8.8` → prueba de conectividad
- `execute traceroute 8.8.8.8` → rastrear ruta
- `get router info routing-table all` → tabla de enrutamiento

---

## 🔀 Políticas de firewall
- `config firewall policy`  
  - `edit 1`  
  - `set srcintf "port1"`  
  - `set dstintf "port2"`  
  - `set srcaddr "all"`  
  - `set dstaddr "all"`  
  - `set action accept`  
  - `set schedule "always"`  
  - `set service "ALL"`  
  - `set nat enable`  
  - `next`  
  - `end`  
- `show firewall policy` → mostrar políticas activas

---

## 📦 Objetos
- `config firewall address` → crear objetos de dirección
- `config firewall service custom` → crear servicios personalizados
- `config firewall addrgrp` → grupos de direcciones

---

## 🔒 Seguridad y VPN
- `config vpn ipsec phase1-interface` → configurar túnel IPsec (fase 1)
- `config vpn ipsec phase2-interface` → configurar túnel IPsec (fase 2)
- `diagnose vpn tunnel list` → estado de túneles
- `diagnose vpn ike log-filter` → depuración de VPN

---

## 🕒 Logs y diagnóstico
- `get system performance status` → estado de CPU y memoria
- `diagnose sys top` → procesos activos
- `diagnose debug enable` → habilitar debug
- `diagnose debug application ike -1` → depuración de VPN
- `execute log filter category 1` → filtrar logs por categoría
- `execute log display` → mostrar logs

---

## 🧹 Administración avanzada
- `execute update-now` → actualizar firmas de seguridad
- `execute restore config flash` → restaurar configuración
- `execute factoryreset` → resetear a valores de fábrica
- `execute shutdown` → apagar dispositivo

---

## 🧰 Tips de experto
- Siempre usar `end` para aplicar cambios en configuraciones.  
- Documenta políticas y objetos con nombres descriptivos para facilitar troubleshooting.  
- Usa `diagnose` para depuración avanzada (VPN, interfaces, procesos).  
- Respaldar configuración antes de cambios críticos con `execute backup config`.  
- En producción, evita abusar de `diagnose debug` porque puede impactar rendimiento.  
