### Respuesta a cada Punto

#### 1.  Ejercicio básico

```sh
#Se ejecuta contenedor basado en la imagen "nginx" y nómbralo "webserver".
❯ podman run -d --name webserver -p 8080:80 nginx
c865ecd4af96b2430bd27857c52e856eb26792feb395416bc8c57cd247618b80

#Se verifica que el contenedor esté en ejecución y que el puerto se haya vinculado correctamente.
❯ curl -v localhost:8080/index.html
*   Trying 127.0.0.1:8080...
* Connected to localhost (127.0.0.1) port 8080 (#0)
> GET /index.html HTTP/1.1
> Host: localhost:8080
> User-Agent: curl/7.88.1
> Accept: */*
> 
< HTTP/1.1 200 OK
< Server: nginx/1.25.0
< Date: Thu, 08 Jun 2023 11:17:50 GMT
< Content-Type: text/html
< Content-Length: 615
< Last-Modified: Tue, 23 May 2023 15:08:20 GMT
< Connection: keep-alive
< ETag: "646cd6e4-267"
< Accept-Ranges: bytes
< 
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
* Connection #0 to host localhost left intact
```

#### 2.  Ejercicio de gestión de contenedores

```sh
#Se crea una imagen de contenedor basado en la imagen "mysql" y nómbralo "database".
❯ cat > Containerfile <<EOF
FROM mysql:latest
ENV MYSQL_ROOT_PASSWORD='password'
VOLUME /tmp/data
EOF

#Se construye la imagen y se ejecuta un contenedor basado en la imagen creada.
❯ podman build -t database .
STEP 1/3: FROM mysql:latest
Resolving "mysql" using unqualified-search registries (/etc/containers/registries.conf.d/999-podman-machine.conf)
Trying to pull docker.io/library/mysql:latest...
Getting image source signatures
Copying blob sha256:3e0c3751e6482e67b70ffad144b2cb9aec9be672df2642a322e875e51b748aeb
Copying blob sha256:de90cd4c0e5df7a54d89ca2140cf329f530b89fe8c79de8873c66cfada8f5de6
Copying blob sha256:7914193c6f0e6bf32545a75c783e4f919ef1fd267a806876c5d2f72da6c4be54
Copying blob sha256:fe4b3f820487ae4bd2869d410c4e4dc497042a73306e0ba99071b261e33190c1
Copying blob sha256:63683b304e3d24e14589c48906cad17ead6bdf22ecf67b6291c12f5bc1544ec3
Copying blob sha256:6ad9069836bd68adbe6be6e2c3aab749575e961266cd5ca27831330c21bb80d7
Copying blob sha256:892e565e2cf01a43d9d6d4b4053893b1b1ea7c36b5b77965eabe762292eb491b
Copying blob sha256:73057d123da0d3d34811ea0383a736c549907f639c24ab1bf576813c3ad40ba8
Copying blob sha256:af1a3c0ec34ee20aec3f319f1f72ab7e94a9171b755be01adc71c30b19406ecb
Copying blob sha256:62fe8dc4ffe938cf78e257d45b0831df9a5053470ebed1d6978a85d061cb6dad
Copying blob sha256:8807488ae889657196a0f63400133a21d65d2ed24ecb1a05faed222acdbeac0d
Copying config sha256:c71276df4a871c5c09ff8411247609cc9683d85290f9dc9b1871dd6e366a28f7
Writing manifest to image destination
Storing signatures
STEP 2/3: ENV MYSQL_ROOT_PASSWORD='password'
--> edee1e4d3a0d
STEP 3/3: VOLUME /tmp/data
COMMIT database
--> f73ee21f4868
Successfully tagged localhost/database:latest
f73ee21f4868bd83362ddd64bf4f367c82612fbc6fe8c25635e5cccc3f76a7c6

#Se verifica que el contenedor esté en ejecución usando comando mysql
❯ podman exec database mysql -u root password 'password'
mysql  Ver 8.0.33 for Linux on x86_64 (MySQL Community Server - GPL)
Copyright (c) 2000, 2023, Oracle and/or its affiliates.
```

#### 3. Ejercicio de gestión de Red

```sh
#Se crea una red llamada "lamerared" y se ejecutan dos contenedores en ella.
❯ podman network create lamerared
lamerared

#Se crea contenedores y se unen a la red.
❯ podman run -d --name frontend --network lamerared httpd
ca732fe2447fe44380ada6da937ee9029b814f32a9f97a58b4f6aba9ef5dabdc
❯ podman run -d --name backend --network lamerared httpd
84beb9ccdeb146b430a51e04f0d11426ed985e39216efb6bb06bd04d3ce898c9

# Se verifica que los contenedores estén en ejecución y se verifica que estén en la red.
❯ podman inspect backend | grep NetworkID
                         "NetworkID": "lamerared",
❯ podman inspect frontend | grep NetworkID
                         "NetworkID": "lamerared",
```

#### 4. Ejercicio de construcción de imágenes

```sh
#Se crea Containerfile con el siguiente contenido
❯ cat > Containerfile <<EOF
FROM alpine:latest
COPY index.html /app
EXPOSE 8080
CMD ["./app"]
EOF

#Se construye la imagen y se ejecuta un contenedor basado en la imagen creada.
❯ podman build -t my-app .
STEP 1/4: FROM alpine:latest
Resolved "alpine" as an alias (/etc/containers/registries.conf.d/000-shortnames.conf)
Trying to pull docker.io/library/alpine:latest...
Getting image source signatures
Copying blob sha256:31e352740f534f9ad170f75378a84fe453d6156e40700b882d737a8f4a6988a3
Copying config sha256:c1aabb73d2339c5ebaa3681de2e9d9c18d57485045a4e311d9f8004bec208d67
Writing manifest to image destination
Storing signatures
STEP 2/4: COPY index.html /app
--> 10d2f4dff1b3
STEP 3/4: EXPOSE 8080
--> abae28c43a33
STEP 4/4: CMD ["./app"]
COMMIT my-app
--> f96a3e2448bd
Successfully tagged localhost/my-app:latest
f96a3e2448bd9a5722fab9c82f88ca7f2fd2f577ea54b53444161998dae4edca

#Se verifica la imagen creada
❯ podman image ls
REPOSITORY                TAG         IMAGE ID      CREATED         SIZE
localhost/my-app          latest      f96a3e2448bd  17 seconds ago  7.63 MB