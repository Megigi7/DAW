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

![image](https://github.com/user-attachments/assets/9bf41541-35b9-4bc0-9072-7a82158aa071)

Como podmeos ver, nos aparece nuestra página guestbook y es funcional


## Ejemplo 2: Despliegue de la aplicación Temperaturas
Comenzamos creando una red para esta aplicación

![image](https://github.com/user-attachments/assets/a2a75a21-2a39-4958-aed0-a6afb939c93d)

Creammos un archivo llamado server.js con el siguiente contenido

![image](https://github.com/user-attachments/assets/048969f9-2e00-4892-bdf9-dd3816c7f5b5)

También crearemos un archivo package.json para las dependencias

![image](https://github.com/user-attachments/assets/3e7f8849-d631-44bf-9d59-1c6c2b7c6f53)

Por último, creamos el archivo Dockerfile y escribimos lo siguiente

![image](https://github.com/user-attachments/assets/2ac7deb1-fd5e-4941-adb5-f065a77da19e)

Construimos la imagen del backend con este comando:

![image](https://github.com/user-attachments/assets/fc581449-94a5-436f-8b27-ae968f048e0e)

Ejecutamos el backend en la red creada anteriormente

![image](https://github.com/user-attachments/assets/f765e40b-cc7b-4e91-ad08-3e80d975906c)

Pasamos a crear el frontend, empezamos creando una carpeta
```bash
mkdir frontend && cd frontend
```
Y dentro creamos el archivo app.py con el contenido necesario

![image](https://github.com/user-attachments/assets/8932d10e-e961-463d-b555-e1090f25e18d)

Además, creamos el archivo requirements.txt

![image](https://github.com/user-attachments/assets/7796ab22-ff1c-4cef-a45a-1d15df7806f4)

Por último, creamos otro archivo Dockerfile, esta vez en la carpeta frontend

![image](https://github.com/user-attachments/assets/828ba327-ecc3-4afe-9c26-96cc390ff18b)

Para construir la imagen del frontend usamos el siguiente comando

![image](https://github.com/user-attachments/assets/b1a2a8bd-97bd-447f-81bc-f402a0d37029)

Finalmente, ejecutamos el contenedor del frontend en nuestra red

![image](https://github.com/user-attachments/assets/009898e5-f1c1-4198-831a-1498a71d0ecc)

Accedemos a localhost:8080 para comprobar el funcionamiento

![image](https://github.com/user-attachments/assets/cdadade6-0281-4620-a4ef-840e4e22ed8f)

Hemos probado también su funcionamiento y todo funciona correctamente


## Ejemplo 3: Despliegue de Wordpress + mariadb
Creamos una nueva carpeta para este ejercicio
```bash
mkdir wordpress && cd wordpress
```
Dentro creamos el archivo docker-compose.yml que usaremos para este ejercicio

![image](https://github.com/user-attachments/assets/add87392-1785-47c3-b8f1-8ee578915124)

En este archivo hemos configurado la base de datos con mysql, wordpress y la red que usarán
Para hacerlo funcionar ejecutamos este comando

![image](https://github.com/user-attachments/assets/f2732dc4-1660-4a8d-a2e3-483bdfd219b7)

Si accedemos a la dirección localhost:8080 nos redirige a la instalación de wordpress

![image](https://github.com/user-attachments/assets/5d100c0e-b7f1-45c3-a5b7-454e414400d6)

Completamos la instalación de wordpress introduciendo los datos necesarios

![image](https://github.com/user-attachments/assets/a5c34aab-1a2a-4488-bd02-4fee46bd12eb)

Si vemos los contenedores activos de docker veremos que hay dos que pertenecen a wordpress

![image](https://github.com/user-attachments/assets/080be0ed-a773-42f7-b325-b009b05839c0)
