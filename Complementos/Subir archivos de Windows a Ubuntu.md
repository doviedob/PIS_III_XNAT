# Cómo subir todos los archivos de Windows al sistema de la terminal Ubuntu

1. Escriba este comando para ir al directorio raíz:
```
cd /
```
2. Cree una nueva carpeta donde quiera subir los archivos de sistema de Windows:
```
sudo mkdir /mnt/windows 
```
3. Con el siguiente commando se montarán todos los archivos:
```
sudo mount -t drvfs C: /mnt/windows 
```

***NOTA:*** Este comando asume que sus archivos están en el disco C, de no estar ahí, cambie la letra C en el comando por la que corresponda.

De ahora en adelante, cada vez que desee acceder a los archivos de Windows, escriba en su consola
```
cd mnt/windows 
```
