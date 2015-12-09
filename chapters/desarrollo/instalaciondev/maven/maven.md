# Instalación de Maven
A continuación se presenta el procedimiento para la instalación de maven en linux CentOS 6.5 y Windows.

# Linux CentOS 6.5
Ejecutar por línea de comandos:

```
#!bash
sudo wget http://www.eu.apache.org/dist/maven/maven-3/3.3.3/binaries/apache-maven-3.3.3-bin.tar.gz  //Descargar el comprimido de maven
sudo gunzip apache-maven-3.3.3-bin.tar.gz       //Descomprimir el archivo
sudo tar -xvf apache-maven-3.3.3-bin.tar        //Descomprimir el .tar
sudo mv apache-maven-3.3.3/ /opt/maven          //Mover el directorio a la carpeta /opt/maven
sudo vi /etc/profile.d/maven.sh                 //Crear un archivo ejecutable de inicio. Escribir lo que sigue:
    #!/bin/bash
    MAVEN_HOME=/opt/maven                       //Variable MAVEN_HOME
    PATH=$MAVEN_HOME/bin:$PATH                  //Agregar la variable a PATH
    export PATH MAVEN_HOME                      //Registrar las variables de entorno
    export CLASSPATH=.
sudo chmod +x /etc/profile.d/maven.sh           //Brindar permisos de ejecución al archivo
sudo source /etc/profile.d/maven.sh             //Ejecutar el bash
sudo mvn -version                               //Verificar la versión de maven
echo $MAVEN_HOME                                //Verificar las variables de entorno
echo $PATH

```

# Windows
Descargar el zip de este [enlace](http://maven.apache.org/download.cgi) y descomprimirlo en un directorio conocido, preferiblemente C:/Archivos de Programa/apache-maven-3.3.3.
Agregar la carpeta `bin` a la variable `PATH` del usuario. Para esto, abrir propiedades del sistema (WinKey+Pause), seleccionar "Configuraci�n avanzada del sistema", "Variables de entorno", y luego agregar a la variable `PATH` el valor `C:/Archivos de Programa/apache-maven-3.3.3` separado por un ;

Abrir una ventana de comandos (WinKey+R) escribir `cmd` y correr `mvn -v` para verificar la instalación.