# Práctica 5

## Ejemplo 1: Configuración básica de Docker Compose con Nginx y MySQL
Creamos un directorio para este proyecto y creamos un archivo llamado docker-compose.yml
```bash
mkdir proyecto_nginx_mysql
cd proyecto_nginx_mysql
nano docker-compose.yml
```
Dentro del archivo escribimos lo siguiente:

![image](https://github.com/user-attachments/assets/cacaf35c-362c-4180-be18-c0521edb03b3)

Guardamos y salimos
Iniciamos los servicios de docker

![image](https://github.com/user-attachments/assets/85f08d44-e81e-4474-9ad1-b20f0af08e05)

Con este comando podemos ver que los contendores están en ejecución

![image](https://github.com/user-attachments/assets/af31140d-7dd5-4873-8aec-396d9f7a6a91)

Si accedemos a http://localhost:8080/ podremos ver que Nginx está funcionando

![image](https://github.com/user-attachments/assets/5d85194e-be7b-4d8f-9422-7d8a31125910)


## Ejemplo 2: Añadir una aplicación PHP al stack con Nginx y MySQL
En la misma carpeta en la que estamos, creamos una carpeta nueva para php y un archivo index.php dentro
```bash
mkdir app
cd app
nano index.php
```
Escribimos lo siguiente dentro del archivo

![image](https://github.com/user-attachments/assets/92788e59-35a4-433f-82ae-9bedb08dfb29)

Modificamos el archivo docker-compose.yml para añadir el php
```bash
nano ../docker-compose.yml
```

![image](https://github.com/user-attachments/assets/c68d583f-75ca-4624-87dc-078ed0458c18)

Reiniciamos los servicios de docker y accedemos de nuevo a la página, veremos los cambios

![image](https://github.com/user-attachments/assets/62113774-eaa8-47d4-9d46-50902b88d2ea)



