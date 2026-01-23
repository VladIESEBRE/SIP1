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

## Paso 9

 - Comprobamos que el ping al servidor funciona desde el cliente

   <img width="755" height="594" alt="Captura de pantalla de 2026-01-16 10-54-58" src="https://github.com/user-attachments/assets/ee903ed4-6263-442c-a463-99d749b8e07b" />

 - Hacemos un apt update e instalamos los paquetes libnss-ldap, libpam-ldap y nscd para permitir la autenticación de usuarios contra el servidor LDAP.

## Paso 10

 - Configuración del cliente LDAP
   
<img width="1019" height="633" alt="Captura de pantalla de 2026-01-16 11-57-22" src="https://github.com/user-attachments/assets/5d885ef9-344b-4856-a9be-7a2449ca4aad" />
<img width="1019" height="633" alt="Captura de pantalla de 2026-01-16 11-58-09" src="https://github.com/user-attachments/assets/92a6e655-db20-4df6-ae2f-12765512d72c" />
<img width="1019" height="633" alt="Captura de pantalla de 2026-01-16 11-58-49" src="https://github.com/user-attachments/assets/0ae6c560-40c8-4d12-8f8b-0a5c140aede2" />
<img width="1019" height="633" alt="Captura de pantalla de 2026-01-16 11-59-01" src="https://github.com/user-attachments/assets/bc8d2f19-4252-4523-962a-e30035428558" />
<img width="1019" height="633" alt="Captura de pantalla de 2026-01-16 11-59-08" src="https://github.com/user-attachments/assets/ec9df728-cba6-4660-adea-0ee3421bb148" />
<img width="1020" height="627" alt="Captura de pantalla de 2026-01-16 12-00-30" src="https://github.com/user-attachments/assets/b37146e8-41eb-4297-a1fd-9278bfd002f0" />
<img width="1016" height="627" alt="Captura de pantalla de 2026-01-16 12-09-17" src="https://github.com/user-attachments/assets/9fd21f7f-6351-47d4-a9d5-be97711e67c6" />

## Paso 11

 - Se modifica el archivo /etc/nsswitch.conf para incluir LDAP como origen de información para usuarios, grupos y contraseñas (passwd, group, shadow y gshadow), permitiendo la autenticación completa mediante el servidor LDAP.

<img width="1012" height="629" alt="Captura de pantalla de 2026-01-16 13-04-37" src="https://github.com/user-attachments/assets/4590a7d6-b9a1-4277-a95e-7f9ba8677c77" />

## Paso 12

 - Se modifica el archivo /etc/pam.d/common-session para crear automáticamente el directorio personal de los usuarios LDAP mediante el módulo pam_mkhomedir, garantizando el correcto inicio de sesión.

<img width="1014" height="632" alt="Captura de pantalla de 2026-01-16 13-09-13" src="https://github.com/user-attachments/assets/e17a84b2-8ebd-4499-a458-1ddf522d1aee" />

## Paso 13

 - Se modifica el archivo /etc/pam.d/common-password eliminando la opción use_authtok en los módulos LDAP para evitar conflictos en la gestión de contraseñas durante la autenticación.

   <img width="1011" height="626" alt="Captura de pantalla de 2026-01-16 13-11-23" src="https://github.com/user-attachments/assets/5b0b6d8b-a2e5-4340-9993-b7d9745fe0a5" />
   <img width="1004" height="627" alt="Captura de pantalla de 2026-01-16 13-13-14" src="https://github.com/user-attachments/assets/f6903d40-c16d-4129-a694-d60994db2dab" />

## Paso 14

 - Se configura el gestor de sesiones LightDM para permitir el inicio de sesión manual, posibilitando el acceso de usuarios LDAP que no aparecen en la lista de usuarios locales.

   <img width="1019" height="631" alt="Captura de pantalla de 2026-01-16 13-15-52" src="https://github.com/user-attachments/assets/85b4c556-df70-4f76-af3c-e78bf7e515b9" />

## Paso 15

 - Se comprueba la autenticación de un usuario LDAP iniciando sesión gráficamente en el cliente. Se verifica la identidad del usuario, la consulta al directorio LDAP y la creación automática del directorio personal.

   <img width="737" height="489" alt="imatge" src="https://github.com/user-attachments/assets/e6291725-63b8-4496-9276-0ba9b0b4298a" />
   <img width="733" height="595" alt="Captura de pantalla de 2026-01-20 13-32-10" src="https://github.com/user-attachments/assets/fa9e0871-4b3a-44a9-b8cb-af7429add27c" />


# Actividad
## Preparació prèvia
 - Fes un dpkg-reconfigure slapd al servidor per tal de deixar la base de dades buida i només amb el
domini i l’usuari admin creat. Comprova-ho amb un slapcat.

<img width="1124" height="679" alt="Captura de pantalla de 2026-01-23 11-45-19" src="https://github.com/user-attachments/assets/b7218f80-e251-4e81-8f1d-2f8748876b3c" />
 
 - Descarrega l'arxiu dades_pt10.ldif del moodle i amb la comanda ldapadd carrega els usuaris, grups i
uos (Compte que el domini és vesper.cat, hauràs de modificar-lo pel teu)

<img width="1120" height="552" alt="Captura de pantalla de 2026-01-23 11-49-26" src="https://github.com/user-attachments/assets/04aa4e58-e7e4-45dd-ad30-7c4cde0a5d41" />

 - Fes un altre slapcat per tal de comprovar que les dades s'han carregat correctament

   <img width="1135" height="683" alt="Captura de pantalla de 2026-01-23 11-50-23" src="https://github.com/user-attachments/assets/24562704-742a-415c-9d6a-06826b66dc9d" />

## 1. Crea un nou usuari directament al domini

<img width="735" height="321" alt="Captura de pantalla de 2026-01-23 11-55-23" src="https://github.com/user-attachments/assets/ce543b60-aa64-4908-b947-47333386f29f" />
<img width="990" height="253" alt="Captura de pantalla de 2026-01-23 11-56-39" src="https://github.com/user-attachments/assets/d78d11d8-272b-4498-a103-1160bdcea1cd" />

## 2. Crea una nova uo anomenada nòmines

<img width="798" height="143" alt="Captura de pantalla de 2026-01-23 11-58-57" src="https://github.com/user-attachments/assets/6bb91cdc-2bbe-4c3b-ba84-a0935079c3ac" />
<img width="1123" height="164" alt="Captura de pantalla de 2026-01-23 11-59-55" src="https://github.com/user-attachments/assets/741d0378-aeb5-45fe-8484-f6e471934b88" />

## 3. Mou l’usuari que has creat dintre de la uo nòmines

<img width="1264" height="124" alt="Captura de pantalla de 2026-01-23 12-05-02" src="https://github.com/user-attachments/assets/1063393a-3332-4a49-a978-0cdc80df39d5" />
<img width="817" height="684" alt="Captura de pantalla de 2026-01-23 12-04-28" src="https://github.com/user-attachments/assets/4fb72246-fba0-4ae8-a030-d08ec77a24e2" />

## 4. Quants grups hi ha al domini vesper.cat?
 - Hay 2 grupos (Informática y Departamentos).

<img width="985" height="545" alt="Captura de pantalla de 2026-01-23 12-11-30" src="https://github.com/user-attachments/assets/21086009-eaab-46ad-8f60-94a0ebbd845b" />

## 5. Afegeix l’usuari que has creat dintre d’un dels grups del domini

   <img width="819" height="144" alt="Captura de pantalla de 2026-01-23 12-19-13" src="https://github.com/user-attachments/assets/e9aeae86-0b65-4882-add7-eb356abfee78" />
<img width="1004" height="162" alt="Captura de pantalla de 2026-01-23 12-19-31" src="https://github.com/user-attachments/assets/9ca9d9ec-dfbb-4313-a48d-ce13814febf4" />
<img width="1003" height="520" alt="Captura de pantalla de 2026-01-23 12-22-26" src="https://github.com/user-attachments/assets/136f1bf7-487a-4ffa-b8ca-0a33c59ea76a" />

## 6. D’un sol cop: Afegeix un nou atribut opcional a l’usuari sergi, modifica el cognom de l’usuari sergi al valor Pallarés

<img width="721" height="200" alt="Captura de pantalla de 2026-01-23 12-32-03" src="https://github.com/user-attachments/assets/71f60d5c-4ea7-48bd-9fcb-47c165fc304b" />
<img width="1049" height="677" alt="Captura de pantalla de 2026-01-23 12-35-25" src="https://github.com/user-attachments/assets/b0e8b6ff-e06b-497f-bb15-728dbf846274" />

## 7. Quants usuaris hi ha dintre de la uo rrhh? Quins són?
 - Hay 3 usuarios: Xavier,Enric,Sergi 

<img width="1195" height="672" alt="imatge" src="https://github.com/user-attachments/assets/5658df16-9396-4369-9170-d1e38b1b9045" />








































