
### Retos Nivel Supermo
Una serie de ejercicios por hacer.

##### Ejercicio No.1 

1. Primero, crea un archivo HTML en tu host. Por ejemplo, puedes crear un archivo llamado "index.html" con el siguiente contenido:
```bash
echo "<!DOCTYPE html>
<html>
<head>
	<title>Mi sitio web</title>
</head>
<body>
	<h1>Bienvenido a mi sitio web!</h1>
	<p>Este es un ejemplo de página web.</p>
</body>
</html>
```
2. Luego, crea un directorio para almacenar los archivos necesarios.
3. Crear un Containerfile usando una imagen de Ngix y copia el archivo index.html a /usr/share/nginx/html/
4. Despliega el contenedor y reinicia el servicio del NGINX
5. Utiliza los puertos 8080 con el 80 del contenedor 
6. ¡Y eso es todo! Ahora puedes abrir un navegador web y acceder a tu sitio web en la dirección http://localhost:8080

##### Ejercicio No.2

1. Crea una red virtual privada "lamerared" para que las tres máquinas puedan comunicarse entre sí de forma segura.

2. Crea un contenedor de MySQL y colócalo en la red virtual privada. Configura el contenedor para que use una base de datos específica y cree un usuario y una contraseña para esa base de datos.

3. Crea un contenedor de Node.js y colócalo en la red virtual privada. Configura el contenedor para que se conecte a la base de datos y proporcione una API REST para acceder a los datos de la base de datos.

4. Crea un contenedor de React y colócalo en la red virtual privada. Configura el contenedor para que se conecte al backend y proporcione una interfaz de usuario para acceder a los datos de la base de datos.

Con estos pasos, tendrás tres máquinas interactuando entre sí: una base de datos, un backend y un frontend. La red virtual privada garantizará una comunicación segura entre los contenedores.

##### Ejercicio No.3

1. Crea un contenedor a partir de la imagen "nginx" y mapea el puerto 80 del contenedor al puerto 8080 del host. Verifica que puedas acceder al servidor web nginx en tu navegador web en la dirección http://localhost:8080.

2. Crea una imagen a partir de un contenedor que tenga una aplicación web personalizada. Asegúrate de que la imagen incluya todos los archivos necesarios para ejecutar la aplicación. Luego, ejecuta un contenedor a partir de la imagen y mapea el puerto 8080 del host al puerto 80 del contenedor. Verifica que puedas acceder a la aplicación en tu navegador web en la dirección http://localhost:8080.

3. Almacenamiento persistente. Crea un contenedor a partir de la imagen "mysql" y mapea el puerto 3306 del contenedor al puerto 3306 del host. Asegúrate de que los datos de la base de datos se almacenen en un volumen persistente para que los datos no se pierdan cuando el contenedor se detenga o se elimine.

4. Crea una red personalizada para que varios contenedores puedan comunicarse entre sí sin exponer sus puertos en el host. Luego, crea dos contenedores a partir de la imagen "nginx" y colócalos en la misma red. Asegúrate de que los contenedores puedan comunicarse entre sí a través de la red personalizada.


##### Ejercicio No.4 
1. Crea dos contenedores con una imagen de Apache.
2. Inicializa un cluster de contenedores usando Podman.
3. Agrega los dos contenedores de Apache al cluster.
4. Verifica que ambos contenedores estén en el cluster.
5. Accede a uno de los contenedores y verifica que se pueda acceder a la página web de Apache.

##### Ejercicio No.5
1. Crea dos contenedores con una imagen de NGINX.
2. Cada contenedor debe exponer el puerto 80.
3. Intenta correr ambos contenedores en el mismo host.
4. Observa que falla el intento.
5. Agrega los dos contenedores a un Podman Pod.
6. Verifica que ambos contenedores estén corriendo sin problemas.

##### Ejercicio No.6
1. Crea un contenedor con una imagen de Alpine.
2. Usa Podman para copiar un archivo de texto al contenedor.
3. Accede al contenedor y verifica que el archivo se haya copiado exitosamente.
4. Actualiza el archivo dentro del contenedor usando Podman.
5. Accede al contenedor de nuevo y verifica que el archivo haya sido actualizado correctamente.

##### Ejercicio No.7
1. Crea un contenedor con una imagen de PostgreSQL.
2. Intenta conectarte a la base de datos desde el host.
3. Observa que falla el intento.
4. Agrega el contenedor a un Podman Pod.
5. Intenta conectarte a la base de datos de nuevo.
6. Verifica que la conexión se realiza sin problemas.
7. Si hay problemas, verifica el estado del contenedor y el Pod usando Podman inspect y Podman logs.

##### Ejercicio No.8
1. Crea una imagen personalizada que utilice una imagen de base de alpine. Agrega el comando echo en la instrucción RUN para imprimir "Hello World".
2. Utiliza la instrucción ADD para agregar un archivo de texto llamado 'test.txt' a la imagen.
3. Utiliza la instrucción COPY para copiar un archivo de tu sistema local a la imagen.

##### Ejercicio No.9
1. Inserta una imagen personalizada en un registro privado.
2. Extrae una imagen de un registro y ejecútala localmente con Podman.
3. Realiza un backup de una imagen con todas sus capas y metadatos.

##### Ejercicio No.10
1. Ejecuta un contenedor de manera local con Podman.
2. Obtén los registros de un contenedor en ejecución.
3. Utiliza el comando podman events para estar atento a los eventos de los contenedores en el host.

##### Ejercicio No.11
1. Crea una stack de aplicación que incluya dos contenedores: uno para una base de datos MySQL y otro para una aplicación web que se conecta a la base de datos.
2. Usa variables de entorno para configurar la conexión de la aplicación web con la base de datos.
3. Crea un volumen y usa la opción -v para montar el directorio de hosts en el contenedor de la aplicación.

##### Ejercicio No.12
1. Examinar los registros de una aplicación en funcionamiento para identificar un problema de conexión a la base de datos.
2. Conéctate a un contenedor en ejecución para investigar el estado de la aplicación.
3. Utiliza la opción --describe del comando podman ps para obtener información detallada sobre los recursos de un contenedor en ejecución.


Enjoy it... :D
