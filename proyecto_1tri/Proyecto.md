![image](https://github.com/user-attachments/assets/10ae023d-ea7c-4169-bc7b-16bd57d7d095)## Práctica Servidores web - 1º trimestre

### Usaremos dos dominios mediante el archivo hosts: centro.intranet y departamentos.centro.intranet. El primero servirá el contenido mediante wordpress y el segundo una aplicación en python
Empezaremos creando las carpetas correspondientes 
![image](https://github.com/user-attachments/assets/fa325e27-ea66-4626-adb7-5ff77079f4ae)

1- Activar los módulos necesarios para ejecutar php y acceder a mysql
Comenzamos instalando todos los módulos necesarios
- Apache
```bash
sudo apt install apache2
```
![image](https://github.com/user-attachments/assets/4d2f7aea-c8b6-4346-a8cc-6b2c0ff2392c)

- Wordpress

Para instalar Wordpress primero necesitamos instalar php, con el siguiente comando instalamos php y sus extensiones
```bash
sudo apt install php libapache2-mod-php php-mysql php-curl php-gd php-xml php-mbstring php-xmlrpc php-zip php-soap php-intl -y
```
![image](https://github.com/user-attachments/assets/b8e1e919-af60-43a7-bb39-8fedd44f48ff)
Creamos un archivo php dentro de la carpeta creada anteriormente
![image](https://github.com/user-attachments/assets/34b652d5-4fd3-49d8-9564-166ad90b9885)

Instalamos mysql
```bash
sudo apt install mysql-server
```
![image](https://github.com/user-attachments/assets/e346a08f-2369-4198-acfd-94d451c5d9bb)

Accedemos a la configuración de mysql con
```bash
sudo mysql
```
Con el siguiente comando establecemos la contraseña para el usuario root, en nuestro caso será 123Abcd%
![image](https://github.com/user-attachments/assets/935293f3-de52-44c4-a221-6b256fac835a)

Creamos una base de datos
![image](https://github.com/user-attachments/assets/84aa7efc-d4f9-498d-af1d-e1df47c24073)

Creamos un usuario con el que operaremos sobre la base de datos
![image](https://github.com/user-attachments/assets/73bef850-53e6-4861-ba60-bc353b89d792)

Salimos de mysql
```bash
mysql> exit
```

Creamos un archivo de configuración para nuestra página de WordPress, para facilitar la tarea copiaremos el archivo ya existente 000-default.conf
![image](https://github.com/user-attachments/assets/4fa3e995-fffb-4392-974d-5afd1456a443)

Añadimos estas líneas

![image](https://github.com/user-attachments/assets/af53a598-0d9a-44a5-8e0a-1cb2088893ad)

Activamos el módulo rewrite y reiniciamos apache
![image](https://github.com/user-attachments/assets/4e1b6059-a21a-4a31-92cf-46f9c94f3117)

Modificamos el archivo de configuración de apache 
```bash
sudo nano /etc/apache2/apache2.conf
```
Añadimos esta línea, siendo la IP  la de nuestra máquina

![image](https://github.com/user-attachments/assets/08f741f4-4108-4cad-b02f-c66245572659)

  
Instalamos WordPress con wget
![image](https://github.com/user-attachments/assets/3992b4bf-96de-47c8-918c-fd4371f3fd55)

Movemos el archivo .zip que se ha descargado a la carpeta /etc/www/html
![image](https://github.com/user-attachments/assets/c32c9487-90b8-4fa6-9a35-9d1d0ac953c9)
Descomprimimos con 
```bash
sudo unzip latest.zip
```
Movemos todo lo de la carpeta recién creada "wordpress" a nuestra carpeta 
![image](https://github.com/user-attachments/assets/6c9fe3b2-5bcd-4671-bbc0-21422e786a15)

-- Accedemos a Wordpress
Para acceder introducimos la dirección "Nuestra IP"/centro.intranet
![image](https://github.com/user-attachments/assets/2a3cad57-c4aa-4bec-9a12-d1d5eace845c)

Iniciamos la instalación, nos pedirá datos para nuestra página en WordPress
![image](https://github.com/user-attachments/assets/3bbe335a-4350-47ef-9474-563af008bfbf)

Finalmente podemos iniciar sesión y acceder a WordPress con el usuario introducido


- Python
Activamos el módulo “wsgi” para permitir la ejecución de aplicaciones Python
```bash
sudo apt-get install libapache2-mod-wsgi-py3
```
Creamos las carpetas necesarias para la estructura de python
```bash
sudo /var/www/html/departamentos.centro.intranet/mypythonapp
sudo /var/www/html/departamentos.centro.intranet/public-html
sudo /var/www/html/departamentos.centro.intranet/mypythonapp/logs
```

Creamos un archivo dentro de mypythonapp que será el controlador añadiendole lo escrito en el comando
![image](https://github.com/user-attachments/assets/93b813f1-b9fd-4df0-9487-71d912c67ea5)

Además, le añadimos lo siguiente
![image](https://github.com/user-attachments/assets/d35493a8-83ae-44e5-8e57-251a1ae2ddef)

Editamos un nuevo archivo en la ruta especificada, le añadimos lo que se ve en el archivo
```bash
sudo nano /etc/apache2/sites-availables/python-web.conf
```
![image](https://github.com/user-attachments/assets/bc160c92-cfbd-4e4c-ab7d-7c66da1c98bb)


Activamos nuestro sitio web y reiniciamos apache
```bash
sudo a2ensite python-web
systemctl reload apache2
```

Editamos el archivo hosts y le añadimos ambas direcciones
```bash
sudo nano /etc/hosts
```
![image](https://github.com/user-attachments/assets/32db9bc5-a630-41b6-ac3a-c1b4ee84af70)

Creamos un script de python que será lo que se verá en la web
```bash
sudo nano /var/www/html/departamentos.centro.intranet/public_html/index.py
```
![image](https://github.com/user-attachments/assets/aad6608e-4071-468d-8efb-f57a6f250627)

Ejecutamos el script accediendo a su dirección
![image](https://github.com/user-attachments/assets/2ffd7534-3174-49ab-9584-421ff5d3b2fb)

