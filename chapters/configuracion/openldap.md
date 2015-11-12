# OpenLdap

A continuación se muestra el proceso de instalación de OpenLdap y sus dependecias para Linux Centos 6.5

## Instalación
CentOS 6.5 tiene incorporado por defecto OpenLdap, por lo cual, solo se requiere la instalación de los paquetes complementarios para el manejo del mismo a través de la consola de Linux.

Para la instalación de los paquetes ejecutar la siguiente línea por comando.

```
#!bat

sudo yum install openldap-servers openldap-clients
```

Editar el archivo de configuración principal del ldap:

```
#!bat

sudo vi /etc/openldap/ldap.conf
```

Una vez en el archivo modificar el dominio base:

```
#!vim

...

BASE dc=spadies,dc=mineducacion,dc=gov,dc=co

...
```

Cerrar el archivo
Copiar los archivos samples para nuestra configuración

```

#!bat

cp /usr/share/openldap-servers/slapd.conf.obsolete /etc/openldap/slapd.conf

cp /usr/share/openldap-servers/DB_CONFIG.example /var/lib/ldap/DB_CONFIG
```
Ejecutar la línea:

```
#!bat

slappasswd

```

Esto pedirá escribir una contraseña, que corresponderá con la contraseña para el usuario administrador del Ldap y arrojará un resultado como este:

```

{SSHA}xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

Copiar esta línea.
Abrir el archivo slapd.conf

```
#!bat

sudo vi /etc/openldap/slapd.conf
```

En la línea correspondiente al rootPw pegar la contraseña, y modificar todos los dominios ``` dc=example,dc=co ``` por ``` dc=spadies,dc=mineducacion,dc=gov,dc=co ```.

``` 
#!vim

...

rootPW={SSHA}xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

...
```

Modificar 
