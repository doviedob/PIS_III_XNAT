La documentación completa la encuentra en el sitio oficial de [Orthanc](https://book.orthanc-server.com/users/debian-packages.html)

1. Abrir la terminal de Ubuntu
2. Actualizar el sistema con el comando: 
```
sudo apt update 
```
3. Aplicar las modificaciones sugeridas en la actualización:
```
sudo apt upgrade  
```
4. Instalar orthanc:
```
sudo apt install orthanc 
```
5. Puede instalar los plugin si así lo requiere:
```
sudo apt install orthanc-dicomweb 
sudo apt install orthanc-gdcm 
sudo apt install orthanc-imagej 
sudo apt install orthanc-mysql 
sudo apt install orthanc-postgresql 
sudo apt install orthanc-python 
sudo apt install orthanc-webviewer 
sudo apt install orthanc-wsi 
```
6. Inicia el servicio de orthanc:
```
sudo service orthanc start 
```
7. Para acceder al servidor se copia en la url del navegador:
   
http://localhost:8042/

El puerto 8042 es el puerto a través del cual se accede a Orthanc 

8. Para parar o resetear el servidor, se tienen los siguientes comandos:
```
sudo service orthanc stop 
```
```
sudo service orthanc restart 
```
