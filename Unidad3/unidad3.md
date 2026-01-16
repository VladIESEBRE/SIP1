# Sprint 3: Gestió de Dominis i Accessos
# INSTAL·LACIÓ DOMINI LDAP I UNIR CLIENT AL DOMINI

### ¿Qué es un dominio?
Un dominio es un conjunto de equipos, usuarios y recursos que se administran de forma centralizada desde un servidor. Permite controlar accesos, permisos y autenticación de los usuarios.

### ¿Qué es LDAP?
LDAP (Lightweight Directory Access Protocol) es un protocolo que permite acceder y administrar un servicio de directorio donde se almacenan usuarios, grupos, equipos y políticas de seguridad.

### ¿Qué es un árbol en LDAP?
Un árbol LDAP es la estructura jerárquica donde se organiza la información del dominio. En él se encuentran los usuarios, grupos y recursos ordenados de forma lógica.

### ¿Para qué sirve un dominio con LDAP?

 - Centralizar usuarios y contraseñas

 - Gestionar permisos de acceso

 - Facilitar la administración de equipos

 - Aumentar la seguridad

## Paso 1
 - Crear la NAT Network
 
 - Esto permitirá que cliente y servidor se comuniquen sin problemas de IP.

   <img width="925" height="780" alt="Captura de pantalla de 2026-01-14 12-08-39" src="https://github.com/user-attachments/assets/056d5d75-3c59-496a-b442-330af478b717" />

## Paso 2
 - Configurar la red del Servidor y del cliente Ubuntu

<img width="881" height="549" alt="Captura de pantalla de 2026-01-14 12-09-18" src="https://github.com/user-attachments/assets/c11e5f20-b07a-4e12-9f12-b2e68e0b0934" />

<img width="884" height="548" alt="Captura de pantalla de 2026-01-14 12-20-32" src="https://github.com/user-attachments/assets/d934ff92-1504-4f9c-961e-3163df7183c9" />

## Paso 3
 - Comprobar la conexión entre cliente y servidor y configurar la red del servidor con direccionamiento IPv4 manual.

<img width="845" height="506" alt="Captura de pantalla de 2026-01-14 12-25-42" src="https://github.com/user-attachments/assets/1367e7ec-d796-494f-9d90-39ce9a85fc16" />

<img width="586" height="478" alt="Captura de pantalla de 2026-01-16 09-30-55" src="https://github.com/user-attachments/assets/f96c77ed-8631-4a4b-94b8-bfabfdd6f2db" />

## Paso 4
 
 - Configurar el nombre del equipo servidor modificando los archivos /etc/hostname y /etc/hosts

<img width="739" height="485" alt="Captura de pantalla de 2026-01-16 09-32-18" src="https://github.com/user-attachments/assets/c1f6267a-8a50-4538-bc56-2dbae90d4e98" />

<img width="743" height="482" alt="Captura de pantalla de 2026-01-16 09-42-40" src="https://github.com/user-attachments/assets/e53f3a27-6bf8-4c1f-ab2d-defec7f680a1" />

## Paso 5

 - Hacemos un apt update e instalamos slapd i ldap-utils.

<img width="709" height="27" alt="Captura de pantalla de 2026-01-16 09-52-36" src="https://github.com/user-attachments/assets/d5a1d314-e562-48ed-a39d-6771c7361364" />

<img width="739" height="485" alt="Captura de pantalla de 2026-01-16 09-50-49" src="https://github.com/user-attachments/assets/2d307597-79f5-4191-8f47-c4ac1225ccf3" />

 - Al escribir 'slapcat' podemos ver que LDAP no está configurado

<img width="745" height="484" alt="Captura de pantalla de 2026-01-16 09-54-05" src="https://github.com/user-attachments/assets/c1327994-1805-4fff-8ac1-5760a4d76082" />


## Paso 6

 - Se importan los ficheros LDIF necesarios para la creación de la estructura del directorio LDAP

<img width="740" height="482" alt="Captura de pantalla de 2026-01-16 10-03-23" src="https://github.com/user-attachments/assets/4a5db25b-30ef-4e84-ad14-f0196e09624b" />

 - Se reconfigura el servicio OpenLDAP mediante dpkg-reconfigure slapd, estableciendo el dominio gina.cat.

<img width="733" height="486" alt="Captura de pantalla de 2026-01-16 10-06-08" src="https://github.com/user-attachments/assets/a5299184-56cd-466e-8f48-6a8b18a7097c" />

<img width="737" height="484" alt="Captura de pantalla de 2026-01-16 10-07-10" src="https://github.com/user-attachments/assets/7d4b75ed-8af8-4376-8e86-b1e26c7b9e8a" />

<img width="738" height="481" alt="Captura de pantalla de 2026-01-16 10-07-53" src="https://github.com/user-attachments/assets/c4d7a3b3-c7c9-475b-9de1-91e835e5bf03" />

<img width="738" height="481" alt="Captura de pantalla de 2026-01-16 10-08-05" src="https://github.com/user-attachments/assets/d3f239a7-131d-4967-b9a1-745c0239964f" />

<img width="738" height="481" alt="Captura de pantalla de 2026-01-16 10-08-55" src="https://github.com/user-attachments/assets/82b7a3d4-d519-496a-9493-a790c49384a3" />

<img width="738" height="481" alt="Captura de pantalla de 2026-01-16 10-09-03" src="https://github.com/user-attachments/assets/b22565f3-aa80-4e59-841b-ef5edd65e360" />

 - Se verifica la correcta creación del árbol del directorio LDAP utilizando el comando slapcat.

<img width="796" height="520" alt="Captura de pantalla de 2026-01-16 10-09-45" src="https://github.com/user-attachments/assets/4aa55f0d-030a-4d76-9579-0e3815bc6c5d" />

## Paso 7

# Explicación del fichero `uo.ldif`

El fichero `uo.ldif` es un archivo en formato **LDIF (LDAP Data Interchange Format)** que se utiliza para crear una **Unidad Organizativa (OU)** dentro del directorio LDAP.  
En este caso, define una unidad organizativa destinada a almacenar los **usuarios** del dominio.

<img width="791" height="521" alt="Captura de pantalla de 2026-01-16 10-13-24" src="https://github.com/user-attachments/assets/644b8a05-06b6-441e-96a9-cd44f3a67266" />


### Explicación línea a línea

- `# Unitat organitzativa USERS`  
  Comentario informativo. No es procesado por LDAP y solo sirve como referencia para el administrador.

- `dn: ou=users,dc=miquel,dc=com`  
  Define el **Distinguished Name (DN)** del objeto, es decir, su ubicación dentro del árbol LDAP.  
  Indica que la unidad organizativa `users` se crea dentro del dominio `miquel.com`.

- `objectClass: organizationalUnit`  
  Especifica que el objeto creado es una **unidad organizativa**.

- `objectClass: top`  
  Clase base obligatoria en LDAP, de la que heredan todos los objetos del directorio.

- `ou: users`  
  Nombre de la unidad organizativa.


  - En el caso del dominio gina.cat, el fichero debe adaptarse para que el DN coincida con la estructura del directorio LDAP

    <img width="791" height="521" alt="Captura de pantalla de 2026-01-16 10-19-08" src="https://github.com/user-attachments/assets/c5a5277a-bc99-44c1-b5ab-5386510a61e4" />

 # Explicación del fichero `grup.ldif`

El fichero `grup.ldif` es un archivo **LDIF** que se utiliza para crear un **grupo LDAP** de tipo POSIX.  
Este tipo de grupo se usa habitualmente en sistemas Linux para gestionar permisos y pertenencia de usuarios.

<img width="791" height="512" alt="Captura de pantalla de 2026-01-16 10-21-58" src="https://github.com/user-attachments/assets/787858a1-fd1b-4cfc-bdcc-ecca4794c93b" />
 
  - Adaptación al dominio correcto

<img width="791" height="512" alt="Captura de pantalla de 2026-01-16 10-24-38" src="https://github.com/user-attachments/assets/f12b4c1c-7a0d-4be1-ba77-c8e71653b924" />


# Explicación del fichero `usu.ldif`

El fichero `usu.ldif` es un archivo **LDIF** que se utiliza para crear un **usuario LDAP**.  
Define un usuario compatible con sistemas Linux, incluyendo datos de identidad, grupo, directorio personal y políticas de contraseña.

<img width="790" height="519" alt="Captura de pantalla de 2026-01-16 10-26-18" src="https://github.com/user-attachments/assets/cd89ce38-7acb-4366-a47f-4db5d69d4595" />
 
  - Adaptación al dominio correcto

<img width="795" height="524" alt="Captura de pantalla de 2026-01-16 10-28-18" src="https://github.com/user-attachments/assets/fdc770a0-b088-4b0b-a2b6-e02cd5f3c6eb" />


## Paso 8 

 - Se importan los ficheros LDIF correspondientes a las unidades organizativas, grupos y usuarios mediante el comando ldapadd.

<img width="957" height="507" alt="Captura de pantalla de 2026-01-16 10-31-18" src="https://github.com/user-attachments/assets/0b1fdf22-338d-4062-8ceb-54db4e002605" />

 - Se comprueba el contenido del directorio LDAP mediante el comando slapcat, verificando la correcta creación del dominio dc=gina,dc=cat, la unidad organizativa users, el grupo alumnes y el usuario alu1, confirmando el correcto funcionamiento del servicio LDAP.

<img width="789" height="802" alt="Captura de pantalla de 2026-01-16 10-35-49" src="https://github.com/user-attachments/assets/2a5a239c-42ad-4245-8122-7330d2f51288" />

<img width="786" height="532" alt="Captura de pantalla de 2026-01-16 10-36-05" src="https://github.com/user-attachments/assets/a1812757-2ec3-4654-b423-9482eadd530e" />




























