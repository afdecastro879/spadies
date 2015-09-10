# Enlace Bitbucket - Jenkins
A continuaci�n se presenta el procedimiento para enlazar Bitbucket con Jenkins, para permitir el proceso de integraci�n cont�nua a partir de un repositorio.

## Instalaci�n del Plugin de Bitbucket para Jenkins

En la p�gina principal de jenkins dar clic en Administrar Jenkins, luego Administrar Plugins. Dar clic en la pesta�a todos los plugins.

![Jenkins Paso 1](../../../img/jenkins/jenkins_1stp.png)

En la barra de b�squeda escribir Bitbucket Plugin, seleccionar el plugin correspondiente y hacer clic en Descargar ahora e instalar despu�s de reiniciar.

## Intercambio de llaves con bitbucket

Entrar a Bitbucket > Manage Account y en el grupo Security seleccionar SSH Keys.

![Jenkins Paso 2](../../../img/jenkins/jenkins_2stp.png)

Entrar a la m�quina donde se encuentra instalado jenkins y por l�nea de comando:

```
#!bash
su - jenkins
cat .ssh/id_rsa.pub             //Esto imprimir� la llave
```

Copiar la llave y dar clic en Add Key en Bitbucket Darle un nombre y copiar la llave.

## Configuraci�n del repositorio

Entrar al repositorio, Dar clic en Settings > Services

![Jenkins Paso 3](../../../img/jenkins/jenkins_3stp.png)

Agregar el servicio `POST` con <jenkins_host>:<jenkins_port>/bitbucket-hook.

Este servicio notificar� a jenkins por cada cambio que exista en el repositorio.

## Comprobar conecci�n SSH
Para comprobar que existe conecci�n SSH entre la m�quina que aloja jenkins y Bitbucket ejecutar por l�nea de comandos:
```
#!bash
ssh -T git@bitbucket.org
```

Si la conexi�n es correcta aparecer� un mensaje para agregar la m�quina Jenkins como un host conocido para Bitbucket. Seleccionar que S�.