# Queue Destination

La creación de la Cola de Mensajería se debe realizar en el Servidor Weblogic destinado para el procesamiento de datos ingresando por la URL:

```
http://ip-servidor-core:7001/console/
```
## Paso 1

En el panel ***Domain Structure*** expanda ***Services*** y ***Messaging***. Luego seleccione ***JMS Modules***.

![Git Paso 1](img/queuepaso1.PNG)

## Paso 2

En ***JMS Modules*** hacer clic en el botón ***New***.

![Git Paso 2](img/queuepaso2.PNG)

## Paso 3

En  ***Summary of Resources*** hacer clice en el bóton ***new***.

![Git Paso 3](img/queuepaso3.PNG)

## Paso 4

Seleccionar ***Queue*** y hacer clic en el botón ***Next***.

![Git Paso 4](img/queuepaso4.PNG)

## Paso 5

En  en el campo ***Name***  escribir ***formatoQueue***. 
Luego en el campo ***JNDI Name*** escribir ***jms/formatoQueue***. Finalmente hacer clic en botón ***Next***

![Git Paso 5](img/queuepaso5.PNG)
## Paso 6

En el campo ***Subdeployments*** hacer clic en el botón ***Create a New Subdeployments***

![Git Paso 6](img/queuepaso6.PNG)
## Paso 7 
En el campo ***Subdeployments*** escribir ***formatoQueue***.

![Git Paso 7](img/queuepaso7.PNG)
## Paso 8

En el campo ***Tarjets*** seleccionar el Servidor JMS ***JMSServer***.

![Git Paso 8](img/queuepaso8.PNG)
## Paso 9

En ***Summary of Resources*** debe mostrar la cola de mensajería  con nombre formatoQueue. 

![Git Paso 9](img/queuepaso9.PNG)
## Paso 10

Repetir los pasos nuevamente para la creación de las colas coherencia y cruce. Estas colas deben tener la configuración que aparece en la imagen.

![Git Paso 10](img/queuepaso10.PNG)