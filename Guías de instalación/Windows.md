# Instalación del software XNAT
## Windows
Para realizar la instalación en el sistema operativo Windows se realiza mediante Docker. Los prerequisitos para la instalación son:
- Más 4GB de memoria disponible
- Docker desktop
- Subsistema Linux

1. Instalar Docker

Link descarga: https://www.docker.com/products/docker-desktop/ 

Posteriormente se deben configurar permisos para uso de Ubuntu en Docker. En el panel izquierdo, entra a la opción “Resources”, presionar en “WSL integration” y marcar Ubuntu. Luego Appply and restart. 

2. nstalar la última versión de Ubuntu para Windows

Link descarga: https://ubuntu.com/tutorials/install-ubuntu-on-wsl2-on-windows-10#1-overview 

3. Abrir la terminal de Ubuntu y actualizar el sistema con el comando: 
```
sudo apt update 
```
4. Aplicar las modificaciones sugeridas en la actualización:
```
sudo apt upgrade 
```
5. Verificar que se tiene Java:
```
java -version  
```
6. De no tenerlo, instalarlo
```
sudo apt install default-jre   
```
7. Verifica la instalación
```
java -version   
```
***Instalación de XNAT clonando el repositorio xnat-docker-compose***

El tutorial oficial se encuentra en: https://wiki.xnat.org/documentation/getting-started-with-xnat/running-xnat-in-a-dockerized-container-with-configurable-dependencies 

1. Abrir Docker Desktop. IMPORTANTE: LA APLICACIÓN DEBE PERMANECER ABIERTA DURANTE TODO EL TIEMPO QUE SE UTILICE XNAT
2. Abrir la terminal Ubuntu y clonar el repositorio xnat-docker-compose alojado en https://github.com/NrgXnat/xnat-docker-compose :
```
git clone https://github.com/NrgXnat/xnat-docker-compose 
```
```
cd xnat-docker-compose    
```
3. Establecer las variables de entorno de Docker:
```
cp default.env .env 
```
4. Iniciar el Sistema:
```
docker-compose up -d 
```
5. Puede supervisar el estado de la implementación observando el registro generado para el contenedor xnat-web:
```
docker logs --follow xnat-web
```
6. Minutos despues observará un mensaje similar al siguiente:
```
Mar 02, 2021 10:35:24 PM org.apache.catalina.startup.Catalina start
INFO: Server startup in 208163 ms
```
7. Podrá ingrresar al sistema mediante el siguiente enlace:

http://localhost/

8. Se observará una pantalla como la siguiente:

![Login page](https://raw.githubusercontent.com/doviedob/PIS_III_XNAT//master/Images/Login.png)

Con lo anterior, podrá ingresar al sistema con las siguientes credenciales:
- User: admin 
- Password: admin 

***NOTA:*** Cada vez que ingrese a XNAT usará esas mismas credenciales 

