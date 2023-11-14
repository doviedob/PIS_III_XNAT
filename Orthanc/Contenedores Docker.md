# CONTENEDORES DOCKER
## Comandos útiles 
- ***Eliminar una imagen***

Primero debes asegurarte de que ningún contenedor esté utilizando la imagen actualmente porque esto no te permitirá eliminarla. 

Para ver qué contenedores están en funcionamiento utiliza el comando:
```
docker ps –a 
```
Para detener el o los contenedores que estén usando tu imagen utiliza:
```
docker ps -a | grep nombre_de_tu_imagen | awk '{print $1}' | xargs docker stop 
```
Para eliminarlos utiliza:
```
docker ps -a | grep nombre_de_tu_imagen | awk '{print $1}' | xargs docker rm 
```
Finalmente para eliminarla:
```
docker rmi 
```

- ***Convertir un código python en una imagen Docker***

Debes ubicarte en la carpeta en la que tienes tu código y crear un archivo que tenga por nombre Dockerfile (debe llamarse exactamente así, con la D mayúscula y el resto en minúscula). Este archivo no debe tener ninguna extensión y su estructura básica es esta:

1. Usa la imagen base de Python
```
FROM python:3.8 
```
2. Instala las librerías necesarias
```
RUN pip install librería1 librería2
```
3. Copia el script Python al contenedor
```
COPY nombre_de_tu_script.py /app/ nombre_de_tu_script.py 
```
4. Establece el directorio de trabajo
```
WORKDIR /app
```
5. Ejecuta el script al iniciar el contenedor con argumentos pasados al script
```
CMD ["python", " nombre_de_tu_script.py"] 
```
