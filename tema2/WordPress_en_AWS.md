# Instalación de Wordpress en instancia Debian(o Ubuntu) EC2 con soporte de base de datos RDS y EFS
En esta tarea configuraremos un servidor web apache montado en una instancia EC2 Ubuntu con un sistema de almacenamiento en EFS y la base de datos que esté gestionada por RDS en una subred privada.
Aunque algunos de los pasos detallados ya han sido realizados en el pasado, yo lo reharé para acompañar la explicacion

## 1. Creación de Instancia
Para comenzar, antes de crear las instancias, necesitamos crear nuestra infraestructura de red en AWS, lo haremos siguiendo estos pasos:
Accedemos a el apartado "VPC" y hacemos clic en "Crear VPC"

![image](https://github.com/user-attachments/assets/2588440f-92cc-4d9a-916c-82835abc95b2)

Aquí podremos crear y configurar la VPC tal y como vemos en la imagen
![image](https://github.com/user-attachments/assets/4683d3c1-34cb-49e3-9c56-f6c8b9f62df9)

Una vez finalizado hacemos clic en "Crear VPC" ![image](https://github.com/user-attachments/assets/5a7ffa5b-1fcd-40e4-9d02-b95e616b4741)

Cuando termine el proceso de creación, podremos ver nuestra VPC
![image](https://github.com/user-attachments/assets/4c4a8608-eda9-485e-9ef0-cbbfb365223d)

Si comprobamos los grupos de eguridad, vemos que tenemos un grupo correspondiente a nuestra VPC

![image](https://github.com/user-attachments/assets/13a82203-2b63-44e1-9943-e9fc942317f0)

Pasamos a crear la instacia
Accedemos a EC2 > Instancias > Lanzar Instacias

![image](https://github.com/user-attachments/assets/919e210f-1137-4b47-8566-28b1c1ae9ac7)

Aquí escribimos el nombre que le daremos y elegimos el OS, en mi caso Ubuntu

![image](https://github.com/user-attachments/assets/1bca42ec-5893-41f4-bd23-88c123e427ac)


Lo importante está en configurar correctamente el apartado de red, seleccionando la VPC que hemos creado y el grupo de seguridad correspondiente, además, comprobamos que la subred es una de las dos subredes públicas
![image](https://github.com/user-attachments/assets/064d962e-dc1b-4d5b-910f-5ae6a1e89bdf)

Una vez configurado, guardamos con "Lanzar Instancia" ![image](https://github.com/user-attachments/assets/fb9247cb-5cb7-430d-b11a-c1a60a0421b0)

Cuando finalice la creación de la instancia nos saldrá este mensaje
![image](https://github.com/user-attachments/assets/f246e3b6-6c21-43fe-8a92-7250e50d298d)

Como realizaremos la conexión por SSH y estamos en Windows, usaremos la aplicacion MobaXterm

Si hacemos clic en su id nos llevará al apartado "Instancias" donde veremos que esta nueva instancia está en ejecución
Dentro de este apartado, si volvemos a hacer clic en la Id, nos lleva a una vista más detallada de la instacia, aquí hacemos clic en "Conectar"
![image](https://github.com/user-attachments/assets/8d1a1275-1131-47b2-8e3c-a2a80b121e5c)

Aquí simplemente le damos a conectar, podríamos cambiar los campos señalados pero en este caso lo dejaremos por defecto ya que nos sirve igualmente

![image](https://github.com/user-attachments/assets/ba3b90eb-912f-40cf-8700-74860903ae3d)

Finalmente, ya estamos conectados a nuestra Instancia
![image](https://github.com/user-attachments/assets/986aedbc-b1e6-4f7b-9245-dc585aa61ee4)

## 2. Apache y PHP
Instalamos Apache introduciendo los siguientes comandos ↓
```bash
sudo apt update
sudo apt install apache2
```
![image](https://github.com/user-attachments/assets/997e8850-16ed-4b00-8b63-46e5a886e3e8)

Así actualizamos nuestra máquina, instalamos apache, iniciamos apache y habilitamos para que incie siempre



