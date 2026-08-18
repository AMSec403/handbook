# Métricas y distancias administrativas
## METRICAS (Calidad del Camino)

El Costo o Metrica define que tan eficiente es un camino dentro de una misma tecnologia. Criterio: El valor mas BAJO siempre gana.

### A) Metricas de Rendimiento Inteligente (SD-WAN / SLA)

Se miden de forma automatica por el equipo en tiempo real, pero tu configuras manualmente las reglas y limites.

*   Metrica de Ancho de Banda
    *   Tipo: Capacidad estatica / Enlaces WAN.
    *   Ejemplo de Aplicacion: Asignas una metrica baja (10) al enlace WAN1 (Fibra Dedicada) y una metrica alta (100) al enlace WAN2 (Linea de respaldo). El trafico preferira el canal de mayor capacidad (WAN1).

*   Metrica de Latencia
    *   Tipo: Retraso dinamico en milisegundos (ms).
    *   Ejemplo de Aplicacion: Enrutamiento de Telefonia IP (VoIP) o Video. Configuras una regla que mida los enlaces en tiempo real; si WAN1 tiene 20 ms y WAN2 tiene 80 ms, las llamadas se van por WAN1 para evitar retrasos en la voz.

*   Metrica de Jitter
    *   Tipo: Variacion del retraso dinamico (ms).
    *   Ejemplo de Aplicacion: Sesiones de Videoconferencias o Escritorios Virtuales (VDI). Si un enlace de internet satelital tiene un jitter muy inestable que congela las pantallas, el equipo lo detecta y cambia el trafico a un enlace de fibra con jitter bajo y constante.

*   Metrica de Perdida de Paquetes
    *   Tipo: Porcentaje de descarte de datos (%).
    *   Ejemplo de Aplicacion: Trafico critico de Bases de Datos o Transacciones Bancarias. Si un enlace de cobre empieza a fallar y pierde el 5% de los paquetes, el sistema saca el trafico de ahi para evitar corrupcion de datos.

*   Metrica Estatica (Prioridad Manual)
    *   Tipo: Forzado por el Administrador.
    *   Ejemplo de Aplicacion: Tienes dos enlaces iguales, pero el WAN2 cobra por Gigabyte consumido. Pones manualmente una metrica mejor en WAN1 para obligar al equipo a usar el enlace ilimitado por razones de costo comercial.


### B) Metricas de Protocolos Tradicionales

Calculadas automaticamente por el Router segun el tipo de protocolo fisico.

*   Conteo de Saltos (Hop Count)
    *   Tipo / Protocolo: Fijo por Router cruzado (RIP).
    *   Ejemplo de Aplicacion: Si hay dos caminos, uno de 2 routers (pero de baja velocidad) y uno de 4 routers (pero de fibra optica), RIP elegira el de 2 routers porque solo cuenta cajas, no velocidad.

*   Costo de Ancho de Banda
    *   Tipo / Protocolo: Calculo matematico automatico (OSPF).
    *   Ejemplo de Aplicacion: El router detecta la velocidad del cable y calcula el costo. Un enlace de 1 Gbps tendra un costo automatico de 1, mientras que uno de 10 Mbps tendra un costo de 10. OSPF elegira el de costo 1 (mas rapido).

*   Metrica Compuesta
    *   Tipo / Protocolo: Formula matematica mixta (EIGRP).
    *   Ejemplo de Aplicacion: El equipo analiza el Ancho de banda minimo y el Retraso acumulado en todo el trayecto del cable para calcular una sola metrica masiva y exacta.


---

## DISTANCIAS ADMINISTRATIVAS (Confiabilidad)

La Distancia Administrativa (AD) desempata cuando el router aprende el mismo destino por dos protocolos distintos. Criterio: El valor mas BAJO es el mas confiable.

### Guia Base de Configuracion (Valores Universales por Defecto)

Usa esta tabla como tu guia cuando necesites saber que protocolo esta pisando a otro en automatico:

| Origen de la Ruta | Distancia (AD) | ¿Quien lo determina? | ¿Como se usa en la vida real? |
| :--- | :---: | :--- | :--- |
| Interfaz Conectada | 0 | Automatico (Equipo) | El cable esta conectado directo al puerto del router. Maxima prioridad. |
| Ruta Estatica | 1 | Manual (Tu) | La escribes tu a mano. El router asume que tu sabes lo que haces y le cree antes que a nadie. |
| EIGRP (Interno) | 90 | Automatico (Equipo) | Protocolo dinamico propietario/avanzado. Muy confiable. |
| OSPF | 110 | Automatico (Equipo) | El estandar de la industria. Si hay OSPF y RIP activos, el router usara OSPF. |
| RIP | 120 | Automatico (Equipo) | Protocolo antiguo. El router desconfia de el si hay otra opcion mejor. |
| Inalcanzable | 255 | Automatico (Equipo) | El router descarta esta ruta, nunca la metera en su tabla de enrutamiento. |


### Ejemplo de Aplicacion Manual: La Ruta Flotante (Respaldo)

Si no configuras esto manualmente, las rutas estaticas normales (AD 1) siempre van a bloquear a tus protocolos dinamicos como OSPF (AD 110).

*   Problema: Quieres que tu red use OSPF (AD 110) de forma ordinaria para que sea automatico, pero si el enlace OSPF falla, quieres que se active una Ruta Estatica que apunta a un modem de respaldo.
*   Solucion Manual: Configuras tu ruta estatica cambiando su valor de fabrica (1) a un valor superior a OSPF, por ejemplo, 125.
*   Resultado: Mientras OSPF este vivo, el router prefiere el valor 110. Si OSPF se cae, esa ruta desaparece y la ruta estatica manual con AD 125 "flota" y salva la conexion.

---

### Recordatorio rapido de bolsillo para desempatar:

1. ¿Protocolos distintos? Mira la Distancia Administrativa (Tabla de arriba).
2. ¿Mismo protocolo, caminos distintos? Mira la Metrica (Apartado 1).
