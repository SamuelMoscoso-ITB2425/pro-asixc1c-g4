## ¿Cómo funciona?
Un sistema híbrido combina refrigeración por aire (CRAC) y refrigeración líquida (chillers)para optimizar la eficiencia térmica y adaptarse a diferentes tipos de cargas.

Al ser una CPD con un consumo pequeño, entre (3-4kw de media), no es necesario tilizar ambos sistemas simultaneamente, sin embargo, al tener intención de ampliar el alcance y el funcionamiento hemos decidido instalar un sistema hibrido.

El sistema de refrigeración líquida se mantendra en espera hasta que sea necesario, esto ayuda a una mayor flexibilidad y tener un respaldo en caso de falla en el sistema de aire.

### Refrigeración por aire

El aire acondicionado (a través de CRACs) enfría el aire, que se distribuye por suelos técnicos, conductos elevados o directamente en los pasillos fríos del data center

El CRAC absorbe el aire caliente de la sala, lo enfría mediante un evaporador interno y lo impulsa de vuelta como aire frío al pasillo frío o al falso suelo, sin requerir agua fría ni torres de enfriamiento externas

El aire frío entra por la parte frontal de los racks, absorbe el calor generado por los equipos de TI y sale como aire caliente por la parte trasera. Este aire caliente se recoge y se retorna a las unidades de climatización para repetir el ciclo



### Refrigeración líquida

Para racks con cargas térmicas muy elevadas (hasta 200 kW/rack), se utiliza refrigeración líquida.

El aire caliente de la sala es aspirado por la unidad CRAH.

El CRAH enfría el aire haciendo pasar el flujo a través de un serpentín por el que circula agua fría proveniente del chiller.

El agua calentada regresa al chiller, donde se enfría nuevamente mediante un ciclo de compresión y expansión.

 El sistema cambia automáticamente entre refrigeración por aire y por agua según la demanda térmica y las condiciones ambientales. Esto permite operar en modo seco para ahorrar agua y en modo húmedo cuando se requiere mayor capacidad de enfriamiento


![Proceso](./Coolin.png)

## Seguridad

Para garantizar la seguridad de la CPD delante de fugas o accidentes podemos añadir:

- Detección de fugas con sensores y sistemas de contención. 

Instalamos sensores de detección de líquidos en las zonas más críticas bajo los racks, en bandejas de tuberías y cerca de las unidades de refrigeración (CRAH, chillers, CDUs).

Los sensores están conectados al sistema BMS (Building Management System) o DCIM, que monitoriza en tiempo real y genera alertas automáticas ante cualquier presencia de líquido.

Al detectar una fuga, el sistema puede activar válvulas de corte automáticas para aislar la zona afectada y evitar la propagación del líquido, además de notificar al personal de mantenimiento.


- Redundancia (N+1) para garantizar operación continua.

Instalamos los equipos de refrigeración, en configuración N+1 (un equipo extra por cada N en operación). Así, si un equipo falla o debe ser aislado por una fuga, el sistema sigue funcionando sin interrupciones.

- Mantenimineto

Se realizan pruebas regulares de los sensores de fugas, válvulas automáticas y sistemas de alarma para garantizar su correcto funcionamiento.


## Ventajas

- Free-cooling: 
Cuando la temperatura exterior es suficientemente baja, el sistema puede usar aire exterior para enfriar el agua del chiller, reduciendo el uso de compresores y ahorrando energía. 

Al situarnos en un lugar con temperaturas bajas podemos sacar más provecho.

- Ahorro energético:
 Reduce el consumo de energía hasta un 74% respecto a la media global, logrando un PUE de 1,15, muy por debajo del estándar del sector.


## Insalación

Las unidades CRAC/CRAH estan ubicadas en los extremos o laterales de la sala.

Mientras que los Chillers (enfriadoras de agua) se encuentran situados fuera del edificio, conectados a los CRAH mediante tuberías de agua fría y caliente.

No es necesario que intslemos, por ahora, un cooling tower ya que no tenemos tanta capacidad en kw por lo que el chriller es suficinete. 


### Distribución

- Diseño Modular
    - Configuración escalable:
Las unidades se distribuyen en paralelo, con la separación recomendada (mínimo 0,5 m) para asegurar un crecimiento fácil y modular.

    - Acceso y flujo de aire:
Mantener caminos despejados para el flujo de aire y el acceso de técnicos.

    - Integración:
Conectar las unidades al data hall mediante tuberías o conductos aislados, usando conectores flexibles para reducir la transmisión de vibraciones.

    - Alta densidad:
En zonas de alta densidad, complementar el enfriamiento por aire con módulos de refrigeración líquida plug-and-play según necesidad.

- Base/Fundación

    - Base nivelada y con absorción de vibraciones:
Instalar sobre una base de hormigón nivelada con almohadillas de goma o amortiguadores para estabilidad y reducción de ruido/vibración.

Para distribuir el agua del chiller a la CPD tenemos tuberías aisladas que llevan agua fría/caliente entre chiller, CRAH y módulos líquidos	bajo suelo técnico.


#### Cantidad

Tenemos instalados un CARC y un CRAH al final de la zona calienta para absorber el aire caliente.

Los CRACs/CRAH suelen tener una capacidad de 7-10kw por lo que con uno es suficiente para satisfacer nustras necesidades.

Las dimmensiones son: 

    - Ancho: 650–800 mm

    - Alto: 1800–2000 mm

    - Fondo: 650–800 mm

El chiller tiene una capacidad de 5-10kw con unas dimensiones de:

    - Largo: 1000–1500 mm

    - Ancho: 800–1000 mm

    - Alto: 1000–1500 mm



![Disttribución](./)

| **Equipo** | **Capacidad** | **Precio por unidad (€)** | **Instalación (€)** | **Total estimado (€)** |
|------------|----------------|----------------------------|----------------------|--------------------------|
| CRAC       | 7–10 kW        | 8.000–15.000               | 2.000–4.000          | 10.000–19.000            |
| CRAH       | 7–10 kW        | 12.000–18.000              | 2.000–4.000          | 14.000–22.000            |
| Chiller    | 5–10 kW        | 10.000–15.000              | 2.000–4.000          | 12.000–19.000            |

