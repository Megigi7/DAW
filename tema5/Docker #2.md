# Instalación de Docker y Práctica 2
Descargamos docker de su página oficial y ejecutamos el instalador
https://www.docker.com/

## Actividades del primer artículo
Ejecutamos el siguiente comando para crear la imagen.

![image](https://github.com/user-attachments/assets/301355d2-02d0-4c35-81f3-ad6bb90ff311)


Para ver las imagenes podemos ejecutar el siguiente comando o verlo desde la aplicación "Docker Desktop".
![image](https://github.com/user-attachments/assets/f7d8c17f-4950-45de-af11-5967db25b005)
![image](https://github.com/user-attachments/assets/d3c9d8f0-e4d2-4bb1-b141-ec12007f9d69)


Si queremos ver los contenedores activos también tenemos las dos opciones, consola o aplicación.

![image](https://github.com/user-attachments/assets/ec5684b9-e073-4f35-afb3-c32ccaefbfb1)
![image](https://github.com/user-attachments/assets/aea22736-d639-4b92-a955-fdf4383e1639)

No aparece ninguno porque, como podemos ver, no hay contenedor activo


Si quisieramos verlos todos ejecutamos el siguiente comando

![image](https://github.com/user-attachments/assets/a4ffd60f-eff2-4aa7-a98b-78288f4e53b8)

Ahora vemos como aparecen los dos contenedores presentes en el apartado anterior


## Actividades del segundo artículo
### Edita el fichero Dockerfile
Para editar el fichero desde la terminal escribimos lo siguiente y añadimos la configuración que queramos
```bash
nano Dockerfile
```
Mi ejemplo:

![image](https://github.com/user-attachments/assets/abd11a58-5c17-4900-b791-d305e154bc43)


### Construye el contenedor
Para construir el contenedor, en la misma carpeta donde se encuentra mi Dockerfile, escribimos lo siguiente:

![image](https://github.com/user-attachments/assets/788072d6-a293-4b56-bb54-50b878512345)

El nombre que le daremos a la imagen que usaremos en el contenedor es "mi-imagen", podremos modificarlo cuando queramos

### Ejecútalo
Con el siguiente comando ponemos en marcha el contenedor con nuestra imagen

![image](https://github.com/user-attachments/assets/40f4e8af-3d23-4aa2-b20d-bf6614dcbf3c)

Aquí podemos ver como devuelve lo que hemos establecido

![image](https://github.com/user-attachments/assets/975b4038-55f0-4354-97cd-a6933c3fdd01)


### Create una cuenta en hub.docker.com
Accedemos a la web y hacemos clic en el botón de la esquina superior "Sing Up", en mi caso accedí con la cuenta de Google

![image](https://github.com/user-attachments/assets/7e4c5594-95fe-4ad3-8bf6-b3ff16571292)

Desde la terminal escribimos el siguiente comando introduciendo nuestro nombre de usuario y contraseña

![image](https://github.com/user-attachments/assets/70b78d0a-f204-4dc3-825c-836bd6c87323)


### Publícalo


