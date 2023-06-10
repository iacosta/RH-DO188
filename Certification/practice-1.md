### Ejercicio - 1 

##### Objetivo
 - Implementar imagenes usando Podman - Practica usando parametros FROM , ADD, COPY , RUN , ENV , CMD y ENTRYPOINT Instructions.

Crea un contenedor de servidor web simple siguiendo los siguientes pasos:

1. Crea un nuevo directorio para tu proyecto.
2. En el nuevo directorio, crea un archivo llamado **Containerfile**.
3. En el Dockerfile, añade las siguientes líneas:

```bash 
FROM nginx:latest 
ENV TZ=America/Los_Angeles
CMD ["nginx", "-g", "daemon off;"]
```

4. Construya una imagen con el siguiente nombre **my-web-server**
5. Ejecute la imagen del contendor my-web-server usando el puerto 8081 del host y el puerto 80 del contenedor. Cree el nuevo contenedor con el nombre **mi-web**
6. Leea el archivo index.html del contenedor my-web-server
7. Genere un backup del archivo index.html del contenedor en el directorio del proyecto en su host
8. Creer un archivo index.html en su host y llevelo al contenedor. El archivo index.html debe tener el siguiente texto

```bash 
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Mi página web</title>
</head>
<body>
  <header>
    <h1>Bienvenido a mi página web</h1>
  </header>

  <nav>
    <ul>
      <li><a href="#">Inicio</a></li>
      <li><a href="#">Acerca de</a></li>
      <li><a href="#">Contacto</a></li>
    </ul>
  </nav>

  <main>
    <section>
      <h2>Acerca de</h2>
      <p>Esta es una página de ejemplo.</p>
    </section>

    <section>
      <h2>Contacto</h2>
      <p>Puedes contactarme a través de correo electrónico o redes sociales.</p>
    </section>
  </main>

  <footer>
    <p>Derechos de autor &copy; 2023. Todos los derechos reservados.</p>
  </footer>
</body>
</html>
```

9. Reinicie el servicio del nginx en el contenedor my-web-server

10. Verifique que funcionamiento del index.html por Navegador y por consola
