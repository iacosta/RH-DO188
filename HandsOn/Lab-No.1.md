
### Laboratorio No.1 

Para la realización de este ejercicio es necesario tener instalado Podman (Local), y tener crear una cuenta en https://quay.io/.

**Importante**
Una vez realizado el ejercicio, no borres el contenedor. Seguramente lo vas a tener que usar en laboratorios posteriores.

##### El reto 

1. Creación de una imagen Ubuntu
2. Renonmbra el TAG de esta imagen con el nombre de appserver:ver1.0
3. Arranca un contenedor desde una imagen base appserver, y define el nombre Working a este contenedor
4. Instala los paquetes nmap y apache.
5. Agregar o crea un archivo llamado index2.html con el siguiente comando
```bash
echo "<h1> My firts Podman Challenge - Checked </h1>" > /var/www/html/index2.html
```
6. Crea una imagen a partir de este contenedor (recuerda que tienes que utilizar el nombre de tu usuario Quay Hub). La imagen se debe llamar <tu_usuario_quay.io>/appserver1.0. Sube la imagen a Quay.

Descarga la imagen y verifica que funciona correctamente. Si consideras necesario y quieres documentar puedes capturar los ScreenShots del proceso.

Enjoy it... :D