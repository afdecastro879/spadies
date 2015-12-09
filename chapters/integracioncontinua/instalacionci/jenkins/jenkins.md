# Instalación de Jenkins
A continuación se presenta el procedimiento para la instalación de jenkins en linux CentOS 6.5

## Linux CentOS 6.5
Ejecutar por línea de comando:

```
#!bash
add user jenkins                            //Crear usuario que usará la aplicación
passwd jenkisn                              //Definir la contraseña para el usuario jenkins
sudo visudo                                 //Entrar al archivo de sudoers y agregar jenkins
    jenkins ALL=(ALL)       ALL
sudo yum install jenkins                    //Instalar Jenkins
sudo yum install java-1.8.0-openjdk         //Instalar el openjdk que es el que usa por defecto Jenkins
sudo yum install java-1.8.0-openjdk-devel
sudo iptables -I INPUT -p tcp -m tcp --dport 8080 -j ACCEPT     //Permitir peticiones de entrada en el puerto 8080
sudo service iptables save                  //Salvar la configuración del firewall
su - jenkins                                //Entrar como usuario jenkins
ssh-keygen                                  //Generar una llave. Seguir las instrucciones y dejarlo en la ubicación por defecto

```
