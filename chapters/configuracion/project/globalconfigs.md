# Configuraciones Globales de Jenkins
A continuación se presentan todas las configuraciones globales de Jenkins para que funcione como el servidor de integración contínua en el proyecto SPADIES 3.0.

## Instalación de Plugins
La siguiente es la lista de plugins necesaria:
+ Bitbucket Plugin
+ Email Extension Plugin
+ Git plugin
+ Maven Integration Plugin
+ SonarQube Plugin

Para la instalación de estos plugins es necesario ingresar a Jenkins > Administrar Jenkins > Administrar Plugins

![Paso 1](../../../img/project/jenkins_1stp.png)

![Paso 2](../../../img/project/jenkins_1stp.png)

Seleccionar la pestaña Todos los Plugins y a través de la barra de búsqueda seleccionar los plugins para la instalación. Dar clic en instalar ahora e instalar después de reiniciar.

## Configurar el sistema
Es necesaria la configuración de todas las variables de entorno y rutas que utilizará Jenkins. Para esto, es necesario ingresar a Jenkins > Administrar Jenkins > Configurar Sistema. A continuación se muestran los valores de la configuración para cada sección:

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