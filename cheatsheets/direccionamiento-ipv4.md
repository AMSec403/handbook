# 🌐 Direccionamiento IPv4

Este documento resume conceptos clave sobre direccionamiento IPv4, máscaras de red, rangos privados y rangos reservados para pruebas.

---

## 📖 Tabla Completa de Máscaras de Red

| Prefijo CIDR | Máscara de Subred | Bits de Host | Nº de Hosts    |
| ------------ | ----------------- | ------------ | -------------- |
| /0           | 0.0.0.0           | 32           | 4,294,967,294  |
| /1           | 128.0.0.0         | 31           | 2,147,483,646  |
| /2           | 192.0.0.0         | 30           | 1,073,741,822  |
| /3           | 224.0.0.0         | 29           | 536,870,910    |
| /4           | 240.0.0.0         | 28           | 268,435,454    |
| /5           | 248.0.0.0         | 27           | 134,217,726    |
| /6           | 252.0.0.0         | 26           | 67,108,862     |
| /7           | 254.0.0.0         | 25           | 33,554,430     |
| /8           | 255.0.0.0         | 24           | 16,777,214     |
| /9           | 255.128.0.0       | 23           | 8,388,606      |
| /10          | 255.192.0.0       | 22           | 4,194,302      |
| /11          | 255.224.0.0       | 21           | 2,097,150      |
| /12          | 255.240.0.0       | 20           | 1,048,574      |
| /13          | 255.248.0.0       | 19           | 524,286        |
| /14          | 255.252.0.0       | 18           | 262,142        |
| /15          | 255.254.0.0       | 17           | 131,070        |
| /16          | 255.255.0.0       | 16           | 65,534         |
| /17          | 255.255.128.0     | 15           | 32,766         |
| /18          | 255.255.192.0     | 14           | 16,382         |
| /19          | 255.255.224.0     | 13           | 8,190          |
| /20          | 255.255.240.0     | 12           | 4,094          |
| /21          | 255.255.248.0     | 11           | 2,046          |
| /22          | 255.255.252.0     | 10           | 1,022          |
| /23          | 255.255.254.0     | 9            | 510            |
| /24          | 255.255.255.0     | 8            | 254            |
| /25          | 255.255.255.128   | 7            | 126            |
| /26          | 255.255.255.192   | 6            | 62             |
| /27          | 255.255.255.224   | 5            | 30             |
| /28          | 255.255.255.240   | 4            | 14             |
| /29          | 255.255.255.248   | 3            | 6              |
| /30          | 255.255.255.252   | 2            | 2              |
| /31          | 255.255.255.254   | 1            | 0*             |
| /32          | 255.255.255.255   | 0            | 1 (host único) |

> En `/31` se usa en enlaces punto a punto, por lo que no se restan direcciones.  
> En `/32` se refiere a una sola dirección IP.

---

## 🏠 Rangos Privados (RFC 1918)

| Clase | Rango CIDR     | Rango de Direcciones          | Máscara     |
| ----- | -------------- | ----------------------------- | ----------- |
| A     | 10.0.0.0/8     | 10.0.0.0 – 10.255.255.255     | 255.0.0.0   |
| B     | 172.16.0.0/12  | 172.16.0.0 – 172.31.255.255   | 255.240.0.0 |
| C     | 192.168.0.0/16 | 192.168.0.0 – 192.168.255.255 | 255.255.0.0 |

---

## 🔧 Rangos Reservados y de Prueba

| Rango CIDR      | Descripción                                                                     |
| --------------- | ------------------------------------------------------------------------------- |
| 0.0.0.0/8       | Usado para identificar hosts en la red local. No se enruta en Internet.         |
| 127.0.0.0/8     | Direcciones de loopback (ejemplo: 127.0.0.1). Se utilizan para pruebas locales. |
| 169.254.0.0/16  | Direcciones link-local (APIPA). Asignadas automáticamente si no hay DHCP.       |
| 192.0.2.0/24    | Bloque reservado para documentación y ejemplos. No se usa en producción.        |
| 198.51.100.0/24 | Reservado para documentación.                                                   |
| 203.0.113.0/24  | Reservado para documentación.                                                   |
| 100.64.0.0/10   | Direcciones para Carrier-Grade NAT (CGNAT). Usadas por proveedores de Internet. |

---

## 🚀 Recursos útiles

- [RFC 1918 - Address Allocation for Private Internets](https://www.rfc-editor.org/rfc/rfc1918)
- [RFC 5737 - IPv4 Address Blocks for Documentation](https://www.rfc-editor.org/rfc/rfc5737)
- [Subnet Calculator](https://www.subnet-calculator.com/)


