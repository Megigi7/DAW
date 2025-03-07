# Práctica 4
## Ejemplo 1: Creación y uso de un volumen en Docker
Creamos un volumen llamado "mis_datos":

![image](https://github.com/user-attachments/assets/6c659625-c5ed-40da-8e8c-b85aeba68bd9)

Ejecutamos un contenedor de Ubuntu y montamos el volumen
Dentro del contenedor creamos un archivo en el volumen y salimos con "exit"

![image](https://github.com/user-attachments/assets/dc13674f-bcc1-44b3-98d2-c5e9ff31cc77)

Ejecutamos otro contendor de Ubutnu y desde él accederemos al archivo creado

![image](https://github.com/user-attachments/assets/630a7362-d046-4294-a4ad-82aab8e55333)

Como podemos ver, los volúmenes pueden verse entre ellos

## Ejemplo 2: Creación de una red personalizada y conexión de contenedores
Creamos una red personalizada llamada "mi_red"

![image](https://github.com/user-attachments/assets/73bcae92-ced1-4cf9-8f8e-a7d9863c34b5)

Ejecutmaos un contenedor Nginx y un contenedor Ubuntu dentro de la red

![image](https://github.com/user-attachments/assets/28ea6fe1-df81-4fb7-9714-7ab819bf7dde)

![image](https://github.com/user-attachments/assets/2c0e79c0-3c05-40c1-acae-8226a77450ab)

En el contenedor Ubuntu (cliente) instalaremos curl para acceder al contendor Nginx (servidor)

![image](https://github.com/user-attachments/assets/071676f1-6fb2-4113-8902-9f3cf799e0c3)

![image](https://github.com/user-attachments/assets/341e2349-918b-400f-a377-51c91faf18a8)

Podemos ver que se ha conectado correctamente y que nos devuelve su contenido

## Ejemplo 3: Uso de una red bridge para aislar contenedores
Docker cuenta con una red bridge por defecto, ejecutaremos un contenedor Nginx en ella

![image](https://github.com/user-attachments/assets/4883693c-e4e9-4e35-9459-730ceb34515e)

En esta misma red, ejecutaremos un contenedor Ubuntu

![image](https://github.com/user-attachments/assets/f1297dea-6f07-45d1-96cc-4573e942fc96)

Desde este contenedor haremos lo mismo que en el ejemplo anterior, instalamos curl y accederemos al contenedor Nginx

![image](https://github.com/user-attachments/assets/52d60054-ab26-48d5-8da6-16391b8b1136)

Como vemos, no puede resolver el nombre de nuestro contenedor Nginx porque la red bridge, por defecto, no permite la resolución de nombres de contenedores automáticamente.

Para acceder lo haremos mediante IP, con el siguiente comando conseguimos la IP del contenedor Nginx

![image](https://github.com/user-attachments/assets/83cf2708-10ae-47a4-bf39-946037f24a5f)

Cuando sepamos la IP accedemos de nuevo al contenedor Ubuntu y ejecutamos "curl" de nuevo, pero esta vez usando la IP en vez del nombre

![image](https://github.com/user-attachments/assets/f2493d26-3515-4828-bd03-a7cadf5677bb)

Ahora sí hemos podido acceder a su contenido


