### Ejercicio - 3

##### Objetivo
 - Crear imagenes de contenedores de en Podman pasando o definiendo variables durante la construcción de la imagen misma.

Crea un ContainerFile que cree una imagen de contenedor con los siguientes requisitos. 

1. Basado en centos:7.
2. Durante la construcción, crear una cuenta de usuario. "benito" debe ser el usuario por defecto.
3. Lee un argumento durante la construcción para anular el nombre "benito".
4. El contenedor debe ejecutar "whoami" para mostrar el usuario activo.

NOTA: ¡Los argumentos NO se pasan durante el tiempo de ejecución del contenedor! Se pasan durante la construcción del contenedor.

Crea dos imágenes de contenedor usando este containerfile, llamadas benito-came:1.0 y elsa-marcela:1.0.

Cuando se ejecuten, deberían mostrar "benito" y "elsa" respectivamente.