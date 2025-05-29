# 3. Legislación y cumplimiento del convenio colectivo
El diseño de nuestra estructura responde a las especificaciones del Convenio colectivo estatal del sector, que hemos consultado en el BOE (BOE-A-2025-7766).

✔Atributos clave definidos por el convenio
Para la tabla grupo-nivel, hemos definido atributos en base a lo estipulado legalmente:

- **Salario**: Salario bruto anual correspondiente al grupo-nivell.

- **Periodo de prueba**: Tiempo de prueba según el nivel.

- **Dias de vacaciones**: El convenio exige 23 días laborales de vacaciones para todas las categorías.

### Clasificación de grupos y niveles
Conforme al convenio:

- Grupo A: Alta dirección, funciones críticas y autonomía total.
- Grupo B (niveles 1-2): Gestión de proyectos con distintos grados de experiencia.
- Grupo C (niveles 1-3): Técnicos con competencias medias y experiencia variable.
- Grupo D (niveles 1-3): Personal administrativo-técnico con autonomía limitada.
- Grupo E (niveles 1-2): Tareas básicas con mínima autonomía y supervisión constante.

### Cumplimiento normativo
Hemos tomado las siguientes medidas:

- Asegurarnos de que cada grupo-nivel esté representado en la empresa, como exige el Área 2 del convenio.
- Todos los salarios se han ajustado y normalizado al formato numérico con punto decimal para evitar errores de inserción SQL.
- Aplicamos restricciones en la base de datos como claves foráneas y campos NOT NULL según las exigencias de integridad referencial del modelo relacional.
