# Proyecto de Asignación de Plazas Hoteleras para el Imserso

Este proyecto tiene como objetivo modernizar el proceso de asignación de plazas hoteleras para el Imserso, a través de la creación de una plataforma eficiente y justa. A continuación, se detallan los pasos y consideraciones clave para el desarrollo de este producto, así como el equipo responsable de su ejecución.

## Objetivo del Proyecto

El Imserso busca agilizar su proceso de asignación de plazas hoteleras, y para ello, hemos sido encomendados con la tarea de diseñar una plataforma que garantice una distribución justa de las mismas. El proyecto no solo consiste en la creación de la plataforma, sino también en la presentación y venta de la solución como si estuviera participando en un concurso público.

## Desarrollo del Producto

### Pasos a Seguir:

1. **Análisis de Requisitos:**
   - Comprender a fondo las necesidades y requisitos del Imserso.
   - Identificar los criterios clave para una asignación justa de plazas hoteleras.

2. **Diseño de la Plataforma:**
   - Desarrollar una interfaz intuitiva y fácil de usar.
   - Implementar algoritmos de asignación que cumplan con los criterios establecidos.

3. **Desarrollo Técnico:**
   - Utilizar tecnologías modernas y robustas para garantizar la eficiencia y la seguridad.
   - Integrar la plataforma con sistemas existentes del Imserso, si es necesario.

4. **Presentación y Venta:**
   - Preparar una propuesta sólida que destaque los beneficios y la innovación de la plataforma.
   - Demostrar la eficacia y la equidad del sistema de asignación.

## Equipo de Desarrollo

Este proyecto está siendo llevado a cabo por un equipo altamente competente, compuesto por:

- Pau Garcia
- Julián Merino
- Toni Faura
- Hugo Fernando Maria Rodriguez
- Paco Tudela

Este readme sirve como guía inicial para el desarrollo del proyecto. ¡Éxito en la creación de una solución innovadora y eficiente para el Imserso!

## Detalles de desarrollo - MVP

- Nos basamos en la siguiente estructura SQL para la MVP
- ![Alt text](images/tables_mvp.png)


- Fin de MVP: 
  - Procesar usuarios, programas y solicitudes con los criterios actuales de IMSERSO (es decir, sin incluir las nuestras).
  - Generar una puntuación por usuario.
  - Rankear las solicitudes.

- Tabla programas:
  - Contiene programa_id y el resto de características del programa.
  - Dos programas pueden tener idénticas características y diferentes fechas de entrada y/o salida.

-  Tabla solicitudes:
   -  Enlaza usuarios mediante usuario_id y programas mediante programa_id
   -  No contiene fechas, ya que las fechas son únicas para cada programa: un usuario se inscribe en una programa con unas fechas predeterminadas ofrecidas.
   -  En un futuro posterior a MVP se puede considerar enlazar más de un usuario a un programa/solicitud - problemas del futuro.

-  Trabajo inmediato:
   -  Inyectar datos en tabla usuarios (100 basta para probar)
   -  Inyectar datos en tabla programas:
      -  2 programas por región de destino (costa insular, costa peninsular, interior y ya iremos ampliando y definiendo cuando funcione) y origen diferente.
   - Inyectar datos en la tabla solicitudes:
     - Hacer combinaciones de usuario_id y programa_id (que no se repitan, es decir un mismo usuario no puede solicitar lo mismo dos veces)
     - Como idea: cada usuario pida todos los programas una vez, en esta MVP serían 100 usuarios * 6 programas (3 regiones, 2 programas por región) = 600 solicitudes, ¿no?

-  23/12/2023
   -  jumepe: he creado un fichero imserso_jmp.sql nuevo que cambia usuario_id a string y le mete el random de NIF del fichero de generación e inserción de datos gen_datos_simple.py
   -  He cambiado el fichero de generacion e inserción de datos gen_datos_simple.py
   -  He creado un fichero de generación e inserción de datos a la tabla programas gen_datos_programas.py que hace:
      -  Genera 10 programas
      -  programa_id int correlativo de 1-10
      -  nombre_programa con la sintaxis origen - destino
      -  fecha_salida y fecha_vuelta limitado a meses de invierno y fecha_vuelta es posterior a fecha_salida
      -  destino es aleatorio entre tres opciones: Costa insular, Costa peninsular e interior
      -  Todo esto se puede cambiar!
      -  ![Alt text](images/programas_01.png)
      -  ![Alt text](images/usuarios_01.png)
