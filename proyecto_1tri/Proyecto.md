## Práctica Servidores web - 1º trimestre

### Usaremos dos dominios mediante el archivo hosts: centro.intranet y departamentos.centro.intranet. El primero servirá el contenido mediante wordpress y el segundo una aplicación en python
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


- Python
