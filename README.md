# PIS_III_XNAT
Guía de instalación

# Instalación del software XNAT
## Windows
Para realizar la instalación en el sistema operativo Windows se realiza mediante Docker. Los prerequisitos para la instalación son:
- Más 4GB de memoria disponible
- Docker desktop
- Subsistema Linux

1. **Instalar Docker**

Link descarga: https://www.docker.com/products/docker-desktop/ 

Posteriormente se deben configurar permisos para uso de Ubuntu en Docker. En el panel izquierdo, entra a la opción “Resources”, presionar en “WSL integration” y marcar Ubuntu. Luego Appply and restart. 

2. **nstalar la última versión de Ubuntu para Windows**

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
