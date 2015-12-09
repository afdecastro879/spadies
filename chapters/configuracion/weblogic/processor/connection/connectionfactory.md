# Modulo JMS

La creación del Módulo JMS se debe realizar en el Servidor Weblogic destinado para el procesamiento de datos ingresando por la URL:

```
http://ip-servidor-procesamiento:7001/console/
```
## Paso 1

En el panel ***Domain Structure*** expanda ***Services*** y ***Messaging***. Luego seleccione ***JMS Modules***.

![Git Paso 1](img/connetionPaso1.PNG)

## Paso 2

En  ***Summary of Resources*** hacer clic en ***new***.

![Git Paso 2](img/connetionPaso2.PNG)

## Paso 3

Seleccionar ***Connection Factory***. Luego, hacer clic en el botón ***Next***

![Git Paso 3](img/connetionPaso3.PNG)

## Paso 4

En el campo ***Name*** escribir el nombre de la conexion ***ConnectionFactory***

![Git Paso 4](img/connetionPaso4.PNG)
## Paso 5

En el campo ***Maximum Masseges per Session*** escribir 100. Luego, seleccionar ***XA Conection Factory Enabled***. Finalmente, hacer clic en el botón ***Next***. 

![Git Paso 5](img/connetionPaso5.PNG)
## Paso 6

En el campo ***Targets*** seleccionar el servidor ***AdminServer***. Luego, hacer clic en el botón ***Finish***.

![Git Paso 6](img/connetionPaso6.PNG)
## Paso 7

Si todo está bien configurado, deberá mostrar el siguiente mensaje:

![Git Paso 7](img/connetionPaso7.PNG)

