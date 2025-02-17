# Instalación de Wordpress en instancia Debian(o Ubuntu) EC2 con soporte de base de datos RDS y EFS
En esta tarea configuraremos un servidor web apache montado en una instancia EC2 Ubuntu con un sistema de almacenamiento en EFS y la base de datos que esté gestionada por RDS en una subred privada.
Aunque algunos de los pasos detallados ya han sido realizados en el pasado, yo lo reharé para acompañar la explicacion

## 1. Creación de infraestructura de red
Para comenzar, antes de crear las instancias, necesitamos crear nuestra infraestructura de red en AWS, lo haremos siguiendo estos pasos:
Accedemos a el apartado "VPC" y hacemos clic en "Crear VPC"

![image](https://github.com/user-attachments/assets/2588440f-92cc-4d9a-916c-82835abc95b2)

Aquí podremos crear y configurar la VPC tal y como vemos en la imagen
![image](https://github.com/user-attachments/assets/4683d3c1-34cb-49e3-9c56-f6c8b9f62df9)

Una vez finalizado hacemos clic en "Crear VPC" ![image](https://github.com/user-attachments/assets/5a7ffa5b-1fcd-40e4-9d02-b95e616b4741)

Cuando termine el proceso de creación, podremos ver nuestra VPC
![image](https://github.com/user-attachments/assets/4c4a8608-eda9-485e-9ef0-cbbfb365223d)
