En esta práctica realizaremos 3 scripts que nos permitiran modificar y crear archivos de una forma cómoda y rápida

## 1. Crea un script que añada un puerto de escucha en el fichero de configuración de Apache. El puerto se recibirá como parámetro en la llamada y se comprobará que no esté ya presente en el fichero de configuración.
```bash
if["$#" -ne "1"]
then
	echo "falta num puerto"
else 
	echo "correcto"
	GREP "LISTEN$1" "/etc/apache2/parts.conf"
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
Habiendose ejecutado correctamente con su parámetro, empezamos buscando 
