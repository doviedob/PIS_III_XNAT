# CONEXIÓN CON XNAT
## Crear una conexión PACS en XNAT ML 

1. Inicie sesión en XNAT como usuario administrador. 
2. Abra las Preferencias de DQR. Vaya a "Administrar > Configuración de complementos" en la navegación superior, luego seleccione la pestaña "Configuración DQR". 
3. Agregue Orthanc como conexión DICOM AE. Busque el panel "Administrar conexiones DICOM AE (PACS)" y haga clic en "Agregar nuevo DICOM AE". Ingrese la siguiente configuración y haga clic en "Guardar":

![Login page](https://raw.githubusercontent.com/doviedob/PIS_III_XNAT//master/Images/connect_Ort-Xnat.png)

Configura todo tal cual se muestra en la imagen, pero en la parte de host se debe colocar el protocolo de internet (IP) con el cual se ha conectado XNAT.  

El puerto 4242 es comúnmente asociado con Orthanc, este utiliza el puerto 4242 como el puerto predeterminado para las conexiones DICOM a través del protocolo DICOM sobre HTTP (o DICOMweb), que es una forma moderna y basada en estándares para acceder a datos DICOM utilizando tecnologías web. 

4. Pruebe su conexión PACS. En la lista de DICOM AE, busque la instancia de Orthanc que acaba de agregar y haga clic en el botón "Ping".

![Login page](https://raw.githubusercontent.com/doviedob/PIS_III_XNAT//master/Images/connect_Ort-Xnat_1.png)

Debería ver un banner de éxito en la parte superior de la página que dice "Estado de PACS: Arriba". 

![Login page](https://raw.githubusercontent.com/doviedob/PIS_III_XNAT//master/Images/connect_Ort-Xnat_2.png)

## Creación de un receptor DICOM habilitado para DQR en XNAT 

El plugin DICOM Query-Retrieve emplea un método de "procesamiento personalizado" para facilitar el reetiquetado y la anonimización específicos de la sesión al importar desde PACS. Para utilizar esta función, es necesario configurar un receptor DICOM SCP en XNAT que haga uso de esta técnica. 

1. Inicie sesión en XNAT como usuario administrador. 

2. Abra Configuración de receptores XNAT DICOM SCP. Navegue hasta "Administrar > Configuración del sitio" en la navegación superior, luego haga clic en la pestaña "Receptores DICOM SCP" en el grupo "Configuración XNAT avanzada" 

3. Cree un nuevo receptor SCP. Haga clic en "Nuevo receptor DICOM SCP" e ingrese la siguiente configuración, luego haga clic en "Guardar":

![Login page](https://raw.githubusercontent.com/doviedob/PIS_III_XNAT//master/Images/DQR_1.png)

Asegúrese de que la opción "dqrObjectIdentifier" esté seleccionada. 

## Conecta tu modalidad a Orthanc 

Adicionalmente, se debe configurar Orthanc para que reconozca estea conexión. En un archivo de confguración de Orthanc se han de crear las modalidades: 

1. Cree el archivo de configuración:
```
Orthanc --config=Configuration.json 
```
2. Crea una copia de este y en la copia, se debe localizar la sección de “DicomModalities”  
3. Elimina todo el contenido de dicha copia y deja solo la sección anteriormente mencionada. 
4. En dicha sección debe crear 2 modalidades, las cuales han sido creado previamente pero en XNAT:
```
{
  "DicomModalities" : {
    "xnat" : ["XNAT_PACS", "172.21.86.117", 4242],
    "xdqr" : ["XDQR", "172.21.86.117", 8102]
}
}
```
“xnat” Hace referencia a como se llamará la modalidad en Orthanc.  El primer termino hace referencia al nombre con el que se identifica en XNAT, este por defecto viene como XNAT, sin embargo, este fue configurado a XNAT_PACS para evitar confusiones  entre variables. En el segundo termino va el IP (el mismo que fue usado en la sección de Conexión PACs con XNAT) y en el tercero va el puerto con el que se conecta que para orthanc es el 4242.  

“xdqr” Hace referencia al receptor dicom. En este caso puede poner los datos tal cual se muestra en la imagen haciendo el cambio de la IP.  

Una vez se haya creado el archivo, se debe detener el Orthanc y el XNAT y ejecutar el siguiente comando en una terminal:  
```
Orthanc ./Configuration.json 
```
Se debe poner el nombre del archivo luego del / 

Si todo fue exitoso, se debe iniciar automaticamente Orthanc:  

![Login page](https://raw.githubusercontent.com/doviedob/PIS_III_XNAT//master/Images/DQR_2.png)

Además, cuando se acceda a la sección DICOM query Retrieve, aparecerán las dos modalidades.

![Login page](https://raw.githubusercontent.com/doviedob/PIS_III_XNAT//master/Images/DQR_3.png)

Elija la modalidad de XNAT y haga click en Test Echo para verificar que la conexión sea exitosa. 

Posteriormente, se hace la comprobración en XNAT; inicialicelo de nuevo y en un proyecto busque la opción “import from PACS” 

![Login page](https://raw.githubusercontent.com/doviedob/PIS_III_XNAT//master/Images/DQR_4.png)

Busque algún estudio e importelo y compruebe que se reciba el archivo correctamente en la sección Upload, import Queu/history.  

![Login page](https://raw.githubusercontent.com/doviedob/PIS_III_XNAT//master/Images/DQR_5.png)

## RECOMENDACIONES

- Revisar que tanto Orthanc como XNAT no estén funcionando antes de correr el archvio de configuración. 

- Revisar que el archivo esté bien copiado, con las llaves necesarias y los datos adecuados 

- Si por alguna razón se corrió el archivo de configuración y no funcionó, se debe pausar Orthanc, ya que el archivo lo inicializa. Sin embargo, se debe es pausar el archivo para que pause Orthanc. Para hacer esto, consulte los archivos que se estén ejecutando: 
```
ps aux | grep Orthanc  
```
  Luego, elimine la ejecución del archivo de configuración: 
```
killall Orthanc../Configuration.json   
```
