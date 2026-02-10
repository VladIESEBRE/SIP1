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
<img width="1122" height="563" alt="Captura de pantalla de 2026-01-23 12-47-16" src="https://github.com/user-attachments/assets/7274f39e-738b-47e5-a8b2-2f29e9ae478f" />


## 2. Crea una nova uo anomenada nòmines

<img width="798" height="143" alt="Captura de pantalla de 2026-01-23 11-58-57" src="https://github.com/user-attachments/assets/6bb91cdc-2bbe-4c3b-ba84-a0935079c3ac" />
<img width="1123" height="164" alt="Captura de pantalla de 2026-01-23 11-59-55" src="https://github.com/user-attachments/assets/741d0378-aeb5-45fe-8484-f6e471934b88" />
<img width="1115" height="560" alt="Captura de pantalla de 2026-01-23 12-45-13" src="https://github.com/user-attachments/assets/34142980-7e30-4af8-ad27-11727279a463" />


## 3. Mou l’usuari que has creat dintre de la uo nòmines

<img width="1264" height="124" alt="Captura de pantalla de 2026-01-23 12-05-02" src="https://github.com/user-attachments/assets/1063393a-3332-4a49-a978-0cdc80df39d5" />
<img width="817" height="684" alt="Captura de pantalla de 2026-01-23 12-04-28" src="https://github.com/user-attachments/assets/4fb72246-fba0-4ae8-a030-d08ec77a24e2" />

## 4. Quants grups hi ha al domini vesper.cat?
 - Hay 2 grupos (Informática y Administración).

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

## 8. Esborra el gidNumber del grup informàtica
 - No se puede borrar gidNumber ya que es obligatorio para la clase de objeto posixGroup

<img width="1111" height="145" alt="Captura de pantalla de 2026-01-23 12-52-02" src="https://github.com/user-attachments/assets/d824bef6-ce88-44ce-896e-a20984029b60" />
<img width="1108" height="212" alt="Captura de pantalla de 2026-01-23 12-53-15" src="https://github.com/user-attachments/assets/ec2faead-abf4-440c-9166-33119bb96cc8" />

## 9. Quantes uos hi ha al domini vesper.cat?
 - Hay 3 uos (rrhh,departaments,nomines)
<img width="1118" height="563" alt="Captura de pantalla de 2026-01-23 12-57-27" src="https://github.com/user-attachments/assets/eec58ae9-49b2-414f-93a5-5058fb433d13" />

## 10. Modifica el cn de Xavier per Francesc Xavier

<img width="1274" height="674" alt="Captura de pantalla de 2026-01-23 13-01-37" src="https://github.com/user-attachments/assets/8ae0cfe9-e38f-4228-88c8-7ec01dab76df" />

## 11. Esborra la uo nòmines

<img width="1258" height="633" alt="Captura de pantalla de 2026-01-23 13-05-38" src="https://github.com/user-attachments/assets/6de41428-c939-4dc7-b88d-c824670490a4" />

## 12. Mostra els usuaris que tinguin com a grup principal el grup administració
 - Primero miramos que GID tine el grupo administración en el archivo original: gidNumber: 1002. Tenemos que buscar usuarios con el gidNumber=1002.

<img width="861" height="803" alt="Captura de pantalla de 2026-01-23 13-08-56" src="https://github.com/user-attachments/assets/727db1cf-2b2b-4158-8d37-c29d9acf2adc" />

## 13. Quin usuari té el uidNumber 1003?
 - No hay usuarios con el uidNumber 1003

 <img width="865" height="524" alt="Captura de pantalla de 2026-01-23 13-12-15" src="https://github.com/user-attachments/assets/68c6bdd3-567f-4a12-9b68-c69808b66501" />

## 14. Mostra quins són els usuaris on el seu cognom comenci per R i el seu uidNumber sigui més gran que 1003

<img width="950" height="338" alt="Captura de pantalla de 2026-01-23 13-14-59" src="https://github.com/user-attachments/assets/f5dde81e-f8a1-4fa8-b7c7-af69dfa50cfa" />

## 15. Mostra quins usuaris formen part del grup informàtica o aquells usuaris que tinguis de cognom Pallarés

 - "No se puede realizar en una sola consulta de usuario porque la objectClass posixGroup guarda a los miembros dentro del objeto de grupo (mediante el atributo memberUid) y no dentro del objeto de usuario. Por lo tanto, he extraído primero los nombres del grupo 'informatica' (xavier, enric) y después he aplicado un filtro lógico combinando ambas condiciones: (|(uid=xavier)(uid=enric)(sn=Pallarés))."

### Paso 1 ( Identificar los miembros del grupo informàtica)

<img width="931" height="480" alt="Captura de pantalla de 2026-01-23 13-19-31" src="https://github.com/user-attachments/assets/d1e346c3-ed04-4be0-9dcd-557bd57ce5a1" />

### Paso 2 ( Identificar los miembros con el apellido Pallarés )

<img width="852" height="414" alt="Captura de pantalla de 2026-01-23 13-21-21" src="https://github.com/user-attachments/assets/f1acc082-0996-4eb5-880b-62dbe74edbd1" />


### Paso 3 ( Identificar los miembros del grupo informàtica)

<img width="1333" height="810" alt="Captura de pantalla de 2026-01-23 13-27-19" src="https://github.com/user-attachments/assets/9c70564e-b77b-4a5a-a21d-5faa07ea7b71" />

# Servidor Samba y servidor NFS

 - Para la gestión de archivos en red, existen dos estándares principales dependiendo de tu sistema operativo. Samba es la herramienta universal diseñada para la interoperabilidad, permitiendo que equipos Linux compartan carpetas e impresoras con sistemas Windows de forma transparente. Es la opción ideal para hogares o oficinas con redes mixtas, basando su seguridad en el acceso por usuario y contraseña.

Por otro lado, NFS (Network File System) es el protocolo nativo del mundo Unix/Linux. Su gran ventaja es la eficiencia; al ser más ligero que Samba, ofrece una velocidad de transferencia muy superior cuando se comunican dos máquinas Linux entre sí. Es el estándar utilizado en servidores y laboratorios educativos, ya que permite montar carpetas remotas como si fuesen discos duros locales con un impacto mínimo en el rendimiento del sistema.

## Parte servidor Samba: 

### Paso 1 ( Istalar Samba)

<img width="937" height="194" alt="Captura de pantalla de 2026-01-27 11-37-39" src="https://github.com/user-attachments/assets/9146f3ac-221a-4372-b0c3-cddf38f3d5b5" />
<img width="939" height="555" alt="Captura de pantalla de 2026-01-27 11-38-28" src="https://github.com/user-attachments/assets/fb09f80f-f57b-4115-b96c-47bc8fa7208c" />


### Paso 2 ( Preparación)
 - Se creó el directorio /proves, al cual se le asignaron permisos totales (777) y se cambió su propiedad al usuario nobody:nogroup.

<img width="939" height="555" alt="Captura de pantalla de 2026-01-27 11-41-31" src="https://github.com/user-attachments/assets/1734c9ba-caf8-4c8d-87b3-968946e2f978" />

 - Se crearon los usuarios blau, roig y groc utilizando el comando useradd -M -s /sbin/nologin y se vincularon dichos usuarios al servicio mediante smbpasswd -a, estableciendo las contraseñas necesarias para que puedan acceder a las carpetas compartidas desde otros equipos
<img width="939" height="555" alt="Captura de pantalla de 2026-01-27 11-44-24" src="https://github.com/user-attachments/assets/5fa7f6bd-df08-432b-b6d3-5d1475a74b53" />

 - Se creó un grupo de sistema denominado colors. Posteriormente, se añadieron los usuarios roig y groc a dicho grupo

<img width="939" height="555" alt="Captura de pantalla de 2026-01-27 11-45-40" src="https://github.com/user-attachments/assets/fcb3499f-b00d-4e03-8ebc-d288179db7cf" />

 - Este esquema permite un control granular donde diferentes usuarios tienen distintos niveles de privilegio sobre la misma carpeta compartida.
<img width="939" height="555" alt="Captura de pantalla de 2026-01-27 11-49-28" src="https://github.com/user-attachments/assets/784a5ad2-bae6-48c6-9a62-d1990867ed73" />

 - Siempre que hacemos cambios reiniciamos el servidor. Tiene que salir en verde al hacer status.
   
<img width="939" height="555" alt="Captura de pantalla de 2026-01-27 11-50-34" src="https://github.com/user-attachments/assets/9bdbc524-1cff-4706-902c-ebb8f67af725" />
<img width="939" height="555" alt="Captura de pantalla de 2026-01-27 11-51-04" src="https://github.com/user-attachments/assets/4a0d0c2f-8c58-409a-9f32-8e194694ab6e" />

## Parte cliente Samba:
 - Instalamos smbclient
   
<img width="729" height="475" alt="Captura de pantalla de 2026-01-27 11-55-42" src="https://github.com/user-attachments/assets/60045dc6-e2db-4a73-8be6-202f10e90b7e" />

### Comprobamos 

 - Anonim/Guest puede entrar y crear ficheros
<img width="940" height="738" alt="Captura de pantalla de 2026-01-27 11-59-53" src="https://github.com/user-attachments/assets/506ce078-271b-4e87-afed-1a31c54be88b" />
<img width="953" height="744" alt="Captura de pantalla de 2026-01-27 12-01-54" src="https://github.com/user-attachments/assets/de8bf345-77bc-4de5-af68-65e1184f7ce8" />

 - Blau puede entrar y crear ficgheros
<img width="953" height="744" alt="Captura de pantalla de 2026-01-27 12-03-44" src="https://github.com/user-attachments/assets/626cdba6-2db2-47ed-a619-2f6490868836" />
<img width="953" height="744" alt="Captura de pantalla de 2026-01-27 12-04-25" src="https://github.com/user-attachments/assets/943e30d2-9a1f-424e-9eac-e5c10dc2ea6b" />

 - Roig no puede entrar
<img width="953" height="744" alt="Captura de pantalla de 2026-01-27 12-05-21" src="https://github.com/user-attachments/assets/2e161142-d329-4a8a-8a9a-2f034d8e38a3" />
<img width="953" height="744" alt="Captura de pantalla de 2026-01-27 12-07-00" src="https://github.com/user-attachments/assets/c91400f1-fef8-4c74-8025-4c06c8213bb9" />

 - Groc no puede crear ficheros
<img width="953" height="744" alt="Captura de pantalla de 2026-01-27 12-06-25" src="https://github.com/user-attachments/assets/4e951d62-bd4c-4afc-9769-cc1f87864bfc" />
<img width="953" height="744" alt="Captura de pantalla de 2026-01-27 12-06-35" src="https://github.com/user-attachments/assets/a2fe593f-1b53-4fd3-9e1c-3c160ce8084d" />

 - Si quitamos guest solucionamos el problema del acceso de roig.

<img width="1125" height="711" alt="Captura de pantalla de 2026-01-27 12-13-31" src="https://github.com/user-attachments/assets/d299773d-3b5b-4ceb-b261-3a98784df126" />

 # ACTIVITAD
 
 ## Configuración de un servidor de archivos Samba con autenticación mediante directorio LDAP en Ubuntu Server
 
 ### Paso 1 ( SERVER )
 - Instalación de paquetes necesarios
<img width="830" height="27" alt="Captura de pantalla de 2026-02-10 20-38-55" src="https://github.com/user-attachments/assets/4e835ae4-dfe0-4b4d-ac05-ded431fc86c6" />

 ### Paso 2 
 - Configuración del cliente LDAP (nslcd)
   <img width="859" height="534" alt="Captura de pantalla de 2026-02-10 20-36-09" src="https://github.com/user-attachments/assets/7aeb0800-c31a-403a-87a6-ad5ca894a01f" />
   <img width="846" height="541" alt="Captura de pantalla de 2026-02-10 20-36-46" src="https://github.com/user-attachments/assets/58245247-223e-4bac-bd43-bd2601936c3c" />
   <img width="850" height="541" alt="Captura de pantalla de 2026-02-10 20-37-56" src="https://github.com/user-attachments/assets/f8ec4970-4172-42d8-9c07-7f9a03e6dbdc" />

 ### Paso 3 
  - Integración con el sistema (Name Service Switch). Editamos el archivo /etc/nsswitch.conf. Añadimos la palabra ldap al final de las líneas passwd, group y shadow.
<img width="837" height="539" alt="Captura de pantalla de 2026-02-10 20-39-47" src="https://github.com/user-attachments/assets/6c952c31-84f3-4b76-9056-ff704ba1dc06" />
    
 ### Paso 4 (Configuración de Samba.)
  - workgroup = GINA: Define el nombre del dominio.
  - passdb backend = ldapsam:ldap://127.0.0.1: Le dice a Samba que no guarde las contraseñas en un archivo de texto, sino que se conecte a la base de datos LDAP local para verificar a los usuarios.
  - ldap suffix y admin dn: Indican dónde buscar los usuarios dentro del directorio.
    
<img width="893" height="768" alt="Captura de pantalla de 2026-02-10 20-43-53" src="https://github.com/user-attachments/assets/d94d0212-3adf-4d19-b501-575c149004e7" />

 ### Paso 5 
 - Reinicio de servicios
   <img width="739" height="28" alt="Captura de pantalla de 2026-02-10 20-47-01" src="https://github.com/user-attachments/assets/f8498bf0-8778-4c6f-bed9-03a2c77160dc" />

### Paso 6
 - Creación y activación de usuario de prueba. Creamos un usuario llamado provesamba en el sistema. Al tener libnss-ldapd configurado, este usuario se integra correctamente. Usamos smbpasswd -a provesamba para habilitarlo en Samba y asignarle una contraseña de red.
<img width="630" height="116" alt="Captura de pantalla de 2026-02-10 21-03-46" src="https://github.com/user-attachments/assets/ddb95c83-f160-466f-9b94-04d6c14cd4d6" />

### Paso 7 
 - Comprobación desde el Cliente
   
   <img width="602" height="432" alt="Captura de pantalla de 2026-02-10 20-59-23" src="https://github.com/user-attachments/assets/2aad67ca-cd12-48f9-bd8e-f968865e1550" />
   
   <img width="1114" height="671" alt="Captura de pantalla de 2026-02-10 20-59-33" src="https://github.com/user-attachments/assets/47649b72-3856-4f6e-9e0f-155186a13dc8" />


#NFS COMpratir la carpeta compartida, ex1 q la carpeta se cree en el servidor no en el client

### Paso 1 ( SERVER )
 - Instalamos nfs-kernerl-server y comprobamos que funciona
   
<img width="733" height="474" alt="Captura de pantalla de 2026-02-06 11-46-23" src="https://github.com/user-attachments/assets/f0cd8629-cbc4-4932-b65b-ff61c8e91996" />
<img width="733" height="474" alt="Captura de pantalla de 2026-02-06 11-47-55" src="https://github.com/user-attachments/assets/b093b0b1-11c6-4fa1-8343-f07f084fa703" />

### Paso 2 
 - Creamos una carpeta "provesnfs", le damos permisos y comprobamos

<img width="733" height="474" alt="Captura de pantalla de 2026-02-06 11-49-16" src="https://github.com/user-attachments/assets/4d418373-5db5-49d1-a5b0-30d7ca638755" />

### Paso 3 
 - Añadidimos la línea necesaria en /etc/exports para compartir el directorio /provesnfs con cualquier cliente (*) con permisos de lectura y escritura. Reiniciamos el servidor.
<img width="733" height="474" alt="Captura de pantalla de 2026-02-06 11-51-58" src="https://github.com/user-attachments/assets/043f6b90-34b1-4c1e-9db5-980cb65a7efa" />
<img width="733" height="474" alt="Captura de pantalla de 2026-02-06 11-53-08" src="https://github.com/user-attachments/assets/6d3cb2db-79bd-4f6d-8ffe-89fb06de7e84" />

### Paso 4 ( CLIENT)
 - Instalamos paquetes
<img width="811" height="82" alt="Captura de pantalla de 2026-02-06 12-01-50" src="https://github.com/user-attachments/assets/7a6a97c0-2df9-4ac0-888f-df7bc2a52944" />

### Paso 5 ( )
 - Creamos una carpeta "divendres" y le damos permisos 
<img width="817" height="511" alt="Captura de pantalla de 2026-02-06 12-02-51" src="https://github.com/user-attachments/assets/9f9faccc-1198-4f1a-ae7d-3fcac1d6c4aa" />

### Paso 6 ( )
 - Configuramos el archivo /etc/fstab para que la carpeta compartida de NFS se monte automáticamente al arrancar el sistema.
<img width="934" height="631" alt="Captura de pantalla de 2026-02-06 12-08-17" src="https://github.com/user-attachments/assets/36b9b93b-d568-42a7-86b0-ac9624d46373" />

 ### Paso 7 ( )
 <img width="740" height="491" alt="Captura de pantalla de 2026-02-06 12-13-11" src="https://github.com/user-attachments/assets/674b2bab-1393-4b06-9499-17c2448e7e20" />
<img width="738" height="484" alt="Captura de pantalla de 2026-02-06 12-13-52" src="https://github.com/user-attachments/assets/65384957-89ac-4d1a-a103-0023aba2ec9d" />

 ### Paso 1 ( )

 <img width="938" height="683" alt="Captura de pantalla de 2026-02-06 12-24-40" src="https://github.com/user-attachments/assets/2aab21f5-f45e-4e20-a2c8-5afb106d152e" />

 ### Paso 2 ( )
 <img width="743" height="487" alt="Captura de pantalla de 2026-02-06 12-26-54" src="https://github.com/user-attachments/assets/2e0959a0-7b75-4383-a619-ac869289a9c0" />
 ### Paso 3 ( )
 <img width="939" height="594" alt="Captura de pantalla de 2026-02-06 12-27-54" src="https://github.com/user-attachments/assets/12724c66-adea-4fef-86e5-aeff5e46e8f9" />
 <img width="704" height="35" alt="Captura de pantalla de 2026-02-06 12-28-30" src="https://github.com/user-attachments/assets/39d6d3f6-638d-4c80-974c-be441827621f" />

 ### Paso 4 ( )
 <img width="744" height="479" alt="Captura de pantalla de 2026-02-06 12-36-27" src="https://github.com/user-attachments/assets/5eae3b6c-5041-4f37-bd1c-1dc637f56e18" />
<img width="744" height="479" alt="Captura de pantalla de 2026-02-06 12-36-33" src="https://github.com/user-attachments/assets/7a5cb746-ba2e-435e-b69b-fd0e1a8f8408" />

 ### Paso 5 ( )
 <img width="748" height="490" alt="Captura de pantalla de 2026-02-06 13-06-57" src="https://github.com/user-attachments/assets/85033d00-fada-4888-bd17-1f6e4667691d" />


