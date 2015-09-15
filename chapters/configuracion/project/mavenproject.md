# Creaci�n de un proyecto Maven

Para la utilizaci�n de Jenkins crearemos un proyecto de tipo Maven en esta herramienta. Para esto se debe entrar al servidor de Jenkins > Nueva Tarea y se seleccionar Nuevo proyecto Maven.

![Paso 1](../../../img/mavenproject/mvnproject_1stp.png)

Posterior a esto, se deben definir las variables para el proyecto:

## Configurar el c�digo fuente
Permite determinar de donde se extraer� el c�digo fuente. En este caso ser� una fuente git. Se debe colocar la direcci�n del repositorio y las credenciales de acceso si este necesita autenticaci�n.

![Paso 2](../../../img/mavenproject/mvnproject_2stp.png)

## Disparadores de ejecuciones
Permite definir en qu� momento se dispara una ejecuci�n. En este caso cuando se cree un SNAPSHOT y cuando haya alg�n cambio en el repositorio.

![Paso 3](../../../img/mavenproject/mvnproject_3stp.png)

## *Pipeline*
En esta secci�n se pueden definir pasos anteriores y posteriores a la ejecuci�n de la primera instrucci�n de Maven. En este caso, se define el fichero ra�z y la primera opcion es ejecutar `sonar:sonar` que es la instrucci�n maven para solicitar un an�lisis de c�digo a sonar.
El paso posterior es ejecutar la tarea `maven install` que ejecutar� todos los pasos de ejecuci�n de pruebas, compilaci�n empaquetado y despliegue autom�tico.

![Paso 4](../../../img/mavenproject/mvnproject_4stp.png)

## Acciones posteriores
En esta secci�n se pueden definir acciones que se ejecuten despu�s del *pipeline* definido. Para este caso, deseamos correr una notificaci�n por email, por lo que seleccionamos A�adir Acci�n > Editable Email Notification

![Paso 5](../../../img/mavenproject/mvnproject_5stp.png)

Finalmente se guardan estas configuraciones y ya queda el proyecto maven listo para ser ejecutado por nuestro servidor de integraci�n cont�nua.