# Servidor WebLogic
A continuación se muestra el proceso de instalaci�n del servidor WebLogic 12c en su versión 12.1.3 para las plataformas Linux CentOS 6.5 (Ambiente de Producción) y Windows (Ambiente de Desarrollo)

En este [enlace](../install.md) encuentra la URL disponible para la descarga.

Para realizar la descarga se debe realizar clic en el link Generic que se muestra en la siguiente imagen. Esto descargará un jar (fmv_12.1.3.0.0_wls.jar) que contiene la distribución para todas las plataformas:

![Web Logic Download](../../img/wl/WebLogic.png)
 
## Instalación

Ir hasta el directorio de descarga del jar y ejecutar la siguiente línea de comando:
```
#!bat

java -jar fmw_12.1.3.0.0_wls.jar
```
Se abrirá la siguiente ventana:

![Weblogic 1st Step](../../img/wl/wl_1stp.png)

Dar clic en siguiente, seleccionar la ruta de instalación y dar clic en siguiente

![Weblogic 1st Step](../../img/wl/wl_2stp.png)

Seleccionar WebLogic Server y dar clic en siguiente

![Weblogic 1st Step](../../img/wl/wl_3stp.png)

Mostrará el resumen de la instalación. Dar clic en instalar:

![Weblogic 1st Step](../../img/wl/wl_4stp.png)

Al terminar la instalación preguntará si desea iniciar el asistente de configuracion. Este permitira crear un nuevo dominio. Se mostrara la siguiente pantalla:

![Weblogic 1st Step](../../img/wl/wl_5stp.png)

Seleccionar crear un nuevo dominio y dar clic en siguiente:

![Weblogic 1st Step](../../img/wl/wl_6stp.png)

Indicar el nombre de la cuenta de administrador y una contraseña válida. Dar clic en siguiente:

![Weblogic 1st Step](../../img/wl/wl_7stp.png)

Seleccionar modo de dominio de desarrollo y la ruta del JDK instalado. Dar clic en siguiente hasta llegar al resumen de la configuración.

![Weblogic 1st Step](../../img/wl/wl_8stp.png)

Seleccionar Crear para crear el dominio con dicha configuración

![Weblogic 1st Step](../../img/wl/wl_9stp.png)

Con esto queda finalizada la instalación del Servidor WebLogic. 

## Inicio y Finalización del servidor

Para iniciar el servidor se requiere ir a la ruta del Middleware indicada en la primera ventana de la instalación del servidor a traves de línea de comando.
Una vez en esta ruta:

```
#!bat

cd user_projects/domains/base_domain/bin
startWebLogic.cmd

```

Para pararlo basta con:

```
#!bat

cd user_projects/domains/base_domain/bin
stopWebLogic.cmd

```