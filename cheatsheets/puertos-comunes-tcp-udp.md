# 🔌 Puertos Comunes TCP/UDP

---

## 📖 Puertos Conocidos (0–1023)

| Puerto          | Protocolo | Uso Principal                         |
| --------------- | --------- | ------------------------------------- |
| 20/tcp          | FTP-Data  | Transferencia de datos FTP            |
| 21/tcp          | FTP       | Control de sesión FTP                 |
| 22/tcp          | SSH       | Acceso remoto seguro                  |
| 23/tcp          | Telnet    | Acceso remoto inseguro (obsoleto)     |
| 25/tcp          | SMTP      | Envío de correo electrónico           |
| 53/tcp/udp      | DNS       | Resolución de nombres de dominio      |
| 67/udp          | DHCP      | Servidor DHCP                         |
| 68/udp          | DHCP      | Cliente DHCP                          |
| 69/udp          | TFTP      | Transferencia simple de archivos      |
| 80/tcp          | HTTP      | Navegación web                        |
| 88/tcp          | Kerberos  | Autenticación en redes                |
| 110/tcp         | POP3      | Recepción de correo electrónico       |
| 119/tcp         | NNTP      | Usenet (grupos de noticias)           |
| 123/udp         | NTP       | Sincronización de hora                |
| 135/tcp         | RPC       | Servicios remotos en Windows          |
| 137-139/tcp/udp | NetBIOS   | Compartición de archivos en Windows   |
| 143/tcp         | IMAP      | Recepción de correo electrónico       |
| 161/udp         | SNMP      | Administración de red                 |
| 179/tcp         | BGP       | Enrutamiento entre sistemas autónomos |
| 443/tcp         | HTTPS     | Navegación web segura                 |
| 445/tcp         | SMB       | Compartición de archivos en Windows   |
| 465/tcp         | SMTPS     | SMTP seguro                           |
| 514/udp         | Syslog    | Registro de eventos                   |
| 587/tcp         | SMTP      | Envío de correo autenticado           |
| 636/tcp         | LDAPS     | LDAP seguro                           |
| 993/tcp         | IMAPS     | IMAP seguro                           |
| 995/tcp         | POP3S     | POP3 seguro                           |

---

## 📖 Puertos Registrados (1024–49151)

| Puerto       | Protocolo  | Uso Principal                       |
| ------------ | ---------- | ----------------------------------- |
| 1433/tcp     | MSSQL      | Microsoft SQL Server                |
| 1521/tcp     | Oracle     | Oracle Database                     |
| 1723/tcp     | PPTP       | VPN (obsoleto)                      |
| 3306/tcp     | MySQL      | MySQL/MariaDB                       |
| 3389/tcp     | RDP        | Escritorio remoto de Windows        |
| 5060/tcp/udp | SIP        | Telefonía VoIP                      |
| 5432/tcp     | PostgreSQL | PostgreSQL Database                 |
| 5900/tcp     | VNC        | Control remoto gráfico              |
| 8080/tcp     | HTTP-alt   | Servidores web alternativos         |
| 8443/tcp     | HTTPS-alt  | Servidores web seguros alternativos |

---

## 📖 Puertos Dinámicos/Efímeros (49152–65535)

- Usados por aplicaciones cliente para establecer conexiones temporales.  
- No tienen asignación fija, pero suelen aparecer en sesiones de navegación web, correo, juegos en línea, etc.

---

## 📚 Recursos

- [Wikipedia: Puertos de red](https://es.wikipedia.org/wiki/Anexo:Puertos_de_red)  
- [IANA Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)
