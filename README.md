# Tarea: Docker - Trabajando con volúmenes

## Instrucciones

Esta práctica consiste en una serie de tareas que debes seguir utilizando Docker y la imagen de Apache. Crea un repositorio en GitHub para subir este archivo README.md con formato markdown. Realiza un commit cada dos apartados, nombrando el número del apartado.

## Pasos

1. **Descarga de la imagen 'httpd' y verificación**

    ```bash
    docker pull httpd
    docker images
    ```

2. **Creación de un contenedor 'asir_httpd'**

    ```bash
    docker run -d --name asir_httpd -p 8000:80 -v "$PWD"/htdocs:/usr/local/apache2/htdocs/ httpd
    ```

    - Ayuda:
        - Mapea el puerto 80 del contenedor con el puerto 8000 de tu máquina.
        - Utiliza bind mount para montar el directorio 'htdocs' del Apache en un directorio que elijas.
        - Utiliza `-v "$PWD"/htdocs:/usr/local/apache2/htdocs/`
        
    - Realiza un 'Hola Mundo' en HTML y comprueba desde el navegador que se accede correctamente.

3. **Creación de un contenedor 'asir_web1'**

    ```bash
    docker run -d --name asir_web1 -p 8000:80 -v "$PWD"/htdocs:/usr/local/apache2/htdocs/ httpd
    ```

    - Utiliza Visual Studio Code para crear un archivo HTML 'index.html' en el directorio 'htdocs' con el contenido 'Hola Mundo'.

4. **Creación de otro contenedor 'asir_web2'**

    ```bash
    docker run -d --name asir_web2 -p 9080:80 -v "$PWD"/htdocs:/usr/local/apache2/htdocs/ httpd
    ```

    - Verifica que los dos servidores 'sirven' la misma página accediendo desde el navegador a:
        - http://localhost:9080
        - http://localhost:8000
    - Ambos deben mostrar la misma página web con el mensaje 'Hola Mundo'.
