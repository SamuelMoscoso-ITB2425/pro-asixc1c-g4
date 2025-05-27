#SOSTENIBILIDAD
La sostenibilidad y la eficiencia energética son pilares fundamentales en el diseño y la gestión de nuestro CPD. 
El objetivo es minimizar el impacto ambiental, optimizar el uso de recursos y garantizar la máxima eficiencia operativa, sin comprometer la calidad ni la seguridad del servicio.

## Estrategias 

**1. Uso de Energías Renovables**

Para minimizar la huella de carbono del CPD, hemos incorporado fuentes de energía renovable como parte fundamental de la infraestructura energética:
- Paneles solares fotovoltaicos: Se han instalado 40 paneles solares de 500 W cada uno, capaces de generar hasta 20 kW de energía limpia. Esta energía renovable contribuye directamente a cubrir parte del consumo eléctrico del CPD, reduciendo la dependencia de la red eléctrica convencional y disminuyendo las emisiones de gases de efecto invernadero.
- Selección de proveedores de nube verde: Para los servicios en la nube, se priorizan proveedores que garantizan un porcentaje elevado de energía renovable en sus centros de datos, como AWS, Google Cloud o Azure, lo que permite que los servicios desplegados tengan una menor huella ambiental.

**2. Optimización de la Eficiencia Energética**

El diseño de la infraestructura se ha orientado a maximizar la eficiencia energética mediante diversas medidas:
- Sistema híbrido de refrigeración: La combinación de refrigeración por aire (CRAC/CRAH) y refrigeración líquida (chillers) permite adaptar el sistema a las necesidades térmicas reales, utilizando el free-cooling siempre que las condiciones ambientales lo permitan. Esto reduce el consumo energético de los compresores y mejora la eficiencia global del sistema.
- Diseño modular y escalable: La infraestructura permite ajustar la capacidad según la demanda, evitando sobredimensionamientos que implicarían un consumo innecesario de energía.
- Distribución física eficiente: La correcta organización de racks, patch panels y cableado estructurado facilita la circulación del aire frío y la extracción del aire caliente, lo que contribuye a mantener temperaturas óptimas con menor consumo energético.
- Sistemas de alimentación inteligentes: Los SAIs y PDU instalados no solo garantizan la continuidad eléctrica, sino que también permiten monitorizar y gestionar el consumo energético, detectando y previniendo situaciones de sobrecarga o desperdicio.

**3. Monitorización y Control Continuos**
Para asegurar la eficiencia y detectar posibles desviaciones, se implementan sistemas de monitorización avanzados:
- Sensores ambientales: Se instalan sensores para medir temperatura, humedad y concentración de partículas en tiempo real, lo que permite ajustar dinámicamente los sistemas de climatización y mantener un ambiente óptimo para los equipos.
- Software de gestión energética (DCIM/BMS): Estas plataformas integran la información de los sensores y equipos, facilitando la visualización, análisis y control del consumo energético, así como la automatización de acciones correctivas para optimizar la operación.

## Cálculo de la Huella Ecológica

#### Recursos utilizados:
Para realizar un cálculo preciso de la huella ecológica, primero se identifican los recursos y servicios desplegados:
- *Equipamiento principal*: Servidores HP DL380 Gen10 con procesadores Intel Xeon Silver 4210, memoria DDR4 ECC, almacenamiento SSD SAS, y switches Cisco Nexus 9336C-FX2.
- *Servicios*: Plataforma de streaming VOD para hasta 16.000 usuarios concurrentes, gestión de contenidos multimedia, monitorización y seguridad.
- *Consumo de recursos*: CPU, RAM, almacenamiento y ancho de banda configurados para soportar la carga prevista, con un bitrate estándar de 5 Mbps por usuario.
- *Previsión de uso*: Operación continua 24/7, con tráfico estimado de hasta 80 Gbps simultáneos.

### Estimaciones del Consumo Energético y Emisiones
**1. Consumo energético anual estimado**
- Servidores: 8 servidores x 250 W promedio x 8.760 horas/año = 17.520 kWh/año.

- Switches: 2 switches x 500 W x 8.760 horas/año = 8.760 kWh/año.

- Refrigeración: Sistema híbrido con consumo estimado de 10 kW x 8.760 horas/año = 87.600 kWh/año.

- Otros sistemas (SAIs, PDU, seguridad): Consumo estimado de 2 kW x 8.760 horas/año = 17.520 kWh/año.

*Total estimado: 131.400 kWh/año.*

**2. Conversión a CO₂**
- Factor de emisión medio regional: 0,23 kg CO₂ por kWh consumido (según Carbon Trust).

- Emisiones totales: 131.400 kWh x 0,23 kg CO₂/kWh = *30.222 kg CO₂ anuales*.

**3. Energiaa renovables**
- Generación solar anual estimada: 20 kW x 1.500 horas de sol al año = 30.000 kWh/año.

- Reducción de emisiones: 30.000 kWh x 0,23 kg CO₂/kWh = 6.900 kg CO₂ anuales.

- Emisiones netas estimadas: 30.222 – 6.900 = *23.322 kg CO₂ anuales*.

Se estima que nuetras emisiones anuales sean de ***23.322 kg CO₂ anuales***.

## Propuestas y Medidas para la Reducción y Optimización

**1. Reducción del consumo energético**
- *Maximizar el uso del free-cooling*: Aprovechar las condiciones climáticas para enfriar el CPD con aire exterior, disminuyendo el uso de compresores y chillers.
- *Virtualización y consolidación de servidores*: Reducir el número de servidores físicos mediante virtualización para mejorar la eficiencia en el uso de CPU y memoria, disminuyendo el consumo energético total.
- *Gestión dinámica de la carga*: Implementar políticas para apagar o poner en modo bajo consumo los equipos no esenciales durante periodos de baja demanda.

**2. Uso de servicios en la nube con energía renovable**
- *Monitorización de la huella de carbono*: Utilizar herramientas como AWS Carbon Footprint Calculator o Google Cloud Carbon Sense para medir y gestionar las emisiones asociadas a los servicios en la nube.
- *Selección de regiones eficientes*: Desplegar servicios en regiones cloud que utilicen energía renovable certificada y tengan centros de datos con alta eficiencia energética.




