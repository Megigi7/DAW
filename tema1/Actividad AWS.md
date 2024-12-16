# Usando una instancia AWS debemos instalar Apache con las siguientes opciones de configuración:
Primero mostraremos como inicializar la máquina virtual en aws
Accedemos a la web de aws -> https://awsacademy.instructure.com/
Accedemos a nuestro curso y vamos hasta "Laboratorio" ↓
![image](https://github.com/user-attachments/assets/3ea71ed2-cd17-404d-bd17-2fc71b31b7a4)

Una vez accedemos inicializamos nuestra máquina y en la sección "AWS details" descargamos las claves SSH
![image](https://github.com/user-attachments/assets/a51d669b-a5c1-46d8-8977-dca987790310)

Hacemos click en "AWS" y buscamos EC2 > Instancias
![image](https://github.com/user-attachments/assets/31013f99-99e1-417e-b352-2e43a73ceb2b)
![image](https://github.com/user-attachments/assets/15fe1110-2979-431e-9e04-1b5c28e1f5c6)

Crearemos una nueva instancia dandole al boton "Lanzar instancia"
![image](https://github.com/user-attachments/assets/aaffb747-0473-4592-a9f4-031e216a408b)

Le ponemos nombre y establecemos el sistema operativo a Ubuntu
![image](https://github.com/user-attachments/assets/cf8dc068-44b7-445b-a740-a2cc65baf68f)

Elegimos la clave de inicio de sesión a "vockey"
![image](https://github.com/user-attachments/assets/70fbf70a-a9dd-47ee-901d-69feccef273b)

Por lo demás, lo dejaremos por defecto
Finalizamos dándole a "Lanzar estancia" y esperamos a que se cree
![image](https://github.com/user-attachments/assets/aa10838c-8458-4014-a339-96d8dbf641ed)

Ya tenemos nuestra instacia, accedemos a ella
![image](https://github.com/user-attachments/assets/53c45340-f886-450c-827f-bd68cb41c758)

Seleccionamos la instacia y le damos a "Conectar"
![image](https://github.com/user-attachments/assets/e5ce7914-3ffb-4911-8bdf-b24d83c9831f)

A continuación pulsamos "Conectar" y nos abrirá una nueva pestaña con nuestra máquina
![image](https://github.com/user-attachments/assets/4d90eb51-0df8-4086-8965-5c8c71e99597)
![image](https://github.com/user-attachments/assets/3af515c3-05e6-4bf3-b823-0275bcc882aa)

## Activar la autenticación con MySql
Comenzamos instalando Apache, habilitamos y activamos
![image](https://github.com/user-attachments/assets/5368fa81-8858-45e2-af2a-d1b7fea667b4)
![image](https://github.com/user-attachments/assets/70ca6b2b-533a-4830-ba31-9f0c8efcb1ca)

Instalamos el módulo mod_authn_dbd para la autenticación
![image](https://github.com/user-attachments/assets/990d1942-c3bf-4ea7-a149-f5b5aaf33b7d)

Editamos el archivo principal de Apache para habilitar el módulo
```bash
sudo nano /etc/apache2/apache2.conf
```
![image](https://github.com/user-attachments/assets/aa5f75f9-01b2-4420-95a4-dfe402b49cbd)
En este caso no tenemos una base de dato específica, la tercera línea modificaría sus parámetros dependiendo de qué estemos usando

Reiniciamos apache
```bash
sudo systemctl restart apache2
```

## Crear un certificado autofirmado y activar el módulo SSL
Instalamos el módulo mod_ssl
![image](https://github.com/user-attachments/assets/3371a0cc-78a0-4b40-b1cd-f3cbfcf5647a)

Generamos un certificado autofirmado, creamos las carpetas donde se guardarán las claves y ejecutamos el siguiente comando
![image](https://github.com/user-attachments/assets/36ff772a-d999-4772-97f1-220c721fbfef)

Al ejecutarlo, nos pedirá unos datos, lo introducimos:
![image](https://github.com/user-attachments/assets/1fc5c1ef-da1e-4ccc-a161-75272b5c49e6)

Editamos el archivo de configuración
```bash
sudo nano /etc/apache2/sites-available/default-ssl.conf
```
![image](https://github.com/user-attachments/assets/fd274f81-fc10-43d3-a557-fa4e2a9eb974)
Ponemos la dirección de nuestras claves

Habilitamos el módulo SSL y el sitio HTTP
![image](https://github.com/user-attachments/assets/81af1be0-0a8c-416f-8b83-8d4547a02d42)
![image](https://github.com/user-attachments/assets/9f2390ee-0485-4022-ab90-e90b7f831553)

Finalmente reiniciamos apache
![image](https://github.com/user-attachments/assets/27108bda-bf12-4be7-9b9e-9114453e6edf)





