En esta práctica realizaremos 3 scripts que nos permitiran modificar y crear archivos de una forma cómoda y rápida

## 1. Crea un script que añada un puerto de escucha en el fichero de configuración de Apache. El puerto se recibirá como parámetro en la llamada y se comprobará que no esté ya presente en el fichero de configuración.
```bash
if["$#" -ne "1"]
then
	echo "falta num puerto"
else 
	echo "correcto"
	GREP "LISTEN$1" "/etc/apache2/ports.conf"
	if["$?" eq 0]
	then
		echo "Listen ya encontrado en ports.conf"
	else
		echo "Listen añadido"
		echo "Listen $1" >> "/etc/apache2/ports.conf"
	fi
fi
```
Empezamos el script comprobando si al ser ejecutado se ha añadido un número de puerto como parámetro, si no es así notificamos al usuario de que falta
Habiendose ejecutado correctamente con su parámetro, empezamos buscando si la orden "listen" con dicho puerto existe en el archivo ports.conf, si existe se le muestra un mensaje al usuario indicándolo y se cierra, si no, añadimos la orden "listen" con el parámetro pasado al archivo ports.conf y notificamos al usuario con un mensaje por pantalla

## 2 Crea un script que añada un nombre de dominio y una ip al fichero hosts. Debemos comprobar que no existe dicho dominio en el fichero hosts
```bash
if [ "$#" -ne 2]
then
	echo "falta ip y host"
else
	echo "correcto"
	grep "$1 $2" "/etc/hosts"
	if["#?" eq 0]
	then
		echo "dominio ya existente en hosts"
	else
		echo "Dominio añadido"
		echo "$1 $2" >> "/etc/host"
	fi
fi
```
Este script es parecido al anterior, solo que esta vez contamos con dos parámetros y lo buscamos en el archivo /etc/hosts, si ya existe avisamos y si no lo añadimos

## 3 Crea un script que nos permita crear una página web con un título, una cabecera y un mensaje
```bash
if ["$#" -ne 3];
then
	echo "Parametros: titulo | cabecera | mensaje"
else
	TITULO $1
	CABECERA = $2
	MENSAJE $3
	NOMBRE_ARCHIVO = "web.html"
	echo "correcto, pagina creada como $NOMBRE_ARCHIVO"
	cat <<EOL> $NOMBRE_ARCHIVO
<!DOCTYPE html>
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<title>$TITULO</title>
</head>
<body>
	<h1>$CABECERA</h1>
	<p>$MENSAJE</p>
</body>
</html>
EOL
fi
```
Explicacion

### PUESTA EN MARCHA DE LOS SCRIPTS
Todos estos scripts para ser utilizados necesitan, en primer lugar, darle los permisos necesarios, lo hacemos con:
```bash
chmod 755 -nuestro archivo-
```

#### Script 1:


#### Script 2:


#### Script 3:
Ejecutamos el script y vemos que el archivo se ha creado
![image](https://github.com/user-attachments/assets/5a85c95b-94c6-4e74-babe-d3ba222168b0)

Comprobamos el contenido del archivo
![image](https://github.com/user-attachments/assets/08e0bdb8-89ca-4b63-b386-afd0ea86c821)


