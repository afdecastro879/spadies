# Configuraciones Globales de Jenkins
A continuaci�n se presentan todas las configuraciones globales de Jenkins para que funcione como el servidor de integraci�n cont�na en el proyecto SPADIES 3.0.

## Instalaci�n de Plugins
La siguiente es la lista de plugins necesaria:
+ Bitbucket Plugin
+ Email Extension Plugin
+ Git plugin
+ Maven Integration Plugin
+ SonarQube Plugin

Para la instalaci�n de estos plugins es necesario ingresar a Jenkins > Administrar Jenkins > Administrar Plugins

![Paso 1](../../../img/project/jenkins_1stp.png)

![Paso 2](../../../img/project/jenkins_1stp.png)

Seleccionar la pesta�a Todos los Plugins y a trav�s de la barra de b�squeda seleccionar los plugins para la instalaci�n. Dar clic en instalar ahora e instalar despu�s de reiniciar.

## Configurar el sistema
Es necesaria la configuraci�n de todas las variables de entorno y rutas que utilizar� Jenkins. Para esto, es necesario ingresar a Jenkins > Administrar Jenkins > Configurar Sistema. A continuaci�n se muestran los valores de la configuraci�n para cada secci�n:

### JDK

![Paso 3](../../../img/project/jenkins_3stp.png)

### Git

![Paso 4](../../../img/project/jenkins_4stp.png)

### SonnarQube Runner

![Paso 5](../../../img/project/jenkins_5stp.png)

### Maven

![Paso 6](../../../img/project/jenkins_6stp.png)

### Jenkins Location

![Paso 7](../../../img/project/jenkins_7stp.png)

### Git Plugin

![Paso 8](../../../img/project/jenkins_8stp.png)

### Extended E-mail Notification

![Paso 9](../../../img/project/jenkins_9stp.png)

### SonarQube

![Paso 10](../../../img/project/jenkins_10stp.png)