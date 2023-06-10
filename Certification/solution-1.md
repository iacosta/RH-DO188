

1. Crear Directorio y archivos

```bash
mkdir my-web-server && cd my-web-server
```

```bash
cat > Containerfile <<EOF
FROM nginx:latest 
ENV TZ=America/Los_Angeles
CMD ["nginx", "-g", "daemon off;"]
EOF
```
2. Construir imagen
```bash
❯ podman build -t mi-web-server .

STEP 1/3: FROM nginx:latest
Resolving "nginx" using unqualified-search registries (/etc/containers/registries.conf.d/999-podman-machine.conf)
Trying to pull docker.io/library/nginx:latest...
Getting image source signatures
Copying blob sha256:831f51541d386c6d0d86f6799fcfabb48e91e9e5aea63c726240dd699179f495
Copying blob sha256:f03b40093957615593f2ed142961afb6b540507e0b47e3f7626ba5e02efbbbf1
Copying blob sha256:eed12bbd64949353649476b59d486ab4c5b84fc5ed2b2dc96384b0b892b6bf7e
Copying blob sha256:fa7eb8c8eee8792b8db1c0043092b817376f096e3cc8feeea623c6e00211dad1
Copying blob sha256:7ff3b2b12318a41d4b238b643d7fcf1fe6da400ca3e02aa61766348f90455354
Copying blob sha256:0f67c7de5f2c7e0dc408ce685285419c1295f24b7a01d554517c7a72374d4aeb
Copying config sha256:f9c14fe76d502861ba0939bc3189e642c02e257f06f4c0214b1f8ca329326cda
Writing manifest to image destination
Storing signatures
STEP 2/3: ENV TZ=America/Los_Angeles
--> 35698262c045
STEP 3/3: CMD ["nginx", "-g", "daemon off;"]
COMMIT mi-web-server
--> a622b5f3a217
Successfully tagged localhost/mi-web-server:latest
a622b5f3a217fa3f48959c8cf9c85ad02200189f3c6c1a77e526b5c18107faa9
❯ podman image ls
REPOSITORY               TAG         IMAGE ID      CREATED         SIZE
localhost/mi-web-server  latest      a622b5f3a217  43 minutes ago  147 MB
docker.io/library/nginx  latest      f9c14fe76d50  12 days ago     147 MB
```

3. Leer el archivo index.html del contenedor my-web-server

```bash
❯ podman exec mi-web cat /usr/share/nginx/html/index.html

<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```

4. Backup del index.html del contenedor a la maquina local

```bash
❯ podman cp mi-web:/usr/share/nginx/html/index.html /Users/iacosta/my-web-server/index.html_backup

❯ ll
total 24
drwxr-xr-x  5 iacosta  staff   160B Jun  6 15:08 .
drwxr-xr-x@ 6 iacosta  staff   192B May 22 11:50 ..
-rw-r--r--  1 iacosta  staff    83B May 22 11:53 Containerfile
-rw-r--r--  1 iacosta  staff   784B May 22 12:22 index.html
-rw-r--r--  1 iacosta  staff   615B May 23 10:08 index.html_backup
````

5. Copiar el archivo index.html del host al contenedor y reiniciar el servicio nginx

```bash
❯ podman cp index.html mi-web:/usr/share/nginx/html/index.html

❯ podman exec mi-web nginx -s reload
2023/06/06 12:55:31 [notice] 26#26: signal process started

❯ curl -v localhost:8081/index.html
*   Trying 127.0.0.1:8081...
* Connected to localhost (127.0.0.1) port 8081 (#0)
> GET /index.html HTTP/1.1
> Host: localhost:8081
> User-Agent: curl/7.88.1
> Accept: */*
>
< HTTP/1.1 200 OK
< Server: nginx/1.25.0
< Date: Tue, 06 Jun 2023 19:59:42 GMT
< Content-Type: text/html
< Content-Length: 784
< Last-Modified: Mon, 22 May 2023 17:22:12 GMT
< Connection: keep-alive
< ETag: "646ba4c4-310"
< Accept-Ranges: bytes
<
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