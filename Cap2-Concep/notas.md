## Conceptos básicos de Podman

- Podman es una herramienta de código abierto que puede usar para gestionar sus contenedores localmente.
- Puede buscar, ejecutar, compilar o implementar contenedores e imágenes de contenedores OCI (Open Container Initiative).
- Algunas otras herramientas como Docker usan un demonio para enviar las solicitudes, lo que genera un único punto de falla y seguridad ya que puede requerir privilegios muy elevados

### Trabajar con Podman
Ventajas
- Extracción y visualización de imágenes 
- Contenedor e imágenes del contenedor
    - Una imagen de contenedor contiene una versión empaquetada de su aplicación, con todas las dependencias necesarias para que la aplicación se ejecute.
- Ejecución y visualización de contenedores
- Exposición de contenedores (Puertos entre el Host & el contenedor)
- Uso de variables de entorno 

### Redes sobre Contenedores
- Podman viene con una red llamada **podman**
    - Ejemplo: Los contenedores que ejecutan una aplicación y una DB pueden usar una red Podman separada para aislar su comunicación de otros contenedores. Así mismo la DB puede usar otra red para aislar la comunicación
- Para usar el DNS, cree una nueva red Podman y conecte sus contenedores a esa red.
- Los contenedores pueden conectarse a una o más redes Podman.

### Acceso a servicios de redes contenerizadas
- La red de un contenedor está aislada, lo que significa que solo se puede acceder a una aplicación en red dentro del contenedor. El reenvío de puertos asigna un puerto desde el contenedor al host del contenedor externo.







___

<details><summary> Resumen
</summary>

- Use el comando podman run para iniciar el contenedor.<br>
- Comunicación de un contenedor a otro mediante el uso de redes Podman, que incluyen:<br>
   - Gestión de redes Podman mediante el uso de subcomandos podman network.<br>
   - Conectar un contenedor a una red en la creación del contenedor y mientras se ejecuta.<br>
- Use el reenvío de puertos para exponer un proceso contenerizado al entorno del host.<br>
- Use los comandos podman stop y podman kill para detener un contenedor.<br>
- Use el comando podman ps para mostrar una lista de los contenedores.<br>
- Use el comando podman cp para copiar archivos desde y hacia contenedores.<br>
- Gestione el ciclo de vida de los contenedores mediante el uso de podman start, podman pause, podman restart y otros comandos de Podman.<br>
</details>