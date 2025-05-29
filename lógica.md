# Seguridad lógica
En nuestra organización, la protección de los datos y la infraestructura es prioritaria. Por ello, aplicamos una combinación de barreras técnicas y procedimientos para asegurar que solo el personal autorizado pueda acceder a los sistemas críticos, garantizar la integridad de la información y asegurar la continuidad del servicio. A continuación, detallamos las principales medidas implementadas en cinco bloques clave.

# RESTRICIÓN

- **Control de acceso por roles (RBAC)**: Limitamos el acceso a sistemas y recursos según las responsabilidades de cada usuario. Solo el personal autorizado puede acceder a información o sistemas críticos.

- **Autenticación multifactor (MFA)**: El acceso por SSH a servidores solo es posible mediante clave pública y un segundo factor (MFA), reforzando la seguridad de las credenciales.

- **Gestión centralizada de usuarios**: Utilizamos LDAP para la administración de usuarios y listas de control de acceso (ACL) para restringir el acceso a carpetas y recursos sensibles.

- **Registro de auditoría**: Todos los accesos quedan registrados, permitiendo saber quién accede, cuándo y qué acciones realiza.

- **Desconexión automática**: En caso de emergencia (sobrecalentamiento, fallo de hardware, malware), los servidores pueden aislarse o desconectarse automáticamente del resto de la infraestructura para evitar propagación de fallos o incidentes de seguridad.
  
# FIREWALL

- **Firewall perimetral**: Instalamos un firewall **FortiGate 1800F** en modo transparente, lo que permite filtrar el tráfico sin modificar la estructura de red existente. Este equipo ofrece protección de alto rendimiento y opera en la capa 2, actuando como un "internal segmentation firewall" para separar segmentos de red y proteger tanto los servidores como la salida de usuarios.

- **Filtrado de tráfico**: Solo se permite el tráfico HTTP/HTTPS (puertos 80/443) y SSH (22) desde IPs específicas de administración. Todo el tráfico no autorizado es denegado.

- Protección avanzada:

  - Protección contra ataques DDoS y bloqueo de IPs maliciosas (Spamhaus).

  - Limitación de peticiones HTTP/HTTPS a 50 req/segundo por IP.

  - Defensa ante ataques SYN (SYN Cookies, redefinición de reintentos, limitación de paquetes UDP a      1000/segundo por IP).

  - Bloqueo de tráfico internacional, permitiendo solo tráfico nacional según la política del            servicio.
  
  - Priorización del tráfico HLS/DASH para garantizar la calidad de servicios de vídeo en tiempo         real.

- **Firewall interno**: Segmenta la red mediante VLANs y ACLs, separando servidores, usuarios y dispositivos críticos.

# BACKUPS
- **Backups automáticos**: Realizamos copias de seguridad diarias, semanales y mensuales, almacenadas tanto en ubicaciones físicas separadas (off-site) como en la nube.

- **Cifrado:** Todas las copias están encriptadas para garantizar la confidencialidad de la información.

- **Pruebas de restauración**: Se realizan pruebas periódicas para asegurar la funcionalidad y fiabilidad de los backups.

- **Aislamiento**: En caso de incidente grave, los backups permiten restaurar sistemas afectados sin comprometer la integridad del resto de la infraestructura.

# MONITORIZACIÓN
- **Monitorización de hardware y servicios**: Utilizamos herramientas nativas de Linux.
Detección de intrusos: Fail2Ban bloquea IPs tras varios intentos fallidos de acceso por SSH o web, reforzando la protección ante ataques de fuerza bruta.

- **Centralización de logs**: Graylog centraliza y analiza los registros de Nginx, kernel y SSH, permitiendo una visión integral de la actividad del sistema.

-**Alertas automáticas**: Configuramos notificaciones a Telegram/email ante eventos críticos: hardware al límite, fallos en discos RAID, múltiples intentos de login fallidos, etc.

- **SIEM e IDS/IPS**: Integramos sistemas de monitorización de eventos de seguridad y detección de intrusiones para una protección proactiva y en tiempo real.
  
# RAIDs
- **Configuración RAID 10**:

  - Combinamos espejado (RAID 1) y distribución por bloques (RAID 0), de modo que cada disco impar       tiene su copia en el siguiente disco par.

  - Los pares de discos (1-2, 3-4, etc.) se agrupan en stripes para formar un volumen único de alta      velocidad y alta disponibilidad.

- **Ventajas**:

  - Alta tolerancia a fallos: si un disco falla, su copia mantiene la integridad de los datos.

  - Mayor velocidad de lectura y escritura.

  - Reducción del riesgo de pérdida de datos y mejora de la continuidad del servicio.
