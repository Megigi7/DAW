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

Si accedemos a la IP pública de nuestra instancia podremos ver la página de inicio de apache
![image](https://github.com/user-attachments/assets/b5d4e424-0657-49f7-9788-963daf62a413)


Continuamos instalando PHP con los siguientes comandos:

Actualizamos nuestra instancia para asegurar que tenemos todo lo necesario instalado 
```bash
sudo apt -y update && sudo apt upgrade
```

Instalamos php como un módulo de Apache:

![image](https://github.com/user-attachments/assets/6dd93d02-9245-4159-83b4-f85bac34718f)

En mi caso no especificaré versión ya que la versión que indicada en el manual no está disponuble en instancias Ubuntu, así que ejecutaremos el mismo comando sin especificar versión


También necesitamos instalar mysql como módulo de apache:

![image](https://github.com/user-attachments/assets/f6a9abb1-c2d2-45e0-ac6b-d52e6ef2a769)


Y reiniciamos apache:
```bash
sudo systemctl restart apache2
```

Comprobamos que php esté instalando preguntando por su versión
![image](https://github.com/user-attachments/assets/e7e88eef-f772-41da-8b49-0bc4c41fe310)


## 3. Creación de Base de Datos
En AWS, accedemos al apartado RDS
![image](https://github.com/user-attachments/assets/958d1d7d-7b74-4f1b-9b21-882ceb36d679)

Hacemos clic en "Crear nueva base de datos"

![image](https://github.com/user-attachments/assets/01ac0695-d589-4a12-a7b6-e6b72ae6c95f)

Configuramos las opciones de la base de datos siguiendo las imágenes:
![image](https://github.com/user-attachments/assets/ef83df94-cfd9-4e67-b058-ef48032a4490)

![image](https://github.com/user-attachments/assets/84a65d1e-b789-4772-b739-bd43f6d543fa)

Introducimos un nombre a la base de datos y unas credenciales, en mi caso la contraseña es "Abcd1234%"
![image](https://github.com/user-attachments/assets/48b55277-ace2-4f03-b4bf-cdf7c3d95402)

![image](https://github.com/user-attachments/assets/c809b1fa-59d5-4468-9c47-4742d9fb96f8)

![image](https://github.com/user-attachments/assets/7a8fbe97-a745-4828-8f4d-929ba51b6caf)

Elegimos la VPC de nuestra práctica
![image](https://github.com/user-attachments/assets/d167808b-55e7-443f-95bc-c027e6f204ff)

En este paso es importante tener en cuenta que el nombre de la base de datos inicial sea el mismo nombre que el de la instancia que establecimos enteriormente 
![image](https://github.com/user-attachments/assets/57dab83d-8522-4d75-98c4-8de48764291e)

Una vez todo configurado, creamos la base de datos ![image](https://github.com/user-attachments/assets/45a433ae-9ba5-4231-bc70-b555c27dc617)

Ajustamos el grupo de seguridad para permitir la entrada desde nuestra instancia.
Esta configuración no es la ideal a que puede ser insegura, pero para nuestra práctica nos ahorrará problemas
![image](https://github.com/user-attachments/assets/8adbcfcd-53d0-46ca-9a0b-9ad9d72d05d4)

Seguimos configurando la conexión, seleccionamos la base de datos y le damos a "Acciones" > "Conexion de EC2" 
![image](https://github.com/user-attachments/assets/8f57f6d8-94d0-404e-a72b-e45f1ec90e81)

Elegimos nuestra instancia y guardamos
![image](https://github.com/user-attachments/assets/1eb15f70-5c11-4d81-8316-0344eed68f53)
Nos saldrá un resumen de la configuración establecida, revisamos que esté todo como queremos y continuamos

Entrando a los detalles de la base de datos podremos ver su Punto de enlace
![image](https://github.com/user-attachments/assets/95872bd4-8a2c-47a9-be27-c09c77d1cacb)

Ya tendríamos lista nuestra base de datos, pasamos al siguiente punto


## 4. Elastic File System.
Accedemos al apartado "EFS" y hacmeos clic en "Crear sistema de archivos"
![image](https://github.com/user-attachments/assets/60fc08a5-3350-49bc-90ea-f5e31209d2f5)

Establecemos un nombre y elegimos la VPC de nuestra práctica
![image](https://github.com/user-attachments/assets/c8751d21-49c1-483b-a2bc-d17283d6901b)

Comprobamos que se ha creado
![image](https://github.com/user-attachments/assets/e394beab-c70b-4eb0-8556-8882431c8012)

Asociamos el EFS a nuestra instancia seleccionandole y haciendo clic en "Asociar"
![image](https://github.com/user-attachments/assets/98c8026d-a96a-49ab-bfdd-ec0f8980def6)

Nos da unas instrucciones para poder conectarse, elegiremos el segundo
![image](https://github.com/user-attachments/assets/4a47863b-6f1d-4e1a-8271-1255360c78d1)

Antes de ejecutar el comando proporcionado, crearemos la carpeta "efs" y ejecutamos el comando de instalacion de efs
![image](https://github.com/user-attachments/assets/5c94b741-4a3d-4ce7-a45b-85b84bfc0f24)
![image](https://github.com/user-attachments/assets/717d1f81-7fde-4d95-a420-94a52265ff53)

Ejecutamos el comando proporcionado:
![image](https://github.com/user-attachments/assets/e29f4471-03de-4667-b946-7a34785b9dd2)

Ya tenemos todo listo, podemos instalar Wordpress

## 5. Instalación de Wordpress
Accedemos al directorio /var/www/html y ejecutamos el siguiente comando para descargar Wordpress
![image](https://github.com/user-attachments/assets/a7b93ac3-6398-4ba2-902e-7f740082a321)

Descomprimimos el fichero descargado
![image](https://github.com/user-attachments/assets/34518fe4-4f38-4b56-ab7f-52651cc0dd73)

Como podemos ver en la captura, ya tenemos nuestra carpeta de Wordpres

Para crear las credenciales seguimos los siguientes pasos:
![image](https://github.com/user-attachments/assets/99e50b50-877d-4d65-8398-20ab691dd90c)

Nos conectamos a la instancia de la base de datos con el siguiente comando:
Usamos el punto de acceso proporcionado para la BD
La contraseña será la que establecimos al crear la instancia (Abcd1234% en mi caso)
![image](https://github.com/user-attachments/assets/ace676cb-d897-43a5-a1aa-783afd56586a)

En la consola de mysql escribimos las siguientes líneas, con esto creamos la base de datos, el usuario y le damos permisos al usuario para poder trabajar en la base de datos
```bash
CREATE DATABASE wordpress; 
CREATE USER 'user' IDENTIFIED BY 'user'; 
GRANT ALL PRIVILEGES ON wordpress.* TO 'user'; 
FLUSH PRIVILEGES;
```

Cuando accedemos a la IP pública, añadiendole /wordpress a la url, vemos esta pantalla
![image](https://github.com/user-attachments/assets/429d7c53-f0bb-4747-bbdc-a5d4e6b18a5f)

Para continuar con la instalación introducimos los datos que nos pide
- El nombre de la base de datos es la que hemos creado en el paso anterior
- Las credenciales son las que creamos anteriormente al crear la base de datos (admmin y Abcd1234% en mi caso)
- El host de la base de datos será la puerta de enlace de nuestra base de datos
![image](https://github.com/user-attachments/assets/fade0dd1-b328-40f2-ba2d-62bd966099d8)

Una vez hemos accedido a la base de datos ya podríamos comenzar a trabajar con ella



