# Práctica 3
## Descarga la imagen de ubuntu, hello-world y nginx
Para descargar dichas imáganes ejecutamos el mismo comando para las tres, especificando su nombre: 

![image](https://github.com/user-attachments/assets/7d207fc9-2669-4c0e-babc-3332f561737a)


## Muestra un listado de todas la imágenes
Ejecutamos el comando "docker images"

![image](https://github.com/user-attachments/assets/51f7c8fb-41d9-45f3-81a2-716d29d16bb0)

Como podemos ver, señaladas en la imagen están las imágenes que acabamos de descargar


## Ejecuta un contenedor hello-world y dale nombre “myhello1”, “myhello2” y “myhello3”
Seguimos el mismo procedimiento para los tres
```bash
docker run --name myhelloX hello-world
```

![image](https://github.com/user-attachments/assets/cafda125-367b-4153-811e-ac41f7a79725)


## Muestra los contenedores que se están ejecutando
Para ver los contenedores escribimos el siguiente comando:

![image](https://github.com/user-attachments/assets/14022b60-6fc2-40c4-bd97-e7b507839b00)

Como podemos ver, ninguno de los tres contenedores se están ejecutando debido a que son "hello-world"s y esos contenedores son efímeros, indicando que se ejecutan y se detienen al instante 


## Para el contenedor "myhello1”, "myhello2”
Para detenerlos introducimos lo siguiente:
![image](https://github.com/user-attachments/assets/811eee80-b4e7-4bed-ad3d-7024fe59c639)


## Borra el contenedor “myhello1”
Ejecutamos este comando para borrar dicho contenedor

![image](https://github.com/user-attachments/assets/72719662-79c9-496c-9389-3ea96b87d42b)


## Muestra los contenedores que se están ejecutando.
De nuevo, veremos que no hay ninguno ejecutándose, pero si vemos todos podremos ver que myhello1 se ha eliminado correctamente

![image](https://github.com/user-attachments/assets/04dc2ab7-0352-4636-98a5-0fec237f7b10)


## Borra todos los contenedores
Por último, para eliminarlos todos, prodecemos con este comando:

![image](https://github.com/user-attachments/assets/9aa74efb-5860-42da-9770-2f4dab0ad9f6)

Todos los contenedores han sido eliminados
