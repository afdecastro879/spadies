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

En la línea correspondiente al rootPw pegar la contraseña, y modificar todos los dominios `dc=example,dc=co ` por `dc=spadies,dc=mineducacion,dc=gov,dc=co`.

``` 
#!vim

...

rootPW={SSHA}xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

...
```

Seguir el mismo procedimiento en los archivos `/etc/openldap/slapd.d/cn=config/olcDatabase={2}bdb.ldif` y `/etc/openldap/slapd.d/cn=config/olcDatabase={0}config.ldif`

## Adicion de entradas principales
Realizar todas las operaciones con usuarios con los permisos necesarios de root.

Crear un directorio temporal en `~` y crear el archivo root.ldif

```
#!bat

sudo mkdir ~/tmp

cd ~/tmp

sudo vi root.ldif
```

Escribir en el archivo la organización y la entrada para grupos y personas del Ldap:

```
#!vim

dn: dc=spadies,dc=mineducacion,dc=gov,dc=co

objectClass: dcObject

objectClass: organization

dc: spadies

o: spadies


dn: ou=groups,dc=spadies,dc=mineducacion,dc=gov,dc=co

ou: groups

objectClass: organizationalUnit


dn: ou=people,dc=spadies,dc=mineducacion,dc=gov,dc=co

ou: people

objectClass: organizationalUnit

```

Remover todo del directorio `/etc/openldap/slapd.d/` con el comando y luego agregar las entradas del arcivho root. La última línea permite probar que las entradas hayan sido agregadas correctamente.

```
#!bat

rm -rf /etc/openldap/slapd.d/*

slapadd -n 2 -l ~/tmp/root.ldif

slaptest -f /etc/openldap/slapd.conf -F /etc/openldap/slapd.d

```

Entregar los permisos a los directorios requeridos:

```
#!bat

chown -R ldap:ldap /var/lib/ldap

chown -R ldap:ldap /etc/openldap/slapd.d

```

Iniciar el servidor LDAP

```
#!bat

chkconfig --level 235 slapd on
    
service slapd start

```

## Creación del Esquema para los Usuarios SPADIES

Copiar el archivo spadies.schema en el directorio `/etc/ldap/schema/`. El archivo está disponible [aquí](openldap/spadies.schema) o vendrá adjunto a este documento.

Copiar el archivo spadies.conf al directorio temporal `~/tmp`. El archivo está disponible [aquí](openldap/spadies.conf) o vendrá adjunto a este documento.

Ejecutar el archivo .conf

```
#!bat

slaptest -f spadies.conf -F .

cn=config/cn=schema && vim cn={3}spadies.ldif

```

Se abrirá un archivo que tiene la configuración del esquema. Dejar unicamente los valores siguientes:

    + dn:
    + cn:
    + objectClass:
    + olcAttributeTypes:
    + olcObjectClasses:
    
Modificar los siguientes datos:

```
#!vim

dn: cn=spadiesPerson,cn=schema,cn=config

cn: spadiesPerson

```

Agregar la entrada del esquema y verificar que la entrada ha sido agregada:

```
#!bat

ldapadd -D cn=config -W -f ~/tmp/cn=config/cn=schema/cn={3}spadies.ldif

ldapsearch -xLLL -D cn=config -W -b cn=config cn=*spadiesPerson*

```

## Agregar grupos y usuario superadministrador del SPADIES

Copiar los archivos 
    + afgrp.ldif 
    + afgrp.ldif
    + sagrp.ldif
    + superadmin.ldif
    + superadmingrp.ldif
    + ufgrp.ldif
    + upgrp.ldif
    + utgrp.ldif
al directorio temporal `~/tmp`. Vendrán adjuntos a este documento o estarán en la carpeta `chapters/configuracion/openldap` de la wiki.

Ejecutar la siguiente línea para cada archivo del directorio. El archivo superadmin.ldif debe ser el último.

```
#!bat

ldapadd -x -W -D "cn=Manager,dc=spadies,dc=mineducacion,dc=gov,dc=co" -f <nombre-archivo>.ldif

```

Escribir la contraseña ingresada en la primera parte de este tutorial.