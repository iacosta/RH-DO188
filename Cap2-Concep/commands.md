### Comandos Básicos

<details><summary> 
Vefiricar la versión
</summary>

```bash
$ podman --version 
podman version 4.3.1
```
</details>

<details><summary> 
Obtener imagenes de contenedores de registros de imágenes
</summary>

```bash
$podman pull alpine
Resolved "alpine" as an alias (/etc/containers/registries.conf.d/000-shortnames.conf)
Trying to pull docker.io/library/alpine:latest...
Getting image source signatures
Copying blob sha256:c158987b05517b6f2c5913f3acef1f2182a32345a304fe357e3ace5fadcad715
Copying config sha256:49176f190c7e9cdb51ac85ab6c6d5e4512352218190cd69b08e6fd803ffbf3da
Writing manifest to image destination
Storing signatures
49176f190c7e9cdb51ac85ab6c6d5e4512352218190cd69b08e6fd803ffbf3da
```
</details>

<details><summary> 
Listar imagenes
</summary>

```bash
$podman images #variantes --all
REPOSITORY                        TAG                  IMAGE ID      CREATED      SIZE
localhost/podman-pause            4.3.1-1668178887     7c7c1b5040d2  7 days ago   1.09 MB
localhost/prueba                  latest               3583f7a8a752  7 days ago   7.34 MB
docker.io/library/mysql           5.7                  d410f4167eea  4 weeks ago  511 MB
docker.io/library/alpine          latest               49176f190c7e  6 weeks ago  7.34 MB
docker.io/library/wordpress       5.4.2-php7.2-apache  d3bd49a68bba  2 years ago  551 MB
gcr.io/google-samples/node-hello  1.0                  4c7ea8709739  6 years ago  665 MB
```
</details>

<details><summary> 
Ejecución y visualización de contenedores
</summary>

```bash
$podman run -it alpine echo 'Esta es una imagen de Linux Alpine'
Esta es una imagen de Linux Alpine
```
</details>

<details><summary> 
Contenedores en ejecución
</summary>

```bash
$podman ps #variante --all
CONTAINER ID  IMAGE                            COMMAND     CREATED         STATUS             PORTS       NAMES
a02c43c86fbc  docker.io/library/alpine:latest  sh          30 seconds ago  Up 30 seconds ago              beautiful_saha
```
</details>

<details><summary> 
Eliminar contenedores
</summary>

```bash
$podman rm a02c43c86fbc
Error: cannot remove container a02c43c86fbc26b1ee700718953244d850b5c86204d78a5e0e136c0800b33153 as it is running - running or paused containers cannot be removed without force: container state improper
$podman rm a02c43c86fbc --force
a02c43c86fbc
```
</summary>

<details><summary> 
Nombrar contenedores con identificadores
</summary>

```bash
$podman run --name iacostac -it alpine sh
$podman ps
CONTAINER ID  IMAGE                            COMMAND     CREATED         STATUS             PORTS       NAMES
9c4652c38a7e  docker.io/library/alpine:latest  sh          11 seconds ago  Up 11 seconds ago              iacostac
```
</summary>

<details><summary> 
Ver contenedor en formato JSON
</summary>

```json
$podman ps --format=json
[
  {
    "AutoRemove": false,
    "Command": [
      "sh"
    ],
    "CreatedAt": "5 minutes ago",
    "Exited": false,
    "ExitedAt": -62135596800,
    "ExitCode": 0,
    "Id": "9c4652c38a7ef81b605b70b9dcba2770ba2ef7d5746a9f01396e5c5418fd8b1e",
    "Image": "docker.io/library/alpine:latest",
    "ImageID": "49176f190c7e9cdb51ac85ab6c6d5e4512352218190cd69b08e6fd803ffbf3da",
    "IsInfra": false,
    "Labels": null,
    "Mounts": [],
    "Names": [
      "iacostac"
    ],
    "Namespaces": {
      
    },
    "Networks": [
      "podman"
    ],
    "Pid": 1955,
    "Pod": "",
    "PodName": "",
    "Ports": null,
    "Size": null,
    "StartedAt": 1673032952,
    "State": "running",
    "Status": "Up 5 minutes ago",
    "Created": 1673032952
  }
]
```
</summary>