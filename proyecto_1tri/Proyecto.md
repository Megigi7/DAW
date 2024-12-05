- 1º trimestre

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
sudo mkdir /var/www/html/departamentos.centro.intranet/mypythonapp
sudo mkdir /var/www/html/departamentos.centro.intranet/public-html
sudo mkdir /var/www/html/departamentos.centro.intranet/mypythonapp/logs
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
- Adicionalmente protegeremos el acceso a la aplicación python mediante autenticación
Protegeremos nuestra aplicación con htpasswd. Instalamos:
```bash
sudo apt install apache2-utils
```
Creamos una archivo de contraseña para un nuevo usuario, en nuestro caso "admin"
![image](https://github.com/user-attachments/assets/7249b23b-cbd8-4e02-a1e7-cb1723cd3064)

En el archivo de configuración de nuestro sitio añadimos estas líneas
![image](https://github.com/user-attachments/assets/8c7d3cfd-c61d-4f1d-961d-5be5e00cdfdd)

Reiniciamos apache
```bash
systemctl restart apache2
```
Accedemos a nuestra página web, nos aparece esta alerta donde nos pide nuestras credenciales, si introducimos los datos que especificamos en el archivo creado anteriormente, podremos acceder
![image](https://github.com/user-attachments/assets/1b73c20d-5daa-4af6-9531-fe915b163846)


- Instala y configura awstat
```bash
sudo apt install awstats
```
Si ejecutamos el comando 'awstats' podemos ver que se ha instalado correctamente
![image](https://github.com/user-attachments/assets/40cb89a3-935b-4861-9203-6607262498d3)

Copiamos el archivo de configuración de awstats a uno nuevo, añadiendole el nombre de nuestro dominio
![image](https://github.com/user-attachments/assets/6bfc4050-aa9c-4525-b61b-c18e28fae32e)

Lo modificamos y ajustamos estas líneas
![image](https://github.com/user-attachments/assets/146a92e6-55f8-4c35-8283-30bd140f4058)

Creamos las estadísiticas iniciales con:
![image](https://github.com/user-attachments/assets/c200d462-c617-4030-8ec5-612392922273)

Creamos un alias para acceder a AWStats, editamos el archivo de configuración de Apache
```bash
sudo nano /etc/apache2/sites-available/000-default.conf
```
Y añadimos lo siguiente
![image](https://github.com/user-attachments/assets/eecb4395-d04e-4712-a851-b6d906473af4)

Guardamos y reiniciamos apache
```bash
systemctl restart apache2
```
Accedemos a la dirección añadiendo /awstats/awstats.pl?config="" y en config la dirección de nuestra web
![image](https://github.com/user-attachments/assets/99068375-3e35-4fe6-84d4-2e8928752e74)

- Instala un segundo servidor nginx bajo el dominio “servidor2.centro.intranet”.
Instalamos NGINX
```bash
sudo apt install nginx
```
Creamos un archivo de configuración para nuestro servidor y añadimos lo siguiente
```bash
sudo nano /etc/nginx/sites-available/servidor2.centro.intranet
```
![image](https://github.com/user-attachments/assets/4af9e153-12a5-4897-90e3-c5d4402f2395)

Creamos el directorio que será la raíz de nuestro dominio
```bash
sudo mkdir -p /var/www/servidor2.centro.intranet
```
Activamos la configuración de NGINX
![image](https://github.com/user-attachments/assets/8672e5b5-fead-4d55-9984-391cf736d144)

Hacemos que escuche por el puerto 8080. Editamos el archivo de configuración
```bash
sudo nano /etc/nginx/sites-available/default
```
![image](https://github.com/user-attachments/assets/83ffedbf-d17f-4585-89b7-3747ba270858)

Creamos el archivo index.php en nuestra carpeta del servidor
![image](https://github.com/user-attachments/assets/308c0717-d8dc-4b3d-bb24-9cf27496a73b)
_no se muestra en las capturas, pero cambié de lugar el directorio del servidor con mv_
![image](https://github.com/user-attachments/assets/bd436613-83cb-40af-af46-521f43c27d93)

Editamos el archivo hosts y añadimos la siguiente línea
```bash
sudo nano /etc/hosts
```
![image](https://github.com/user-attachments/assets/f9b027e2-be97-4a3d-a90f-73c6d6ca8212)

Accedemos a la página y podremos ver el archivo generado
![image](https://github.com/user-attachments/assets/d66d8251-22fe-40f0-bf65-0db94a89e381)

Nuestro servidor nginx con php estaría listo, no hemos necesitado instalar nada de php ya que lo hicimos antes

-  Instala phpmyadmin
```bash
sudo apt install phpmyadmin -y
```
Al instalar, nos aparecerá esta ventana, elegimos apache2
![image](https://github.com/user-attachments/assets/615f7f1c-de55-419b-99df-8470f9092b87)

Después elegimos "Sí" para crear la base de datos
![image](https://github.com/user-attachments/assets/20c53726-b00c-426d-9a9d-e997849368fe)

Nos pedirá una contraseña, introducimos una que cumpla los requisitos de seguridad
![image](https://github.com/user-attachments/assets/c1bbb483-5da5-4bdf-b23e-623d988b6cc3)

Una vez instalado, creamos un enlace simbólico para phpmyadmin
![image](https://github.com/user-attachments/assets/232d9bf3-3f07-40c0-9c62-b3742579b431)

Accedemos a la direccion de nuestro dominio añadiendole /phpmyadmin
![image](https://github.com/user-attachments/assets/1645b7de-ae82-4655-932a-4627913734a7)

Con esto, phpmyadmin estaría instalado y listo para ser usado y nuestra práctica habría finalizado
