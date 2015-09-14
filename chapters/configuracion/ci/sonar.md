# Instalaci�n del servidor de SonarQube

A continuaci�n se presenta el procedimiento para la instalaci�n de SonarQube en linux CentOS 6.5

## Linux CentOS 6.5

Para la instalaci�n de SonarQube se requiere de una base de datos. Dentro del proceso de integraci�n continua para el proyecto SPADIES se utilizar� una base de datos MySQL para este fin.

### MySQL
Ejecutar a trav�s de l�nea de comandos:

```
#!bash
su                                          //Entrar como usuario root
yum install mysql-server                    //Instalaci�n del servidor de MySQL
/sbin/chkconfig mysqld on                   //Activar el servicio mysqld
service mysqld start                        //Dar inicio al servidor de MySQL
mysqladmin -u root password 'mypassword'    //Crear password para el usuario root de MySQL
adduser sonar                               //Agregar un usuario para sonar
passwd sonar                                //Agregar una contrase�a para el usuario sonar
```

### SonarQube
Ejecutar a trav�s de l�nea de comandos:

```
#!bash
sudo wget -O /etc/yum.repos.d/sonar.repo http://downloads.sourceforge.net/project/sonar-pkg/rpm/sonar.repo  //Agregar el repositorio de sonar
yum install sonar                           //Instalar sonar a trav�s de yum
```

### Crear Base de datos y usuarios para sonar
Es necesario generar las bases de datos y el usuario a trav�s del cual se conectar� sonarqube.
Para esto, se debe ingresar a la consola de mysql a trav�s de:
```
#!bash
mysql -u {mysql-user} -p {mysql-password}   // Para este caso particular entrar como root: mysql -u root -p mypassword
```

Una vez en la consola de mysql:
```
#!mysql
CREATE DATABASE sonar CHARACTER SET utf8 COLLATE utf8generalci;
CREATE USER 'sonar' IDENTIFIED BY 'sonar';
GRANT ALL ON sonar.* TO 'sonar'@'%' IDENTIFIED BY 'sonar';
GRANT ALL ON sonar.* TO 'sonar'@'localhost' IDENTIFIED BY 'sonar';
FLUSH PRIVILEGES;
```

### Configuraciones de sonar:
Una vez creada la Base de datos y el usuario en necesario acceder a la configuraci�n de sonar y agregar estos datos. Por defecto esta configuraci�n est� en `/opt/sonar/conf/conf.properties`

```
#!bash
vi /opt/sonar/conf/conf.properties
```

Descomentar las l�neas correspondientes. En este caso se tiene en cuenta que la base de datos y el usuario creado son los mismos que vienen por defecto en el archivo de configuraci�n:

```
#!bash
#----- Default SonarQube server
sonar.host.url=http://localhost:9000

#----- PostgreSQL
#sonar.jdbc.url=jdbc:postgresql://localhost/sonar

#----- MySQL
sonar.jdbc.url=jdbc:mysql://localhost:3306/sonar?useUnicode=true&amp;characterEncoding=utf8

#----- Oracle
#sonar.jdbc.url=jdbc:oracle:thin:@localhost/XE

#----- Microsoft SQLServer
#sonar.jdbc.url=jdbc:jtds:sqlserver://localhost/sonar;SelectMethod=Cursor

#----- Global database settings
sonar.jdbc.username=sonar
sonar.jdbc.password=sonar
```
### Asegurando Sonar

Se puede iniciar el servicio de sonar a trav�s de:

```
#!bash
sudo service sonar start
```

Una vez iniciado el servicio se deben configurar las opciones de seguridad:
+ Entrar a trav�s del browser a http://localhost:9000.
+ Iniciar sesi�n con la cuenta admin con contrase�a admin.
+ Cambiar la contrase�a entrando a �Administrator� > �My Account�
+ Desactivar el acceso an�nimo a trav�s de �Settings� > �Configuration� > �Security� seleccionando True en �Force user authentication�

### Instalaci�n de Sonar Runner
Para enviar un an�lisis de c�digo se requiere del SonarRunner. Para esto:

```
#!bash
cd /opt
sudo wget http://repo1.maven.org/maven2/org/codehaus/sonar/runner/sonar-runner-dist/2.2.2/sonar-runner-dist-2.2.2.zip   //Descargar sonar-runner
sudo unzip sonar-runner-dist-2.2.2.zip                  //Descomprimir el archivo descargado
sudo ln -s sonar-runner-2.2.2 sonar-runner              //Renombrar el fuente

//Crear un script para agregar las variables de entorno de sonar-runner al inicio del OS
sudo echo -e '#!/bin/bash\nexport SONAR_RUNNER_HOME=/opt/sonar-runner\nexport PATH=$PATH:$SONAR_RUNNER_HOME/bin' > /etc/profile.d/sonar-runner.sh

export SONAR_RUNNER_HOME=/opt/sonar-runner              //Exportar las variables de entorno para la sesi�n actual
export PATH=$PATH:$SONAR_RUNNER_HOME/bin

sonar-runner -v                                         //Probar la correcta instalaci�n del sonnar-runner
```

### Sonar con Maven
Para que sonar pueda ser llamado a trav�s de maven se requiere de agregar un profile a la configuraci�n de Maven:

```
#!bash
vi /opt/maven/settings.xml
    <profile>
        <id>sonar</id>
        <activation>
            <activeByDefault>true</activeByDefault>
        </activation>
        <properties>
            <sonar.jdbc.url>
              jdbc:mysql://localhost:3306/sonar?useUnicode=true&amp;characterEncoding=utf8
            </sonar.jdbc.url>
            <sonar.jdbc.username>sonar</sonar.jdbc.username>
            <sonar.jdbc.password>sonar</sonar.jdbc.password>
            <sonar.login>admin</sonar.login>
            <sonar.password>adminPassword</sonar.password>

            <sonar.host.url>
              http://localhost:9000
            </sonar.host.url>
        </properties>
    </profile>
```

