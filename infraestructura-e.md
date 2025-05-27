# SISTEMAS DE ALIMENTACIÓN

La continuidad eléctrica es crítica para la operación ininterrumpida del CPD. Para ello, hemos implementado una arquitectura de alimentación redundante basada en:

**Doble acometida eléctrica**: El CPD dispone de dos líneas independientes de suministro, minimizando el riesgo de corte total.

**Paneles solares**: Instalación de 40 paneles solares de 500 W cada uno, aportando hasta 20 kW de energía renovable, que contribuyen a la sostenibilidad y reducen la dependencia de la red eléctrica.

**SAIs (Sistemas de Alimentación Ininterrumpida)**:

- 2 x APC Smart-UPS Ultra 5kVA 2U por rack, garantizando alimentación limpia y estable a todos los equipos críticos.

- Los SAIs filtran y estabilizan la corriente, eliminando picos, caídas y “ruido” eléctrico, y proporcionan energía instantánea en caso de fallo de red.

**PDU (Power Distribution Unit):**
Modelo AP8861, que permite la distribución eficiente y monitorizada de energía en cada rack, con protección ante sobrecargas y gestión remota.

# Autonomía y cálculo de componentes
Consumo estimado de equipos principales
Servidores HP DL380 Gen10 8SFF:

- Consumo por servidor: 150–350 W (típico/pico).

4 servidores por rack: 600–1.400 W por rack.

Switch Cisco Nexus 9336C-FX2:

Consumo típico: 367–650 W (según configuración y carga).

Autonomía proporcionada
Racks de red:

Autonomía estimada: 80 minutos con la configuración actual de SAIs y carga.

Racks de servidores:

Autonomía estimada: 18 minutos bajo carga máxima, suficiente para permitir el arranque de generadores o el apagado controlado de los sistemas en caso de corte prolongado.

> [!NOTA] 
> : La autonomía real depende de la carga conectada y el estado de las baterías. Es recomendable revisar periódicamente el sistema y ajustar la capacidad de los SAIs si se amplía la infraestructura 
