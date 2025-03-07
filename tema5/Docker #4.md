# Práctica 4

## Ejemplo 1: Despliegue de la aplicación Guestbook
Seguiremos este ejemplo 
https://github.com/josedom24/curso_docker_ies/blob/main/modulo3/guestbook.md

Comanzamos la práctica creando una red docker

![image](https://github.com/user-attachments/assets/50e5a7a5-9d36-432d-bbf0-17b79a605aa0)

Usaremos Redis como base de datos, lo ejecutamos en la red creada

![image](https://github.com/user-attachments/assets/8803ffb2-2102-489f-a2d3-ad6254652b4d)

Como yo no tenía una imagen Redis, lo ha descargado automáticamente

Procedemos a crear el frontend en un nuevo directorio, yo lo llamé guestbook. Dentro creamos un archivo llamado app.py
```bash
mkdir guestbook && cd guestbook
nano app.py
```
![image](https://github.com/user-attachments/assets/b33f4335-176e-45f1-af9e-e37601446475)

También creamos un archivo Dockerfile con este contenido

![image](https://github.com/user-attachments/assets/2383ba3b-bb68-4de8-9edf-83dd4d1df3a3)

Por último, un archivo requirements.txt donde escribimos lo siguiente

![image](https://github.com/user-attachments/assets/51d63b3c-c566-479e-81c0-5ebb50efb7c3)

Una vez todos nuestros archivos listos, pasamos a construir la imagen para el frontend

![image](https://github.com/user-attachments/assets/43a8b162-d0c5-4af5-8ae8-529e53f7a6e8)

Finalmente ejecutamos el contenedor

![image](https://github.com/user-attachments/assets/0d2db4cb-b7c3-4a6e-9b4c-07cb177af2c3)

Accedemos a localhost:8080 para comprobar su funcionamiento

