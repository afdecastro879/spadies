# Servidor JMS
La creación del servidor JMS se debe realizar en el Servidor Weblogic destinado para el procesamiento de datos ingresando por la URL:
 
```
http://ip-servidor-core:7001/console/
```
## Paso 1

En el panel ***Domain Structure*** expanda ***Services*** y ***Messaging***. Luego seleccione ***JMS Servers***.

![Git Paso 1](img/jmsserverpaso1.PNG)

## Paso 2

En  ***JMS Servers*** dar clic en ***new***.

![Git Paso 2(img/jmsserverpaso2.PNG)

## Paso 3

En el campo ***Name*** escribir el nombre del servidor JMS ***JMSServer***.

![Git Paso 3](img/jmsserverpaso3.PNG)

## Paso 4

En  en el campo ***Persistence Store***  hacer clic en el boton ***Create a New Store***.

![Git Paso 4](img/jmsserverpaso4.PNG)
## Paso 5

En el campo ***Type*** seleccionar ***File Store*** y luego hacer clic en el botón **Next***.

![Git Paso 5](img/jmsserverpaso5.PNG)
## Paso 6

En el campo ***Name*** escribir el nombre del File Store ***FlleStoreJMS***. Luego  en el campo ***Directory*** escribir la siguiente ruta:
```
/u01/app/Middleware/oracle/user_projecdts/domains/base_domain
```

Finalmente, hacer clic en el botón ***OK***

![Git Paso 6](img/jmsserverpaso6.PNG)
## Paso 7

En el campo ***Persistent Store*** seleccionar ***FileStoreJMS*** y luego hacer clic en el botón ***Next***. 

![Git Paso 7](img/jmsserverpaso7.PNG)
## Paso 8

En el campo ***Tarjet*** seleccione ***AdminServer*** y luego hacer clic en el botón ***Finish***. 

![Git Paso 8](img/jmsserverpaso8.PNG)
## Paso 9

En la lista de ***JMS Server*** deberá aparecer el servidor JMS que se acaba de crear. 

![Git Paso 9](img/jmsserverpaso9.PNG)