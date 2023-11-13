# Subir archivos a XNAT via consola
## Curl

La mayoría de los sistemas UNIX tienen curl preinstalado, es una herramienta que permite establecer comunicación con un servidor. 

El comando es: 
```
curl -u USERNAME:PASSWORD -X PUT "http://central.xnat.org/data/PATH/TO/DESTINATION" -F "file=@filename.txt" 
```
La información adicional sobre este metodo la encontrará en la web oficial de [XNAT](https://wiki.xnat.org/display/XAPI/Tips+for+Uploading+Files+via+REST)

## XNAT Python client 

Permite trabajar con las estructuras de XNAT como si fueran objetos de Python. 

Ejemplo de lectura de proyectos y subida de archivos: 

![Login page](https://raw.githubusercontent.com/doviedob/PIS_III_XNAT//master/Images/python_client.png)

La información adicional sobre esta herramienta la podrá encontrar en el documento oficial de [XNAT](https://xnat.readthedocs.io/en/0.5.1/)
