### Laboratorio No.3 

Conceptos claves a tener en cuenta. Container File, Datos Persistentes y manejo de archivos entre el contenedor y host local.

**Los pasos son:**

1. Descargar una imagen de MYSQL del siguiente repositorio docker.io/bitnami/mysql

2. Creamos un contenedor a partir de la imagen descargada. Ejecutar en una sola linea de comando los siguientes parametros.

        -d: Deatached Mode es la forma en que indicamos que corra en background.
        -p : puerto, el contenedor corre en el puerto 3306, pero hacemos un bind para que lo escuchemos en Host el puerto 33061 en el host local.
        –name : mysql-db.
        -e : environment le asignamos la contraseña que sea igual a secret

3. Verificar el estado del Container por medio de los logs generados al momento de crear el contenedor

4. Descarga los archivos sakila-data.sql y sakila-schema.sql

5. Entrar al contenedor usamos un modo interactivo. Allí debes crear una base de datos llamada sakila y subir (importar) los archivos sakila-data.sql y sakila-schema.sql

6. Verificar el estado de la base de datos sakila.

7. Borrar el contenedor y ejecutar de nuevo el paso No.2, verificar que la base de datos de sakila existe. Si no exite, verificar o concluir lo sucedido.

8. Crear volumen llamado mysql-db-data para dejar la base de datos persistente

9. Crear un container file con el resumen de los pasos 2 al 5.

10. Verificar el estado contenedor, la base de datos sakila.

10. Borrar el container, sin borrar el volumen creado.

11. Ejecutar los pasos No.2 y verificar que la base de datos de Sakila se encuentra operando.

12. Definir el TAG para el nuevo contenedor 'my-mysql-db'

13. Finalmente suba esa imagen creada con la base de datos Sakila a tu repositorio previamente en https://quay.io/

Muchos éxitos en el reto. Enjoy it... :D