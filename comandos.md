# Comandos de PODMAN

Comaandos para instalar Podman y Podman-Desktop en MAC 
<code>
brew install podman
brew install podman-desktop
brew install podman-compose
</code>

Correr un container

<code>$ podman run -it alpine sh</code>

Listamos archivos dentro 

<code># ls
bin    dev    etc    home   lib    media  mnt    opt    proc   root   run    sbin   srv    sys    tmp    usr    var</code>

Instalamos en la versión de Linux Alpine el paquete de Curl

<code># apk add curl
fetch https://dl-cdn.alpinelinux.org/alpine/v3.17/main/x86_64/APKINDEX.tar.gz
fetch https://dl-cdn.alpinelinux.org/alpine/v3.17/community/x86_64/APKINDEX.tar.gz
(1/5) Installing ca-certificates (20220614-r3)
(2/5) Installing brotli-libs (1.0.9-r9)
(3/5) Installing nghttp2-libs (1.51.0-r0)
(4/5) Installing libcurl (7.87.0-r0)
(5/5) Installing curl (7.87.0-r0)
Executing busybox-1.35.0-r29.trigger
Executing ca-certificates-20220614-r3.trigger
OK: 9 MiB in 20 packages </code>

Ahora podemos construir una imagen para Podman

- Usamos vim para crear la imagen 

<code> vim Containerfile</code>

- Agregamos los comandos a la Imagen

<code> 
FROM alpine 
RUN echo "Whatssaaauppp from podman. By Ivan Acosta" </code>

Ejecutamos el comando para construir la imagen apartir del archivo Containerfile

<code> #podman build -t prueba:latest . </code> 
**Nota:** El . significa que va a ejecutar el archivo Containerfile como imagen

Ahora miremos el resultado

<code># podman build -t prueba:latest .
STEP 1/2: FROM alpine
STEP 2/2: RUN echo "Whatssaaauppp from podman. By Ivan Acosta"
Whatssaaauppp from podman. By Ivan Acosta
COMMIT prueba:latest
--> 3583f7a8a75
Successfully tagged localhost/prueba:latest
3583f7a8a75229011c35ca6aabc8710b146fa56d26b04fde205a8793edb5552a
</code>

Miremos ahora el listado de imagenes
<code>#podman images
REPOSITORY                TAG         IMAGE ID      CREATED      SIZE
localhost/prueba          latest      3583f7a8a752  5 days ago   7.34 MB
docker.io/library/alpine  latest      49176f190c7e  6 weeks ago  7.34 MB </code>

Ahora podemos entrar a la maquina con
<code># podman run -it prueba sh
/ # ls
bin    dev    etc    home   lib    media  mnt    opt    proc   root   run    sbin   srv    sys    tmp    usr    var </code>

___
Ahora vamos a crear un POD con dos imagenes. La primera con una capa de aplicación con WordPress y la segunda con una DB de MySQL asociada. 

Vamos a crear el pod primero Llamado **demo_wordpress**
<code>#podman pod create --name demo_wordpress -p 8585:80
b658a848a20f66f45e7fbba86afcd653e4b0867d51adbf0751e7eb1ed79e31b8</code>

Ahora vamos a crear un contenedor de MySQL y lo vamos agregar al pod **demo_wordpress**

<code>#podman run -d --pod demo_wordpress -e WORDPRESS_DB_USER=root -e WORDPRESS_DB_PASSWORD=root -e WORDPRESS_DB_NAME=wordpress -e WORDPRESS_DB_HOST=127.0.0.1 wordpress:5.4.2-php7.2-apache 
Resolving "wordpress" using unqualified-search registries (/etc/containers/registries.conf.d/999-podman-machine.conf)
Trying to pull docker.io/library/wordpress:5.4.2-php7.2-apache...
Getting image source signatures
Copying blob sha256:eb10907c011020c78d6036534f8781b54eaad07aa9812b0efaca32718aa9c2f3
Copying blob sha256:bf59529304463f62efa7179fa1a32718a611528cc4ce9f30c0d1bbc6724ec3fb
Copying blob sha256:a409b57eb4640b0580c61ce49aac67cb9c2f68d4fdcdca238c54b8bc4ca521e7
Copying blob sha256:3192e6c84ad0a910ff9ee4f6e46b570312c08dbb4f3f8e6be396b1219ef1e704
Copying blob sha256:43553740162b7b4a0c825a05b0c55c4d6e23598ff7092b25461cac849012c1ca
Copying blob sha256:d8b8bba42dea97f8e4f55f8b70186c335b12b3c2b25969bf45afc2763c123c80
Copying blob sha256:10568906f34e1e3ff1dfcb6db191d6ceb90826020fa5d6b8ffdaf6644c8f11f0
Copying blob sha256:7a8a58d5365a88abfe2fc3a9042438336aab5a70bc103278c1074506a2b87d8b
Copying blob sha256:0d7d944c357e4b98e7ad0e0ca08c6a5059a9e4168ece2275d9613bb9e05bb34e
Copying blob sha256:c523214ebbcbbdc484b192333a0597ada69fadb9a61f555270a8152f54ce4baa
Copying blob sha256:09a7e2a894fadce027b2ed38fd309c864bff0d1ae85d4155b58ded679097c927
Copying blob sha256:0a5b0b18984247df2fbef7d84c5b5cb78e228adeed465d793de5afc904070fac
Copying blob sha256:5a971be0edbfa6da27a5abed814f0b095050c76fcb3e2aa60d28bccb3d7ca371
Copying blob sha256:41998deb7b343e97dac763136bb2637f458f4437f836908615c1561d47aba5da
Copying blob sha256:e6403ed9b0529ff982dcefeec8217f754938619f9dc30bb6ed971444e05d8490
Copying blob sha256:fc9b6eaf07b4534fef982fa6914056a34cabbce2b1a8bb6b2212f24e8901a508
Copying blob sha256:1ea8b1b2e4a3320c20bc7426c4671ebb56f05dadabb7b5de0f651c17b324d6ca
Copying blob sha256:78ad0612408dbfa4ea01f3a0a05be7a5106c994c7f8118502040802a519c4fb2
Copying blob sha256:7d26adf363965b879bcafbdc80048a01bc5f3befab08b87f5a2bb0e55b8e0742
Copying blob sha256:419d030a840d426b636b6a5fea47697a1c4147b160bef3091339caf052d23c67
Copying blob sha256:3db472489ef43c12977b80fbcce7a07df81b1b61737786da7fd5fd518cd801d0
Copying config sha256:d3bd49a68bba89420fc1759b197eb2dea9c8afcbb6ea1b6a59daecd1d5a0f972
Writing manifest to image destination
Storing signatures
829e6065afacd35090c27830cd31e8aca42390c4d68d4c64e5e0dba704fe3f2e</code>


Ahora vamos descargar la imagen de la aplicación que se conectara al contenedor de MySQL que creamos en el paso anterior
<code>#podman run -d --pod demo_wordpress -e MYSQL_DATABASE=wordpress -e MYSQL_ROOT_PASSWORD=root mysql:5.7 --default-authentication-plugin=mysql_native_password 
Resolving "mysql" using unqualified-search registries (/etc/containers/registries.conf.d/999-podman-machine.conf)
Trying to pull docker.io/library/mysql:5.7...
Getting image source signatures
Copying blob sha256:2e747e5e37d77f3d8331753fc4c4eb0b0e5af8648ee5b2eec8fa274ebdddb475
Copying blob sha256:d26998a7c52d2b84e7927f97651d1d703a805c8e4d3f658a03138721f5a5dd44
Copying blob sha256:4a9d8a3567e30df99576e0a4dbca773af581230fee203891610e6ccbdaa823d2
Copying blob sha256:bfee1f0f349e08af59ed77c7d56ede70f0c5739daa2477ef54a4ee457f5e3e47
Copying blob sha256:71ff8dfb9b12b027c35d779fe4f06a9b3d0d26efed52153324cfa2f409423b0d
Copying blob sha256:bf56cbebc916d35659623816867a456610961f77db6d9753e738c5564651dfa0
Copying blob sha256:711a06e512dab8bc033e74a32300e408fc4d5ab67e6db0f84942d3ddadb7376d
Copying blob sha256:3288d68e4e9e0f5e70378db2d166bf205b73ca677bdf72384be72fa529264ed1
Copying blob sha256:49271f2d6d157b6b14c6d6c165b3b29b8d29aef70edd653702832a48bcecf382
Copying blob sha256:f782f6cac69ce870188610aef114b2852e9f69f2b849a4df90c0209bf8dc1717
Copying blob sha256:701dea355691c2e0ccc548aa219fc1dd83ba44ff81843802aef25e77e813454d
Copying config sha256:d410f4167eea912908b2f9bcc24eff870cb3c131dfb755088b79a4188bfeb40f
Writing manifest to image destination
Storing signatures
2d36758c05fa611709ce263ac2fc8ae58596061f8dc2074cab58c854c06b9056</code>

Ahora para verificar, podemos abrir un navegador en nuestro HOST LOCAL e ingresar al localhost:8585 y ya tenemos acceso a la instalación de Wordpress. 

Tambien podemos vericar los procesos de podman con el siguiente comando
<code> #podman ps
CONTAINER ID  IMAGE                                            COMMAND               CREATED     STATUS         PORTS                 NAMES
34dafc1caf1b  docker.io/library/alpine:latest                  sh                    7 days ago  Up 7 days ago                        sweet_meitner
745deb259a58  localhost/podman-pause:4.3.1-1668178887                                5 days ago  Up 5 days ago  0.0.0.0:8585->80/tcp  b658a848a20f-infra
829e6065afac  docker.io/library/wordpress:5.4.2-php7.2-apache  apache2-foregroun...  5 days ago  Up 5 days ago  0.0.0.0:8585->80/tcp  silly_keller
2d36758c05fa  docker.io/library/mysql:5.7                      --default-authent...  5 days ago  Up 5 days ago  0.0.0.0:8585->80/tcp  loving_gauss </code>

Con el siguiente comando podemos ver la cantidad de pods y los containers asociados al mismo
<code>
#podman pod ls
POD ID        NAME            STATUS      CREATED     INFRA ID      # OF CONTAINERS
b658a848a20f  demo_wordpress  Running     5 days ago  745deb259a58  3
</code>

Podemos crear un manifiesto de K8S de acuerdo a lo que se esta ejecutando en los PODS de Podman. Con este comado podemos hacerlo

<code>
#podman generate kube demo_wordpress > wordpress_full.yaml
</code>

Ahora podemos ver el contenido
<code># vim wordpress_full.yaml
</code>

Tambien podemos tomar un manifiesto de K8S y ejecutarlo en Podman, así
<code># podman play kube pod.yaml
Pod:
87f3a70f6b0235f93762d3a60ec364535c2477f5e52805a17fdf811bab761911
Container:
0e9ebe1dea18e3c316867a63e5fdc5699ec31823ee12817694a5799a83853505
</code>

Para verificar que el contenedor esta funcionando correctamente, podemos verificarlo por medio del comando
<code># curl localhost:8080
Hello Kubernetes!%
</code>

## Link de Interes
[Mapa Mental](https://www.goconqr.com/es/mapamental/31944811/podman)
[Flash Cards - DO180](https://quizlet.com/692889577/do180-studey-set-flash-cards/)
[Cards de Comandos - DO180](https://quizlet.com/717521005/do180-commands-flash-cards/)
[Examen de Practica - DO180](https://acloudguru.com/hands-on-labs/red-hat-ex180-practice-exam)
[Examen de Ejemplo - DO180](https://ziyonotes.uz/ex180-sample)
[Repo GIT](https://github.com/kukudm/D0180)

