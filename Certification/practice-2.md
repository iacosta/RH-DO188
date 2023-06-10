### Ejercicio - 2
#### Objetivo
Ejercicios varios ejercicios de Podman para ejecutar contenedores localmente.

1. Ejercicio básico:
   - Crea un contenedor basado en la imagen "nginx" y nómbralo "webserver".
   - Asigna el puerto 8080 del host al puerto 80 del contenedor.
   - Ejecuta el contenedor en segundo plano.
   - Verifica que el contenedor esté en ejecución y que el puerto se haya vinculado correctamente. 

2. Ejercicio de gestión de contenedores:
   - Crea un contenedor basado en la imagen "mysql" y nómbralo "database".
   - Establece la variable de entorno "MYSQL_ROOT_PASSWORD" con un valor seguro.
   - Asigna un volumen para persistir los datos del contenedor en el host.
   - Ejecuta el contenedor y confirma que está en ejecución.
   - Verifica que el contenedor tenga acceso a los datos persistentes.

3. Ejercicio de red:
   - Crea dos contenedores basados en la imagen "httpd" y nómbralos "frontend" y "backend".
   - Crea una red de tipo bridge para los contenedores.
   - Conecta ambos contenedores a la red creada.
   - Verifica que los contenedores puedan comunicarse entre sí en la misma red.

4. Ejercicio de construcción de imágenes:
   - Crea un archivo Dockerfile en un directorio vacío.
   - Usa una imagen base adecuada y copia tu aplicación dentro del contenedor.
   - Expón un puerto en el contenedor.
   - Construye la imagen utilizando Podman y dale un nombre apropiado.
   - Ejecuta un contenedor basado en la imagen recién creada y verifica que funcione correctamente.

5. Ejercicio de almacenamiento:
   - Crea un contenedor basado en la imagen "registry" de Docker.
   - Monta un volumen en el contenedor para almacenar los datos del registro.
   - Asigna un puerto en el host para acceder al registro.
   - Sube una imagen personalizada al registro utilizando Podman.
   - Verifica que la imagen se haya subido correctamente y esté disponible para su descarga.

Recuerda que estos ejercicios son solo ejemplos y puedes adaptarlos según tus necesidades y conocimientos. ¡Espero que te sean útiles para practicar con Podman!
