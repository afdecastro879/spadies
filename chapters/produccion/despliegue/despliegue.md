# Despliegue de la Aplicación en WebLogic 12c #
## Descripción ##
Este capítulo contiene las instrucciones para realizar el despliegue del aplicativo de SPADIES a un servidor WebLogic 12c.
## Requisitos ##
1. Debe tener los archivos .WAR (FrontEnd) y .EAR (BackEnd) generados a partir del código de ambos proyectos.
## Instrucciones ##
1. Ingresar a la consola de WebLogic que se encuentra en la URL `http://<host>:7001/console`
2. Dirigirse a la vista de Despliegues en el menú `Estructura de Dominio` y hacer clic en el botón `Instalar`:
![001.PNG](https://bitbucket.org/repo/RpRKkd/images/2013536604-001.PNG)
3. En `Ruta de Acceso` seleccionar la ruta donde se encuentra el WAR/EAR:
![002.PNG](https://bitbucket.org/repo/RpRKkd/images/2943286910-002.PNG)
4. Hacer clic en `Siguiente`
![003.PNG](https://bitbucket.org/repo/RpRKkd/images/3509571425-003.PNG)
5. Hacer clic en `Terminar`
![004.PNG](https://bitbucket.org/repo/RpRKkd/images/3738827012-004.PNG)
6. Verificar que en la lista de despliegues se encuentra el WAR/EAR
7. Repetir el proceso para hacer el despliegue del EAR. 
## Acceso ##
Ingrese a la URL `http://<host>:7001/spadiesWeb` que lo redirigirá al dashboard de la aplicación.
![006.PNG](https://bitbucket.org/repo/RpRKkd/images/1527955748-006.PNG)