# TAS9 - Contenedor frontend
## 1. Título  
Contenerización de una Aplicación Frontend
## 2. Tiempo de duración  
El tiempo fue de 200 minutos. 

## 3. Fundamentos

### Dockerfile 

Un contenedor Docker tiene una vida limitada e interactúa con su entorno. Imagina que contenedor es como un organismo vivo. Piensa en un organismo unicelular, como una célula de levadura. Siguiendo esta analogía, una imagen Docker equivale, digamos, a la información genética: todos los contenedores creados a partir de una imagen son iguales, como todos los organismos unicelulares clonados a partir de una unidad de información genética. El Dockerfile define los pasos a seguir para crear una nueva imagen. Hay que entender que se empieza siempre con una imagen base existente. La nueva imagen nace de la imagen base. Además, hay ciertos cambios puntuales. En nuestro ejemplo de la célula de levadura, los cambios serían mutaciones (¿Qué Es El Dockerfile? - IONOS, n.d.). 

### ¿Cómo funciona un Dockerfile y cómo se crea una imagen a partir de él?

Dockerfile es un archivo de texto totalmente normal. El Dockerfile contiene un conjunto de instrucciones, cada una en una línea distinta. Para crear una Docker Image, las instrucciones se ejecutan una tras otra. Quizás te suene este esquema de la ejecución de un script por lotes. Durante la ejecución, se añaden paso por paso más capas a la imagen.  Una imagen Docker se crea ejecutando las instrucciones de un Dockerfile. Este paso se conoce como el proceso build y empieza con la ejecución del comando “docker build”. El contexto de construcción es un concepto crucial: define a qué archivos y directorios tiene acceso el proceso de construcción, donde un directorio local hace las veces de fuente. El contenido del directorio fuente se transfiere al Docker Daemon al accionar “docker build”. Las instrucciones contenidas en el Dockerfile reciben acceso a los archivos y directorios contenidos en el contexto de construcción (¿Qué Es El Dockerfile? - IONOS, n.d.).

<img src="./back/dfile.jpeg" alt="contenedor react docker" width="500"/>


### Multi-stage buils

En una compilación tradicional, todas las instrucciones se ejecutan en secuencia y en un único contenedor: descarga de dependencias, compilación de código y empaquetado de la aplicación. Todas estas capas se convierten en la imagen final. Este enfoque funciona, pero genera imágenes voluminosas que pesan innecesariamente y aumentan los riesgos de seguridad. Aquí es donde entran en juego las compilaciones multietapa.(Compilaciones Multietapa | Documentación de Docker, n.d.)

Las compilaciones multietapa introducen varias etapas en tu Dockerfile, cada una con un propósito específico. Piénsalo como la capacidad de ejecutar diferentes partes de una compilación en múltiples entornos diferentes, simultáneamente. Al separar el entorno de compilación del entorno de ejecución final, puedes reducir significativamente el tamaño de la imagen y la vulnerabilidad de ataque. Esto es especialmente beneficioso para aplicaciones con grandes dependencias de compilación.

Se recomiendan compilaciones de varias etapas para todo tipo de aplicaciones. Para lenguajes interpretados, como JavaScript, Ruby o Python, puedes compilar y minimizar tu código en una sola etapa y copiar los archivos listos para producción a una imagen de tiempo de ejecución más pequeña. Esto optimiza tu imagen para la implementación.
Para lenguajes compilados, como C, Go o Rust, las compilaciones multietapa permiten compilar en una sola etapa y copiar los binarios compilados en una imagen de ejecución final. No es necesario incluir todo el compilador en la imagen final.(Compilaciones Multietapa | Documentación de Docker, n.d.)

<img src="./back/multi.jpeg" alt="contenedor react docker" width="500"/>

## 4. Conocimientos previos

El estudiante debe conocer:
- Fundamentos de Spring Boot.
- Comandos básicos de Docker.
- Lectura y escritura de archivos `Dockerfile`.
- Uso de entornos .env para variables de configuración.
- Fundamentos de React.
- Comunicación entre contenedores en Docker.
- Conceptos básicos de redes en Docker Compose.


## 5. Objetivos a alcanzar

- Contenerizar la aplicación frontend mediante un Dockerfile.
- Contenerizar la aplicación backend mediante un Dockerfile.
- Crear un docker-compose
- Gestionar variables de entorno mediante archivo .env.
- Verificar que el frontend consuma correctamente la API del backend.
- Validar la conexión y migración automática de la base de datos.


## 6. Equipo necesario

- Computador.
- Navegador web.
- Conexión a internet.

## 7. Material de apoyo

- Documentación oficial de Docker.
- Cheatsheet de comandos Docker.
- Videos tutoriales.
- Guía de asignatura.

## 8. Procedimiento

### Pasos 

1. Crear el Dockerfile para el backend.

Figura 8-1 Creacion del Dockerfile en spring boot.

<img src="./back/c1.PNG" alt="contenedor react docker" width="500"/>

2.  Crear el Dockerfile para el frontend.

Figura 8-2 Creacion del Dockerfile en React.

<img src="./back/c2.PNG" alt="contenedor react docker" width="500"/>

3.Crear el archivo .env.

Figura 8-3 Creacion del archivo .env para variables de entorno .

<img src="./back/c3.PNG" alt="contenedor react docker" width="500"/>

4. Crear el archivo docker-compose.yml para orquestar los contenedores.

Figura 8-4 Estructura de docker-compose.

<img src="./back/c4.PNG" alt="contenedor react docker" width="500"/>

5. Ejecutar los contenedores 
Figura 8-5 Ejecucion de los contenedores.

<img src="./back/c5.PNG" alt="contenedor react docker" width="500"/>


## 9. Resultados esperados

Al finalizar la práctica, se cumplió exitosamente con todos los objetivos propuestos. La aplicación backend fue contenerizada correctamente utilizando un Dockerfile con multi-stage build. Se creó una imagen liviana y optimizada que fue ejecutada mediante docker-compose, junto con una base de datos PostgreSQL y la herramienta de administración pgAdmin. Durante el proceso se verificó:
- La conexión entre la aplicación y la base de datos PostgreSQL mediante logs de Spring Boot.
- La ejecución automática de migraciones con Flyway.
- La exposición de puertos y correcta ejecución en segundo plano.
- La conexión a la base de datos desde pgAdmin, confirmando la persistencia y la comunicación en red entre los servicios.
Todo el proceso fue acompañado de capturas que evidencian los pasos seguidos, desde la clonación del repositorio hasta la verificación de la aplicación corriendo dentro del contenedor.

<img src="./back/resultado.PNG" alt="contenedor react docker" width="500"/>


## 10. Bibliografía
- Compilaciones multietapa | Documentación de Docker. (n.d.). Retrieved May 30, 2025, from https://docs.docker.com/get-started/docker-concepts/building-images/multi-stage-builds/
- ¿Qué es el Dockerfile? - IONOS. (n.d.). Retrieved May 16, 2025, from https://www.ionos.com/es-us/digitalguide/servidores/know-how/dockerfile/

