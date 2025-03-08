# Práctica 6
## Ejemplo 1: Construcción de imágenes con una página estática
### Versión 1: Desde una imagen base
Creamos el archivo Dockerfile:

![image](https://github.com/user-attachments/assets/153e55bf-480c-4175-89da-3b04958657ff)

Además de una carpeta con el archivo de nuestra página web dentro

![image](https://github.com/user-attachments/assets/3750761b-13d5-4cd1-8343-405751f4be91)

Ejecutamos el comando para crear la imagen

![image](https://github.com/user-attachments/assets/1768e09b-6b22-4b1a-82fb-6433e15c73b1)

Si consultamos las imagenes, veremos la que acabamos de crear

![image](https://github.com/user-attachments/assets/fb090312-dd44-484a-9ba8-c139d1e39e83)

Creamos un contenedor

![image](https://github.com/user-attachments/assets/ddb1f0be-793c-4314-8d4f-f67bc1cf612a)

Si accedemos a la web veremos nuestra página

![image](https://github.com/user-attachments/assets/3fa2a142-0d01-4cd7-b453-aa14f450be29)


### Versión 2: Desde una imagen con apache2
Comenzamos creando el fichero Dockerfile, esta vez con este contenido:

![image](https://github.com/user-attachments/assets/b56b4b78-dea5-47fa-a4ca-4d44b4e8d332)

Creamos la imagen y el contenedor

![image](https://github.com/user-attachments/assets/fca120dd-52df-42ff-b1c0-50962cc8afc7)

![image](https://github.com/user-attachments/assets/7ba2ad86-608b-4467-935f-23677c7cc959)

### Versión 3: Desde una imagen con nginx
Creamos el archivo Dockerfile que tendrá este contenido

![image](https://github.com/user-attachments/assets/aa4f82bc-177e-4fe6-8161-3403c5d97d7d)

Continuamos creando la imagen y el contenedor

![image](https://github.com/user-attachments/assets/57aef005-d4c7-4804-8160-02019ba90597)

![image](https://github.com/user-attachments/assets/274e0d4d-86f6-46a9-87af-76aa31d1e5eb)


## Ejemplo 2: Construcción de imágenes con una una aplicación PHP
### Versión 1: Desde una imagen base
Creamos el archivo Dockerfile y una carpeta llamada app. En el archivo Dockerfile escribimos lo siguiente

![image](https://github.com/user-attachments/assets/64cb324c-877b-4069-bd94-4a36d2265791)

Dentro de la carpeta app creamos nuestro index.html

![image](https://github.com/user-attachments/assets/837b4d18-4519-4e33-a438-2f142ad2ccc4)

Creamos la imagen

![image](https://github.com/user-attachments/assets/457018ac-68be-456f-8bc5-75d9829d7353)

Vemos que la imagen está creada

![image](https://github.com/user-attachments/assets/99b73ee8-6aeb-4679-b52e-0a4be1f90a26)

Podemos crear un contenedor

![image](https://github.com/user-attachments/assets/6efd0e41-22c5-4185-a8da-dc70d5b6b77a)

![image](https://github.com/user-attachments/assets/a46cd4da-b3ea-499e-9f49-f75c66a28243)

Además, para nuestro archivo con phpinfo creamos un archivo dentro de app

![image](https://github.com/user-attachments/assets/10f04536-1642-49a2-91e4-e194d232bb82)

Ejecutamos de nuevo el contenedor 

![image](https://github.com/user-attachments/assets/7596cd25-77a8-4afa-99f6-ef8bdc3726b3)


### Versión 2: Desde una imagen con PHP instalado
Comenzamos de nuevo creando el archivo Dockerfile, esta vez con este contenido

![image](https://github.com/user-attachments/assets/2a990b14-3577-40c4-ad64-485e031070a9)

Directamente ejecutamos la creación de la imagen y del contenedor

![image](https://github.com/user-attachments/assets/2d22eb41-2923-4312-b86d-aae2f1098415)

![image](https://github.com/user-attachments/assets/3579c9f3-858d-4d94-92ea-7a6037ca63a5)

Accedemos de nuevo

![image](https://github.com/user-attachments/assets/141bf4db-489a-45c2-8d51-6585c80ce3a3)

Como podemos ver, la versión de php ha cambiado debido al cambio de método de instalación


## Ejemplo 3: Construcción de imágenes con una una aplicación Python
### Versión 1
Descargamos los archivos del recurso que proporciona el ejercicio

![image](https://github.com/user-attachments/assets/52716a3d-9481-4e66-97d3-12dadc88273b)

Creamos la imagen

![image](https://github.com/user-attachments/assets/92a368f3-6fad-4141-b180-c6448799ddc2)

Seguimos creando el contenedor

![image](https://github.com/user-attachments/assets/a78b16d2-de70-44fb-a1fc-28868a0a7db6)

Y accedemos a la web

![image](https://github.com/user-attachments/assets/8f429410-df03-4455-a9d4-968b8f86a769)


### Versión 2: Desde una imagen con python instalado
Con la misma estructura de carpetas, cambiamos el contenido del archivo Dockerfile al siguiente

![image](https://github.com/user-attachments/assets/f0f91d42-ba32-4232-bae3-e867fb36ab9b)

Creamos la imagen y el contenedor

![image](https://github.com/user-attachments/assets/a768ffc4-ddd2-4f17-a15d-2542ee1fb165)

![image](https://github.com/user-attachments/assets/128ba33d-8055-41bd-96b8-9c07c2656c13)

De nuevo, obtendríamos la misma página

![image](https://github.com/user-attachments/assets/8aa56b7a-bdf6-41fc-a29a-2f378212418d)




