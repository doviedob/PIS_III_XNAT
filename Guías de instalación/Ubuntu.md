# Instalación del software XNAT
## Ubuntu
Para realizar la instalación en el sistema operativo Ubuntu se realiza mediante Docker. Los prerequisitos para la instalación son:
- Más 4GB de memoria disponible
- Java 8 JRE o JDK (XNAT no se ejecutará con versiones posteriores de Java)
- Apache Tomcat 8.5 o 9.0 (recomendado; compatible con 7.0 pero requiere una configuración especial)
- PostgreSQL 10 o posterior

Abra una terminal de Ubuntu y actualizar el sistema con el comando: 
```
sudo apt update 
```
Posteriormente, aplique las modificaciones sugeridas en la actualización:
```
sudo apt upgrade 
```
Tambien deberá verificar que se tiene Java:
```
java -version  
```
De no tenerlo, instalarlo
```
sudo apt install default-jre   
```
Verifica la instalación
```
java -version   
```
***Instalación de XNAT clonando el repositorio xnat-docker-compose***

El tutorial oficial se encuentra en la [pagina oficial de XNAT](https://wiki.xnat.org/documentation/getting-started-with-xnat/running-xnat-in-a-dockerized-container-with-configurable-dependencies) 

1. Abrir la terminal Ubuntu y clonar el repositorio xnat-docker-compose alojado en el [Git](https://github.com/NrgXnat/xnat-docker-compose) 
```
git clone https://github.com/NrgXnat/xnat-docker-compose 
```
```
cd xnat-docker-compose    
```
2. Establecer las variables de entorno de Docker:
```
cp default.env .env 
```
3. Iniciar el Sistema:
```
docker-compose up -d 
```
4. Puede supervisar el estado de la implementación observando el registro generado para el contenedor xnat-web:
```
docker logs --follow xnat-web
```
5. Minutos despues observará un mensaje similar al siguiente:
```
Mar 02, 2021 10:35:24 PM org.apache.catalina.startup.Catalina start
INFO: Server startup in 208163 ms
```
6. Podrá ingresar al sistema mediante el siguiente enlace que lo dirigirá al [inicio de XNAT](http://localhost/)

7. Se observará una pantalla como la siguiente:

![Login page](https://raw.githubusercontent.com/doviedob/PIS_III_XNAT//master/Images/Login.png)

Con lo anterior, podrá ingresar al sistema con las siguientes credenciales:
- User: admin 
- Password: admin 

***NOTA:*** Cada vez que ingrese a XNAT usará esas mismas credenciales 
