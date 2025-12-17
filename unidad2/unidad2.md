# Sprint 2: Gestió de la Informació del Sistema i Administració
## Sistemes de fitxers i particions
### Mida del sector
 - Un sector es la unidad física mínima donde un disco puede leer o escribir datos.Su tamaño no se puede modificar porque depende del hardware del disco. Tradicionalmente 512 bytes por sector era el estándar, actualmente muchos discos modernos usan 4.096 bytes , pero también pueden emular 512 bytes para compatibilidad.El sistema operativo organiza los datos basándose en esta unidad mínima, si quieres guardar un archivo de 1 byte, el disco igual usa un sector completo.

### Mida del block
 - Un bloque es la unidad mínima lógica que utiliza el sistema operativo para guardar y gestionar los datos dentro de una partición. Mientras que el sector es una unidad física fija del disco, el bloque es una unidad lógica definida por el sistema de archivos (ext4, NTFS, FAT32, etc.). El tamaño habitual del bloque normalmente es de 4096 bytes. Este tamaño si que se puede modificar cuando formateas una partición y eliges el sistema de archivos.Si un archivo ocupa 1 byte, igualmente utilizará un bloque completo por eso si trabajas con archivos grandes, bloques más grandes pueden dar mejor rendimiento. Si tienes muchos archivos pequeños, conviene usar bloques pequeños para no desperdiciar espacio.

### Fragmentació interna 
 - La fragmentación interna es todo el espacio del disco que se desperdicia dentro de un bloque porque no se utiliza completamente. Si un archivo ocupa 1 byte, igualmente utilizará un bloque completo(4096 bytes) por eso si trabajas con archivos grandes, bloques más grandes pueden dar mejor rendimiento. Si hay muchos archivos pequeños, es mejor usar bloques pequeños para no desperdiciar espacio.

### Fragmentació externa 
  - La fragmentación externa se produce cuando, a medida que el sistema operativo crea, modifica y elimina archivos, estos dejan de guardarse en bloques contiguos del disco.
Como consecuencia, el archivo queda dividido en varias partes separadas y el disco debe acceder a distintos puntos físicos para leerlo, lo que provoca una disminución del rendimiento.En Windows existe el desfragmentador de disco, que reorganiza los datos para mejorar la continuidad de los bloques. En Linux, normalmente no es necesaria la desfragmentación porque sus sistemas de archivos (como ext4) están diseñados para minimizar este problema.


 ## Demonstración 
 
 ### 1.

 - Aquí podemos ver que cada sector lógico mide 512 bytes y cada sector físico real del disco también es de 512 bytes.
   
    <img width="743" height="491" alt="Captura de pantalla de 2025-10-31 11-55-03" src="https://github.com/user-attachments/assets/176f8cb0-743d-434b-a2ab-d974b7ac8d98" />
 ### 2.

 - El comando que sí sirve para ver el tamaño de bloque es: "tune2fs -l /dev/sdb1 | grep Block". Podemos ver que es de 4096 bytes.
   
 <img width="742" height="501" alt="Captura de pantalla de 2025-10-31 11-58-35" src="https://github.com/user-attachments/assets/44b761fe-87d9-4c5c-acc9-6d769a42321d" />

 ### 3.

 - Creamos un archivo llamado div.text con el contenido: "Per fi divendres"
 - Comprobamos el tamaño real del archivo mediante el comando "du -b div.text"
 - El 17 significa que 17 bytes es el tamaño real del contenido del archivo(cada carácter ocupa 1 byte y la frase tiene 17 caracteres).
 - "du -sh div.text" nos muestra el tamaño ocupado en disco. Aunque el archivo solo contiene 17 bytes,ocupa 4 KB reales en el disco.
 - El sistema de archivos ext4 usa bloques de 4096 bytes (4 KB).Aunque el archivo tenga 1, 10 o 17 bytes, siempre ocupará mínimo 1 bloque = 4 KB.


<img width="742" height="501" alt="Captura de pantalla de 2025-10-31 12-01-36" src="https://github.com/user-attachments/assets/f95e0125-2dd2-45d2-840b-8fe66047c6e2" />

 ### 4.
 - La herramienta e4defrag muestra que la partición /dev/sda1 tiene el fragmentation score a 0, por lo que no necesita desfragmentación.
Aunque hay algunos archivos del sistema (sobre todo en /var/log) con varios fragmentos. Siguen el sistema  now/best, 13/1 por ejemplo quiere decir que el 13 es el número de fragmentos actuales del archivo y el 1 es el número óptimo si estuviera completamente contiguo (normalmente 1).

 <img width="742" height="501" alt="Captura de pantalla de 2025-10-31 12-17-23" src="https://github.com/user-attachments/assets/d53dc9cd-df48-4695-bc74-ef0d722113f1" />

 ### 5.
 - El comando "e4defrag /dev/sda1" analiza y desfragmenta la partición /dev/sda1. Reorganiza los bloques de los archivos para que estén contiguos, minimizando la fragmentación externa y mejorando el rendimiento.
   
   <img width="737" height="490" alt="Captura de pantalla de 2025-10-31 12-19-17" src="https://github.com/user-attachments/assets/f5227d50-958d-4db9-9be2-bac8d2b767d5" />

## Tipos de sistemas de archivos

#### FAT32 (Windows)
 - Acceso: Compatible con Windows, Linux, macOS, consolas, cámaras, etc.
 - Tamaño de bloques: Normalmente 4 KB (dependiendo del tamaño del disco).
 - Tamaño máximo de archivo: 4 GB (límite más problemático).
 - Nombre de archivos: Hasta 255 caracteres, compatible con UTF-8.
 - Rendimiento: Bueno en dispositivos pequeños, pero limitado para discos grandes.
 - Uso típico: Pendrives, tarjetas SD.

#### NTFS (Windows y Linux)
 - Acceso: Windows: lectura y escritura total. Linux: lectura y escritura mediante ntfs-3g.
 - Tamaño de bloques: Normalmente 4 KB.
 - Tamaño máximo de archivo: Hasta 16 TB o más.
 - Nombre de archivos: Hasta 255 caracteres.
 - Rendimiento: Muy bueno para sistemas Windows; gestiona bien archivos grandes.
 - Uso típico: Partición principal de Windows, discos internos.

#### EXT4 (Linux)

 - Acceso: Linux: lectura y escritura.Windows: lectura/escritura solo con programas especiales (no nativo).
 - Tamaño de bloques: Normalmente 4 KB (configurable a 1024, 2048 o 4096).
 - Tamaño máximo de archivo: Hasta 16 TB.
 - Nombre de archivos: Hasta 255 caracteres.
 - Rendimiento: Excelente, muy poca fragmentación, fiable y rápido.
 - Uso típico: Particiones de Linux.

#### Otros  
 - exFAT: Muy bueno en memorias externas y discos grandes.
 - XFS: muy rápido para archivos grandes (servidores).
 - Btrfs: snapshots, compresión, RAID integrado.
 - APFS: sistema de archivos moderno de Apple.

## Tipos de formateo 

##### Formateo de alto nivel

 - Es el que se realiza desde el sistema operativo cuando seleccionamos “formato rápido”. No borra realmente los archivos, solo elimina la información del sistema de archivos. Los datos siguen físicamente en el disco y pueden recuperarse con programas como Recuva. Es muy rápido porque no revisa el contenido del disco.

##### Formateo de nivel medio

 - Similar al formateo de alto nivel, pero además comprueba si existen sectores defectuosos y los marca para no volver a usarlos. Es más lento porque hace esta verificación adicional. A nivel de borrado, se comporta igual que el alto nivel (no elimina completamente los archivos).

##### Formateo de bajo nivel

 - Es el formateo que sobrescribe todos los sectores del disco, eliminando cualquier dato sin posibilidad de recuperación. Borra absolutamente todo y devuelve el disco a un estado vacío.

#### Particiones / Volúmenes
 
 - Una partición es una división del disco a nivel físico. Un volumen es una capa de abstracción que se coloca por encima de las particiones físicas.
 - Los volúmenes permiten unir el espacio libre de varias particiones o discos y gestionarlo como si fuese una sola unidad.  
 
 ### 1. Añadir disco virtual.
  - En VirtualBox añadí un nuevo disco virtual de 10 GB (archivo Ubuntu clona_2.vdi).
  
   <img width="875" height="533" alt="Captura de pantalla de 2025-10-31 12-41-48" src="https://github.com/user-attachments/assets/32acfc5e-1114-419c-89b7-fa8021062e3d" />

 ### 2. Comprobación
 - Comprobamos que el sistema lo detecta como /dev/sdc.
    <img width="731" height="478" alt="Captura de pantalla de 2025-10-31 12-55-18" src="https://github.com/user-attachments/assets/a981e6e3-c0e3-400d-8d84-a2b4e7af01c6" />

 ### 3. Instalamos Gparted
 - GParted (GNOME Partition Editor) es un programa gráfico para gestionar particiones del disco. En este caso ya está instalado.
   
<img width="731" height="478" alt="Captura de pantalla de 2025-10-31 12-49-33" src="https://github.com/user-attachments/assets/11860273-1388-4241-8b27-1cebb0b75a70" />

 ### 4. Crear y comprobar particiones
  - Creamos una partición de 4,8GB en /sdc1 y 5,2GB en /sdc2
    <img width="731" height="478" alt="Captura de pantalla de 2025-10-31 12-57-13" src="https://github.com/user-attachments/assets/22adbf6b-a73e-4f75-a9ce-b3bbfce321f0" />
    <img width="731" height="478" alt="Captura de pantalla de 2025-10-31 12-58-02" src="https://github.com/user-attachments/assets/170824b7-2dbb-4389-97de-7138e68c6e47" />
    <img width="731" height="478" alt="Captura de pantalla de 2025-10-31 12-58-53" src="https://github.com/user-attachments/assets/20dedf64-56b2-43ab-b983-2f0e19749d0d" />
 
 ### 5. Formatear una partición 
 - En esta captura se formatea la partición /dev/sdc1 usando el comando "mkfs.ext4 -b 2048". De esta forma se consigue un tamaño de bloque distinto al valor por defecto (4096 bytes).
 
  <img width="742" height="480" alt="Captura de pantalla de 2025-11-14 13-21-03" src="https://github.com/user-attachments/assets/c3847f18-7fa3-470f-b335-eb26b7bb1062" />


 ### 6. Comprobación
 - Podemos ver que el block size ha cambiado a 2048.
   
<img width="737" height="485" alt="Captura de pantalla de 2025-11-19 09-06-00" src="https://github.com/user-attachments/assets/a6565ad2-37a0-4fd7-bac0-2450c5b2713f" />

 ### 7. Formatear la segunda partición en NTFS desde GParted
  - Formatear como NTFS significa crear un sistema de archivos NTFS en una partición, eliminando la estructura anterior y preparándola para almacenar datos con el formato utilizado por Windows.
  - Al final en "/sdc2" podemos ver que aparece en verde y que pone NTFS.
    
    <img width="1144" height="663" alt="Captura de pantalla de 2025-10-31 13-02-42" src="https://github.com/user-attachments/assets/bbad731d-54f7-4281-b552-a6b70e4ec580" />
    <img width="1144" height="663" alt="Captura de pantalla de 2025-10-31 13-03-41" src="https://github.com/user-attachments/assets/cd476d04-a15c-461e-b9db-43d9ffeb4738" />
    <img width="780" height="548" alt="Captura de pantalla de 2025-11-19 09-16-11" src="https://github.com/user-attachments/assets/b931459e-5643-4c7a-8e44-70e2dd8a953c" />

 ## Montaje y configuración en fstab
 
 ### 1. Crear un directorio donde montar la partición
  - Ese directorio será el punto de montaje.
    
 <img width="740" height="487" alt="Captura de pantalla de 2025-10-31 13-16-22" src="https://github.com/user-attachments/assets/776a2099-3555-46c9-9906-9f076ecc4df1" />

 ### 2. Intentar crear un archivo antes de montar la partición
  - Eso significa que aún NO está montada la partición, solo estás escribiendo en el directorio vacío /mnt/particio1.

  <img width="740" height="487" alt="Captura de pantalla de 2025-10-31 13-19-44" src="https://github.com/user-attachments/assets/1bf898a6-d972-4ba7-946a-4d23134b3d8e" />

 ### 3. Montar la partición EXT4 en ese directorio
 - Despues de introducir el comando "mount -t ext4 /dev/sdb1 /mnt/particio1/" ,/mnt/particio1 ya no es un directorio vacío, ahora contiene el sistema de archivos real de /dev/sdb1.
 - Por eso después, al hacer "ls" ves "lost+found+prova+timeshift".Esto demuestra que la partición está montada correctamente.

   <img width="740" height="487" alt="Captura de pantalla de 2025-10-31 13-21-05" src="https://github.com/user-attachments/assets/26df6852-57a2-45f8-b3ae-130787919908" />

 ### 4. Editar el archivo /etc/fstab
 - Hemos añadido una linea al final. Esto significa que la partición /dev/sdb1 se montará automáticamente en /mnt/particio1, usando sistema de archivos EXT4 y con permisos de lectura/escritura
 - Esto hace que el montaje sea permanente, incluso después de reiniciar.
   
<img width="740" height="487" alt="Captura de pantalla de 2025-10-31 13-24-20" src="https://github.com/user-attachments/assets/41b0ca66-0851-424d-ada1-ef00990e7b36" />

 ### 5. Comprobar que funciona
  - Confirmación de que la partición está correctamente montada.

    <img width="740" height="487" alt="Captura de pantalla de 2025-10-31 13-28-46" src="https://github.com/user-attachments/assets/f815066d-5519-447d-a284-f4d8df92c863" />

 # Gestió d'usuaris, grups i permisos

 ## Fitxers implicats
 
 ### 1. passwd
 - Este archivo almacena información básica de cada usuario, no contiene contraseñas.
 - "vlad" es el nombre del usuario,	la contraseña	"x" significa que la contraseña está en /etc/shadow, 1000	UID	es el User ID (identificador del usuario), 1000	GID	es el Group ID del grupo principal del usuario (En Linux, cada nuevo usuario tiene un grupo propio con el mismo número).

 <img width="927" height="595" alt="Captura de pantalla de 2025-11-04 11-48-53" src="https://github.com/user-attachments/assets/688e0882-69b3-4303-8470-4d17a64dbd36" />

### 2. Group
 - Es el archivo donde Linux guarda todos los grupos del sistema y qué usuarios pertenecen a cada grupo.
 - Cada línea tiene: nombre del grupo, contraseña (x), GID y usuarios miembros.
   
   <img width="927" height="595" alt="Captura de pantalla de 2025-11-04 11-50-34" src="https://github.com/user-attachments/assets/d847381f-6d7b-4f8a-9135-4f030eafc9c8" />

### 3. Shadow
 - Es donde Linux guarda las contraseñas cifradas, la información de expiración de la contraseña y los datos de seguridad de cada usuario.
 - El 0:99999:7::: del final significa: el mínimo de días antes de poder cambiar la contraseña, el máximo de días antes de expirar y los días de aviso antes de expirar.
   
<img width="927" height="595" alt="Captura de pantalla de 2025-11-04 11-51-08" src="https://github.com/user-attachments/assets/50f43b73-2526-41ec-943c-6d42e16d097e" />


### 4. Gshadow
 - Es donde Linux guarda contraseñas de los grupos, administradores de cada grupo y miembros de cada grupo. Este archivo es la versión segura de /etc/group.
 - Cada línea tiene 4 campos: "adm: * ::syslog,vlad" --> nombre del grupo(adm), contraseña( * ), lista de administradores (vacio en este caso) y lista de usuarios(syslog,vlad).
 - A diferencia de /etc/group, este archivo solo puede ser leído por root y muestra quién administra cada grupo.
   
<img width="736" height="488" alt="Captura de pantalla de 2025-11-21 10-36-52" src="https://github.com/user-attachments/assets/a4a3f8fb-71ae-4f7f-8676-a1d2ad844246" />

 ## Comandes bàsiques 

 ### 1. Crear usuario con adduser
  - Cuando creamos un usuario con useradd, el sistema solo añade la entrada del usuario en /etc/passwd, /etc/group, /etc/shadow y /etc/gshadow. La carpeta /home/usuario no se crea hasta que el usuario inicia sesión por primera vez. Al iniciar sesión, Linux crea automáticamente las carpetas: Documents, Downloads, Desktop, etc.

#### Paso 1

  - Creamos usuario con "sudo adduser gina".
    
    <img width="1101" height="675" alt="Captura de pantalla de 2025-11-25 19-35-50" src="https://github.com/user-attachments/assets/ab3c7d7e-8e67-4bef-baf0-5b58ecc2eab4" />

#### Paso 2

  - Comprobamos el /home. No aparecen carpetas personales (Documentos, Música, etc.) todavía.

  <img width="1086" height="665" alt="Captura de pantalla de 2025-11-25 19-40-06" src="https://github.com/user-attachments/assets/86ba114d-0c7f-4458-aa3a-ae38e38f331b" />

#### Paso 3

  - Iniciamos sesión como Gina y comprabamos otra vez /home. Podemos encontrar el resto de las carpetas ahora.

<img width="1107" height="578" alt="Captura de pantalla de 2025-11-25 19-41-49" src="https://github.com/user-attachments/assets/fbaa646b-9c44-473a-b1f1-e43fb67b0513" />
<img width="740" height="491" alt="Captura de pantalla de 2025-11-25 19-44-27" src="https://github.com/user-attachments/assets/c6aa2e7f-7ccc-41f8-bd98-dcf390a1fdfc" />

#### Paso 4
  - Si lo queremos borrar escribimos "sudo deluser --remove-home gina"

    <img width="741" height="479" alt="Captura de pantalla de 2025-11-25 20-01-34" src="https://github.com/user-attachments/assets/5ba70d40-30ca-4aea-b2e7-c16c50ca8804" />


### 2. Crear usuario con useradd

#### Paso 1
  
  - A diferencia de adduser , useradd no es interactivo, no crea la carpeta /home (a menos que uses -m),no pide contraseña (hay que usar passwd después) y necesitas crear permisos tú mismo. Es más difícil, pero más flexible
  - Se puede crear usuario de forma rápida con "sudo useradd vesper -m -s /bin/bash" o de forma larga "sudo useradd vesper -s /bin/bash". Lo voy a hacer de forma larga.
  - 1.Crear usuario sin home -sudo useradd vesper -s /bin/bash
  - 2.Crear su carpeta /home -sudo mkdir /home/vesper
  - 3.Darle permisos correctos al usuario -sudo chown vesper:vesper /home/vesper

    <img width="924" height="489" alt="Captura de pantalla de 2025-11-25 20-23-51" src="https://github.com/user-attachments/assets/1b95807c-b821-491f-94b7-aa1d7b7b0acd" />


#### Paso 2

- Asignar contraseña al usuario -grep vesper /etc/passwd
- Comprobar passwd, group y shadow

<img width="924" height="489" alt="Captura de pantalla de 2025-11-25 20-26-54" src="https://github.com/user-attachments/assets/5e062544-fffb-4fcb-bc16-2694d76f2252" />

#### Paso 3

  - Iniciamos sesión en vesper3 y comprobamos que han aparecido las carpetas en /home 

  <img width="742" height="486" alt="Captura de pantalla de 2025-11-25 20-39-56" src="https://github.com/user-attachments/assets/2d7c93ba-6a3d-4e47-8a38-ecebe340f793" />


#### Paso 4

  - Podemos modificar el usuario. Le podemos cambiar el shell, bloquear (aparece "!" en shadow) o desbloquear.
    
  <img width="740" height="485" alt="Captura de pantalla de 2025-11-25 21-02-35" src="https://github.com/user-attachments/assets/f7240980-f78f-4894-bf19-6dd9ba90795e" />

#### Paso 5

 - Podemos crear un grupo (test en este caso ) y añadir usuarios (vesper3 en este caso) o eliminarlo del grupo
 - Tambien podemos ver que si el grupo tiene usuarios dentro, no se puede borrar.
  
<img width="743" height="481" alt="Captura de pantalla de 2025-11-25 21-05-17" src="https://github.com/user-attachments/assets/e283f484-bfcf-4b02-9b34-75603e6627ec" />
<img width="745" height="488" alt="Captura de pantalla de 2025-11-25 21-38-05" src="https://github.com/user-attachments/assets/c17bcb64-5c5c-401b-a6d2-4ee90a0c96a1" />
<img width="746" height="488" alt="Captura de pantalla de 2025-11-07 11-58-28" src="https://github.com/user-attachments/assets/c8365345-3ee2-4106-af4e-ce0382656323" />
<img width="746" height="488" alt="Captura de pantalla de 2025-11-07 12-06-10" src="https://github.com/user-attachments/assets/2b6205c1-4436-4ee0-855a-a280f738de34" />

#### Paso 6

  - Podemos borrar solo el usuario con "sudo userdel vesper" o el usuario y la carpeta /home con "sudo userdel -r vesper"

<img width="741" height="485" alt="Captura de pantalla de 2025-11-25 21-12-45" src="https://github.com/user-attachments/assets/32c04e0d-1f76-4bc8-840a-98320ff4c984" />

### 3.Ver el contenido de /etc/skel

  - El directorio skel tiene 3 ficheros ocultos para todos los usuarios. Todo lo q hay en esta carpeta aparece para todos los usuarios.
  - Si creamos acces_directe y fitxer_compartit y despues creamos un nuevo usuario (prova5) e iniciamos sesión, podemos ver que los ficheros que hemos creado están ahí.

<img width="746" height="488" alt="Captura de pantalla de 2025-11-07 12-11-06" src="https://github.com/user-attachments/assets/28c9d96a-4334-4766-b10e-bdb1c491ea65" />
<img width="1008" height="735" alt="Captura de pantalla de 2025-11-07 12-23-25" src="https://github.com/user-attachments/assets/3ff775d3-8da0-4d66-8fc0-bcee2c0a79e5" />


 ## Personalització de comandes

### 1. Editar /etc/adduser.conf

  - Activar LETTERHOMES que crea un directorio con la primera letra del usuario en el /home al crear un usuario nuevo.

    <img width="739" height="486" alt="Captura de pantalla de 2025-11-25 22-01-44" src="https://github.com/user-attachments/assets/4e746ca4-200f-44c8-ba31-f6c4a0bd76d7" />
    <img width="739" height="486" alt="Captura de pantalla de 2025-11-25 22-04-12" src="https://github.com/user-attachments/assets/04cd76c3-05c7-4227-98d0-897aab67da4b" />

### 2. Editar /etc/useradd.conf

   - Cambiar EXPIRE date global. Todos los usuarios nuevos creados con useradd tendrán fecha de expiración.

<img width="739" height="486" alt="Captura de pantalla de 2025-11-25 22-11-11" src="https://github.com/user-attachments/assets/45ac04ca-af02-44d8-9d17-242c41b8c73c" />
<img width="739" height="486" alt="Captura de pantalla de 2025-11-25 22-12-56" src="https://github.com/user-attachments/assets/db316a31-6544-4f53-bf05-1c79b94e0303" />

### 3. Editar /etc/login.defs

  - Cambiar el número mínimo de días entre cambios de contraseña de 0 a 5.

    <img width="746" height="492" alt="Captura de pantalla de 2025-11-25 22-19-52" src="https://github.com/user-attachments/assets/91effcfa-ec15-4f37-884b-437038508bd4" />
    <img width="746" height="492" alt="Captura de pantalla de 2025-11-25 22-23-03" src="https://github.com/user-attachments/assets/0a776017-8df5-427e-8ec9-1e2d4acb9065" />


### 4. Editar /etc/skel/.profile

  - Mensaje de bienvenida con fecha y hora.

    <img width="741" height="485" alt="Captura de pantalla de 2025-11-25 22-30-21" src="https://github.com/user-attachments/assets/f81d6178-8c44-440b-960c-93d809e4326d" />
    <img width="741" height="485" alt="Captura de pantalla de 2025-11-25 22-32-44" src="https://github.com/user-attachments/assets/79b8552e-2c59-4db7-9398-1788ca137917" />

### 5. Editar /etc/skel/.bashrc

   - Crear un alias personalizado

  <img width="741" height="485" alt="Captura de pantalla de 2025-11-25 22-37-08" src="https://github.com/user-attachments/assets/4713b2b9-d97e-4cd2-9442-813169719479" />
  <img width="741" height="485" alt="Captura de pantalla de 2025-11-25 22-39-28" src="https://github.com/user-attachments/assets/030a6e08-2bdc-46d4-a14a-01c9b0cc62ee" />



### 4. Editar /etc/skel/.bash_logout

  - Mensaje al cerrar sesión

    <img width="742" height="480" alt="Captura de pantalla de 2025-11-27 21-26-23" src="https://github.com/user-attachments/assets/f5070bc8-80e9-4ba3-952c-58ac64093dfd" />
    <img width="742" height="480" alt="Captura de pantalla de 2025-11-27 21-27-35" src="https://github.com/user-attachments/assets/7f18a7cb-710e-4a04-985b-0ed65b4cb667" />




### 4. Sesión TTY (modo consola)

  - Estamos en un terminal TTY, no en GNOME. Esto pasa cuando pulsas Ctrl + Alt + F3 o arrancas sin entorno gráfico.
  - Hemos iniciado sesión como prova10. Su directorio HOME está en /var/prova10 (porque lo cambiamos en adduser.conf). En la segunda foto podemos ver que todo lo que editamos en /etc/skel se copió correctamente. El usuario prova10 heredó los archivos .bashrc, .bash_logou y  .profile .
  - En la tercera foto creamos un archivo hola dentro de imagenes y en la cuarta lo revisamos en GNOME.
 
 <img width="1279" height="775" alt="Captura de pantalla de 2025-11-07 12-42-56" src="https://github.com/user-attachments/assets/da092b2d-1d0b-45f7-b575-774760f9d3e5" />
<img width="1281" height="842" alt="Captura de pantalla de 2025-11-07 12-47-38" src="https://github.com/user-attachments/assets/92f3a3ea-a780-49a0-a69e-8e13e4d6c5e9" />
<img width="1281" height="842" alt="Captura de pantalla de 2025-11-07 12-54-06" src="https://github.com/user-attachments/assets/e6a86131-3e07-41c5-861f-77d0bf01fe0c" />

 ## Gestión de permisos
 
En Linux, los permisos controlan quién puede acceder a archivos y directorios. Se basan en el modelo **UGO**, que distingue entre:

- **U (User)** → usuario propietario  
- **G (Group)** → grupo  
- **O (Others)** → otros usuarios  

### Permisos básicos

Los permisos básicos son:

- **r (read)**: permite leer el contenido.
- **w (write)**: permite modificar el contenido.
- **x (execute)**: permite ejecutar un archivo o acceder a un directorio.

Estos permisos pueden representarse de forma **simbólica** (`rwx`) o **numérica**.

### Gestión de permisos y propietarios

- **chmod**: modifica los permisos de archivos y directorios.
- **chown**: cambia el propietario.
- **chgrp**: cambia el grupo propietario.

La **umask** define los permisos por defecto al crear archivos y carpetas, restando permisos a los valores base:
- **666** para archivos
- **777** para directorios

Existen permisos especiales como el **sticky bit**, el **SUID** y el **SGID**, que aportan un control adicional en situaciones concretas.

Por último, las **ACL (Access Control Lists)** permiten asignar permisos más detallados a usuarios o grupos específicos, más allá del sistema tradicional UGO.

---

### Tipo de archivo

La **primera letra** de los permisos indica el tipo de archivo:

- `-` → archivo normal
- `d` → directorio
- `l` → enlace simbólico

### Ejemplo práctico

- **prova** empieza por `-` → es un archivo
- **prova2** empieza por `d` → es un directorio

---

### Estructura de los permisos

Después del primer carácter aparecen **9 letras**, divididas en **3 bloques de 3**: rwx r-x r--
Corresponden a:
- Usuario
- Grupo
- Otros

Si una letra **no aparece**, significa que ese permiso **no está concedido**.

### Significado en directorios
En los directorios, el permiso **x** significa **poder entrar** en la carpeta.

---

### Análisis de permisos en los ejemplos

### Archivo `prova` (`rw-r--r--`)

- **Usuario** (`rw-`):
  - `r` → puede leer
  - `w` → puede modificar
  - `x` → no puede ejecutar
- **Grupo** (`r--`): solo lectura
- **Otros** (`r--`): solo lectura

---

### Directorio `prova2` (`rwxr-xr-x`)

- **Usuario** (`rwx`): puede ver, entrar y crear o borrar archivos.
- **Grupo** (`r-x`): puede ver y entrar, pero no crear ni borrar archivos.
- **Otros** (`r-x`): puede ver y entrar, pero no crear ni borrar archivos.




 <img width="746" height="493" alt="Captura de pantalla de 2025-12-09 11-43-58" src="https://github.com/user-attachments/assets/55a4014e-19ad-4048-8598-f6a903235680" />


 ### Paso 1
 
 - Creamos 4 usuarios(roig, verd,groc y blau),añadimos los usuarios roig y blau al grupo parchis q hemos creado.

<img width="746" height="493" alt="Captura de pantalla de 2025-12-09 11-46-33" src="https://github.com/user-attachments/assets/a108e2eb-e565-48e8-8258-16803862d43c" />

 ### Paso 2
 
 - Vamos a "/var" y hacemos una carpeta llamada "compartida".

 <img width="746" height="493" alt="Captura de pantalla de 2025-12-09 11-47-54" src="https://github.com/user-attachments/assets/c769a530-0fb6-4403-8842-712084abfdac" />

 ### Paso 3

 - Utilizamos el comando chown para cambiar el propietario de la carpeta y chgrp para modificar el grupo propietario.

<img width="746" height="493" alt="Captura de pantalla de 2025-12-09 11-52-21" src="https://github.com/user-attachments/assets/dd472021-f692-464b-a44c-d483afca02e3" />

 
 ### Paso 4

 - En el directorio compartida, hemos quitado los permisos de acceso usando tres métodos distintos con chmod:
 - Forma numérica (octal) "chmod 750 compartida"
 - Forma simbólica quitando permisos a otros "chmod o=--- compartida"
 - Forma simbólica quitando solo el permiso de ejecución "chmod o-r,o-x compartida" o equivalente "chmod o-rx compartida".Al quitar la x, los usuarios no pueden entrar en la carpeta.

<img width="736" height="485" alt="Captura de pantalla de 2025-12-09 11-55-44" src="https://github.com/user-attachments/assets/03f37b7a-ba7d-4f90-adcf-595403397cfa" />

 
 ### Paso 5
 
 - Comprobamos que groc tiene todos los permisos,entramos y creamos una carpeta.

<img width="736" height="485" alt="Captura de pantalla de 2025-12-09 11-56-50" src="https://github.com/user-attachments/assets/44a3aa2b-1723-4653-97c8-21f416ad3855" />
 
 ### Paso 6

 - Comprobamos que el usuario groc no puede crear o borrar ficheros.

<img width="736" height="485" alt="Captura de pantalla de 2025-12-09 11-58-36" src="https://github.com/user-attachments/assets/e08a035a-05d0-43eb-adb8-f3917bee6f5b" />

 ### Paso 7
 
 - Comprobamos que el usuario verd no tiene ningun permiso.

<img width="736" height="485" alt="Captura de pantalla de 2025-12-09 12-00-00" src="https://github.com/user-attachments/assets/c9592f62-cc1b-4120-a540-587bdde2fb26" />

 
 ## PERMISOS ESPECIALES

 - Creamos un nuevo usuario llamado "morat"
 - Mediante setfacl hemos asignado permisos completos al usuario morat y lo hemos hemos verificado mediante el comando getfacl; el símbolo + confirma que existen ACL activas y que el usuario tiene permisos efectivos.
 - En la segunda foto comprobamos que "morat" tiene los permisos.

 <img width="732" height="481" alt="Captura de pantalla de 2025-12-09 12-06-28" src="https://github.com/user-attachments/assets/adc60ccd-3260-4b34-86f9-a62ce597c439" />

<img width="732" height="481" alt="Captura de pantalla de 2025-12-09 12-08-09" src="https://github.com/user-attachments/assets/14ccdbb6-f946-4dce-91e2-17023b67230e" />


 ### Paso 8
 - Denegamos al usuario roig permisos y comprobamos 
 <img width="741" height="483" alt="Captura de pantalla de 2025-12-09 12-10-24" src="https://github.com/user-attachments/assets/ea5232e1-85b7-4618-8289-1bd44090cf5e" />
 <img width="741" height="483" alt="Captura de pantalla de 2025-12-09 12-10-57" src="https://github.com/user-attachments/assets/73472222-205d-4c75-9938-332edd7b8e11" />


 ### Paso 9

 - Con setfacl -b se han eliminado todas las excepciones ACL, restaurando únicamente los permisos estándar UGO del directorio.

<img width="741" height="490" alt="Captura de pantalla de 2025-12-09 12-12-40" src="https://github.com/user-attachments/assets/84b72e7a-ce9e-4fc8-a493-9ffbebc1eac4" />

 
 ### Paso 10

 - Cambiamos el propietario y el grupo del directorio a root y concedimos permisos completos a todos los usuarios mediante chmod 777.
 <img width="741" height="490" alt="Captura de pantalla de 2025-12-09 12-14-17" src="https://github.com/user-attachments/assets/a838eea1-a5ab-4dd6-8cb0-39b4c45e2625" />

 ### Paso 11

 - Al conceder permisos 777, cualquier usuario puede acceder al directorio y borrar archivos aunque no sean de su propiedad, como se comprueba con el usuario blau.

 <img width="741" height="490" alt="Captura de pantalla de 2025-12-09 12-16-05" src="https://github.com/user-attachments/assets/f52ca467-9a95-410a-a755-91c9af73625a" />

 ### Paso 12

 - Para evitar que los usuarios borren archivos ajenos en una carpeta compartida, se ha activado el sticky bit mediante chmod o+t o chmod 1777.

<img width="741" height="490" alt="Captura de pantalla de 2025-12-09 12-19-45" src="https://github.com/user-attachments/assets/42113733-b9bc-4f7d-b409-fc159af03b69" />


 ### Paso 10

  - Con el sticky bit activado, los usuarios pueden crear archivos en la carpeta compartida, pero solo pueden borrar los que son de su propiedad, como se comprueba con el usuario verd.


 <img width="741" height="490" alt="Captura de pantalla de 2025-12-09 12-21-41" src="https://github.com/user-attachments/assets/f91fbb5e-0093-4dc3-98f4-08df00a1a4ef" />

# Copias de Seguridad y Automatización


## 1. Teoría de las copias de seguridad

### ¿Qué es una copia de seguridad?
Una **copia de seguridad** es una duplicación de datos que se realiza con el objetivo de **proteger la información** y poder recuperarla en caso de pérdida, fallo del sistema, errores humanos, ataques o averías de hardware.

---

### Tipos de copias de seguridad

| Tipo | Definición | Ventajas | Inconvenientes |
|-----|-----------|----------|----------------|
| **Completa** | Copia todos los datos seleccionados en cada ejecución | Es la más segura y fácil de restaurar | Es lenta y ocupa mucho espacio |
| **Diferencial** | Copia solo los cambios desde la última copia completa | Más rápida y ocupa menos que la completa | El tamaño aumenta con el tiempo |
| **Incremental** | Copia solo los cambios desde la última copia realizada | Muy rápida y ocupa muy poco espacio | Restauración más compleja |

---

### Diferencia entre copia de seguridad, imagen de sistema e instantáneas

- **Copia de seguridad**  
  Guarda archivos y carpetas concretas para poder recuperarlos de forma individual.

- **Imagen de sistema**  
  Es una copia exacta de todo el sistema (sistema operativo, programas y datos).  
  Permite restaurar el equipo completo en caso de fallo grave.

- **Instantáneas (snapshots)**  
  Capturan el estado de un sistema o disco en un momento concreto.  
  Son rápidas, pero dependen del sistema de archivos y no sustituyen a una copia externa.

---

### Redundancia de datos (RAID)

La **redundancia** consiste en duplicar datos para aumentar la **seguridad y disponibilidad** del sistema.  
Un ejemplo común es **RAID**, que combina varios discos duros para mejorar la tolerancia a fallos.
RAID **no es una copia de seguridad**, ya que solo protege frente a fallos de hardware y no ante borrados accidentales, virus o errores humanos.

---


## 2. Teoría de comandos para copias de seguridad

En Linux existen varios comandos para realizar copias de seguridad. Cada uno tiene un uso distinto según el tipo de datos y el entorno donde se utilice.

## Comandos de copia de seguridad

| Comando | Definición | Características |
|-------|-----------|----------------|
| **cp** | Realiza una copia simple de archivos o directorios | No es inteligente, equivale a *copiar y pegar* (Ctrl+C / Ctrl+V). Solo se usa en sistemas locales |
| **rsync** | Sincroniza archivos y carpetas | Permite copias locales y remotas mediante **SSH**. Solo copia los cambios, por lo que es rápido y eficiente |
| **dd** | Clona discos o particiones completas | No es inteligente. Copia bloque a bloque. Se usa para clonar discos, no para copias de archivos |

---

- El comando `dd` no se recomienda para copias de seguridad habituales de archivos, ya que no discrimina datos y puede sobrescribir información si se usa incorrectamente.


## 3. Práctica: comandos de copias de seguridad

 ### Paso 1
 
Se crea un sistema de archivos EXT4 en la partición `/dev/sdb1` usando:

mkfs.ext4 /dev/sdb1

Este proceso borra el contenido anterior y deja el dispositivo listo para su uso.  
A continuación, se accede al directorio `/var` y se crea la carpeta `copies`, que se utilizará como destino o punto de montaje para las copias.

<img width="741" height="496" alt="Captura de pantalla de 2025-12-12 12-37-10" src="https://github.com/user-attachments/assets/1133f6c8-228b-454d-91b1-91ce5f44b47b" />

### Paso 2

Después de crear el sistema de archivos, se monta la partición `/dev/sdb1` en el directorio `/var/copies` mediante el comando:

mount -t ext4 /dev/sdb1 /var/copies

A continuación, se utiliza `df -T` para comprobar que el dispositivo se ha montado correctamente.  
La salida confirma que `/dev/sdb1` utiliza el sistema de archivos **ext4** y está montado en `/var/copies`, quedando listo para almacenar copias de seguridad.

<img width="743" height="492" alt="Captura de pantalla de 2025-12-12 12-39-12" src="https://github.com/user-attachments/assets/107e4a31-948c-47fc-b480-b554c9beb9b4" />

### Paso 3
 
En las siguientes fotos se realiza una copia de seguridad simple utilizando el comando `cp`.

Primero, se crean un archivo (`prova`) y un directorio (`prova2`) en el directorio `/home/vlad/Documentos`.  
A continuación, se copian todos los archivos y carpetas de este directorio al destino `/var/copies` usando:

cp -R /home/vlad/Documentos/* /var/copies/

El parámetro `-R` permite copiar directorios de forma recursiva.

Finalmente, se comprueba la copia con `ls /var/copies`, verificando que los elementos `prova` y `prova2` se han copiado correctamente.


<img width="735" height="489" alt="Captura de pantalla de 2025-12-12 12-44-11" src="https://github.com/user-attachments/assets/d89727d5-c4f4-44a8-a0b8-1a2a77cb56e5" />


### Paso 4

Después de realizar la primera copia, se modifica el contenido del directorio origen.  
Se crea un nuevo archivo llamado `divendres` y se elimina el archivo `prova`:

A continuación, se vuelve a ejecutar el comando de copia:

cp -R /home/vlad/Documentos/* /var/copies/

Finalmente, se comprueba el contenido del destino con.  
Se observa que el nuevo archivo `divendres` se ha copiado correctamente, pero el archivo `prova` sigue existiendo en el destino.

Esto demuestra que el comando `cp` **no es inteligente**, ya que copia archivos nuevos o modificados, pero **no elimina los archivos borrados en el origen**, por lo que no sincroniza carpetas.

<img width="735" height="487" alt="Captura de pantalla de 2025-12-12 12-44-52" src="https://github.com/user-attachments/assets/f1f682ea-c047-4c9d-bb72-378af2b99579" />

### Paso 5

En las siguientes fotos se comprueba el funcionamiento del comando `rsync`, que permite sincronizar carpetas de forma inteligente.

Primero, se realizan cambios en el directorio origen `/home/vlad/Documentos`:  
se crea el archivo `dissabte`, se crea el directorio `nadal` y se elimina el directorio `prova2`.

A continuación, se ejecuta el comando:

rsync -av --delete /home/vlad/Documentos/ /var/copies/

Las opciones utilizadas son:
- `-a`: modo archivo (mantiene permisos y estructura)
- `-v`: muestra información del proceso
- `--delete`: elimina en el destino los archivos que ya no existen en el origen

El resultado muestra que `rsync` elimina automáticamente los archivos y carpetas borrados en el origen (`prova2`, `prova`, `lost+found`) y copia los nuevos elementos.

Esto demuestra que `rsync` **sí es inteligente**, ya que sincroniza completamente el contenido entre origen y destino.

Finalmente, al listar el contenido del destino con `ls /var/copies`, se comprueba que ambos directorios contienen los mismos archivos y carpetas (`dissabte`, `divendres` y `nadal`).

Esto confirma que `rsync` sincroniza correctamente el contenido entre origen y destino, manteniendo ambos directorios idénticos.

<img width="738" height="490" alt="Captura de pantalla de 2025-12-12 12-47-19" src="https://github.com/user-attachments/assets/45cbd758-abcd-47bf-9f46-1d3cb4beb36e" />
<img width="738" height="490" alt="Captura de pantalla de 2025-12-12 12-47-26" src="https://github.com/user-attachments/assets/a782b487-cda8-4ed1-a145-948208343df4" />


### Paso 6

En esta foto se realiza el clonado completo de un disco utilizando el comando `dd`.

Primero, se crea el directorio `/var/clonacio` y se monta la partición `/dev/sdc1` para su uso.  
A continuación, se ejecuta el comando:

dd if=/dev/sdb1 of=/dev/sdc1 bs=1M status=progress

Este comando copia el contenido del disco origen (`/dev/sdb1`) al disco destino (`/dev/sdc1`) bloque a bloque.  
La opción `bs=1M` mejora el rendimiento y `status=progress` muestra el avance del proceso.

Para verificar que la clonación se ha realizado correctamente, se utiliza:

md5sum /dev/sdb1 /dev/sdc1

El resultado muestra el mismo valor hash en ambos discos, lo que confirma que la copia es **idéntica**.

Esto demuestra que `dd` permite clonar discos o particiones completas, aunque no es un método inteligente para copias de archivos.

<img width="738" height="490" alt="Captura de pantalla de 2025-12-12 12-51-26" src="https://github.com/user-attachments/assets/96bc97f9-4843-467f-9c3d-77ed435b3bc2" />


## 4. Copias de seguridad con Duplicity 

La primera copia es completa y las siguientes solo almacenan los cambios, reduciendo el tiempo y el espacio necesario para las copias de seguridad.
 
---

### Paso 1 

Antes de usar Duplicity es necesario instalar el paquete, ya que no viene instalado por defecto en el sistema.

Después se crea el directorio donde se almacenarán las copias de seguridad:
sudo mkdir -p /var/backups-duplicity

Se realiza la primera copia completa del directorio /home/vlad/Documentos: sudo duplicity full /home/vlad/Documentos file:///var/backups-duplicity
Esta copia guarda todos los archivos y carpetas del directorio origen.

<img width="828" height="580" alt="Captura de pantalla de 2025-12-17 23-25-29" src="https://github.com/user-attachments/assets/cb56e2d2-802d-496d-a36e-450967057db7" />

### Paso 2

Para comprobar el funcionamiento de las copias incrementales, creamos el fichero "prueba1" y la carpeta "carpeta1" en el directorio origen

Se ejecuta nuevamente Duplicity sin indicar full: sudo duplicity /home/vlad/Documentos file:///var/backups-duplicity

Duplicity detecta que ya existe una copia completa y guarda solo los cambios, creando una copia incremental.

<img width="822" height="575" alt="Captura de pantalla de 2025-12-17 23-31-28" src="https://github.com/user-attachments/assets/d3b9ec75-d540-4d0e-a8d8-522b54f216af" />

### Paso 3

Para verificar que existen copias completas e incrementales se usa: sudo duplicity collection-status file:///var/backups-duplicity
El resultado muestra la copia completa inicial y las copias incrementales posteriores.

<img width="822" height="575" alt="Captura de pantalla de 2025-12-17 23-32-47" src="https://github.com/user-attachments/assets/bdee44f2-5273-456b-9190-a7da012852e0" />


## 5. Teoría de automatización

## Automatización: scripts, cron y anacron

## ¿Qué es un script?
Un **script** es un archivo que contiene una serie de comandos que se ejecutan de forma automática y en el orden indicado.  
Se utilizan para **automatizar tareas repetitivas**, evitando tener que ejecutar los comandos manualmente uno a uno.

---

## ¿Para qué sirven los scripts?
Los scripts permiten:
- Automatizar copias de seguridad
- Ejecutar tareas de mantenimiento
- Programar limpiezas del sistema
- Ahorrar tiempo y reducir errores humanos

---

## Diferencias entre `cron` y `anacron`

### `cron`
El servicio **cron** se utiliza para automatizar tareas de usuarios o del sistema en una **fecha y hora concretas**.

Características:
- Ejecuta tareas en un momento exacto
- Se usa habitualmente para tareas de **usuarios**
- Si el ordenador está apagado en el momento programado, **la tarea se pierde**
- Ideal para tareas frecuentes y precisas

---

### `anacron`
**Anacron** sirve para automatizar tareas similares a cron, pero pensadas para **tareas generales del sistema**.

Características:
- No requiere que el ordenador esté encendido a una hora exacta
- Si el sistema está apagado, la tarea se ejecuta **cuando vuelve a encenderse**
- Se utiliza principalmente para tareas del sistema operativo
- No está pensado para tareas de usuarios normales

---

### Relación entre cron y anacron
Antiguamente, `cron` y `anacron` funcionaban por separado.  
Actualmente, **trabajan conjuntamente**, permitiendo una automatización más flexible y fiable en los sistemas Linux modernos.



## 6. Práctica de automatización

 ### Paso 1 (Automatización con `cron`)

 Abrimos "cron" mediante: nano/etc/crontab
 En este archivo se configuran las tareas **diarias, semanales y mensuales** del sistema, que se ejecutan cuando el equipo vuelve a encenderse si no pudieron realizarse antes.

<img width="742" height="484" alt="Captura de pantalla de 2025-12-12 13-02-44" src="https://github.com/user-attachments/assets/47cc49a6-18a8-4cbb-8c6f-1bae9207acd9" />
<img width="742" height="484" alt="Captura de pantalla de 2025-12-12 13-02-51" src="https://github.com/user-attachments/assets/1623aaef-3ffc-4484-98c3-4a4d12e58d33" />
<img width="742" height="484" alt="Captura de pantalla de 2025-12-12 13-03-33" src="https://github.com/user-attachments/assets/37fc814f-263f-4006-93e6-fa0bfcac5e1a" />

 ### Paso 2

Se listan los directorios relacionados con cron 

El resultado muestra los directorios:
- `cron.hourly`
- `cron.daily`
- `cron.weekly`
- `cron.monthly`

Estos directorios contienen scripts que se ejecutan de forma periódica. Cron se encarga de lanzar estas tareas y, si el sistema no estaba encendido, **anacron se asegura de que se ejecuten al volver a arrancar**.
De esta forma, cron y anacron trabajan conjuntamente para automatizar tareas del sistema sin que se pierdan.

<img width="742" height="484" alt="Captura de pantalla de 2025-12-12 13-04-27" src="https://github.com/user-attachments/assets/2687d3de-78ea-4f98-80a2-9400e1179543" />

 ### Paso 3

En la siguiente imágen vemos el **crontab de un usuario**, que permite programar tareas automáticas personales. Al abrir el editor aparece un archivo temporal donde se definen las tareas de cron. Cada tarea se define en una sola línea con el siguiente formato:

minuto hora día_mes mes día_semana comando

En este tipo de crontab **no se indica el usuario**, ya que las tareas se ejecutan con el usuario que las ha creado.

<img width="742" height="484" alt="Captura de pantalla de 2025-12-12 13-06-32" src="https://github.com/user-attachments/assets/a6138daa-9cc4-4b90-a1c4-2a86947b7aed" />

 ### Paso 4

En esta imágen se crea un **script Bash** llamado `copies.sh` para automatizar la realización de copias de seguridad.

Se define una variable `TIMESTAMP` que guarda la fecha y hora actual, lo que permite crear copias con nombres distintos y evitar sobrescribir archivos: TIMESTAMP=$(date +"%Y%m%d_%H%M%S")

Finalmente, se utiliza el comando `tar` para comprimir el directorio `/home/vlad/Documentos` en un archivo `.tar.gz`, guardándolo en el escritorio: tar -cvf "/home/vlad/Escritorio/copies_$TIMESTAMP.tar.gz" "/home/vlad/Documentos"

De esta forma, cada vez que se ejecuta el script se genera una copia de seguridad comprimida con un nombre único basado en la fecha y la hora.


<img width="907" height="526" alt="Captura de pantalla de 2025-12-12 13-11-26" src="https://github.com/user-attachments/assets/691ce3da-5e99-4bbb-a91c-fcb3d773fb26" />

 
 ### Paso 5

Una vez creado el script `copies.sh`, se comprueban sus permisos. 

Inicialmente, el archivo no tiene permiso de ejecución. Para permitir que el script pueda ejecutarse, se utiliza el comando: chmod +x copies.sh

Tras aplicar este comando, se vuelve a listar el archivo y se observa que aparece el permiso `x`, indicando que el script es ejecutable.

De este modo, el script ya puede ejecutarse manualmente o programarse con `cron` para automatizar la copia de seguridad.

<img width="907" height="526" alt="Captura de pantalla de 2025-12-12 13-12-18" src="https://github.com/user-attachments/assets/4f8684ce-c965-4284-9c28-dac076fc8916" />


### Paso 6

En esta foto se edita el archivo `/etc/crontab` para programar la ejecución automática del script de copias de seguridad `copies.sh`.

Se programa el script: /home/vlad/Documentos/copies.sh para que se ejecute de forma automática según la planificación indicada.

El script de copia de seguridad se ejecuta automáticamente sin necesidad de intervención del usuario, integrando scripts y cron para la automatización.


<img width="907" height="526" alt="Captura de pantalla de 2025-12-12 13-14-10" src="https://github.com/user-attachments/assets/9361f581-0f81-4184-bbc0-86f5af8f354a" />

<img width="175" height="274" alt="Captura de pantalla de 2025-12-12 13-17-20" src="https://github.com/user-attachments/assets/b14b02b5-dbd0-4458-ac80-8949a3574563" />

<img width="606" height="529" alt="Captura de pantalla de 2025-12-12 13-21-17" src="https://github.com/user-attachments/assets/745e04ca-0dc2-41a1-a43e-5f59afa7cc9b" />

### Paso 7

La siguiente línea del archivo `/etc/crontab` programa la ejecución de un script: 21 13 * * * root /home/vlad/copies.sh

Su significado es el siguiente:
- **21** → minuto 21
- **13** → hora 13 (13:21)
- **\*** → cualquier día del mes
- **\*** → cualquier mes
- **\*** → cualquier día de la semana
- **root** → usuario que ejecuta la tarea
- **/home/vlad/copies.sh** → script que se ejecuta

Esto indica que el script `copies.sh` se ejecutará **todos los días a las 13:21**
con permisos de administrador.

<img width="614" height="32" alt="Captura de pantalla de 2025-12-12 13-23-44" src="https://github.com/user-attachments/assets/f06592e1-55b2-47c7-bb15-2ec510bd48fc" />

### Paso 8

En esta foto se automatiza la ejecución del script de copias de seguridad utilizando el directorio `/etc/cron.daily`
Al listar el contenido del directorio con `ls /etc/cron.daily`, se comprueba que el script `copies` aparece junto a otras tareas automáticas del sistema.
De esta forma, la copia de seguridad se ejecuta diariamente sin necesidad de indicar una hora concreta y sin depender de que el sistema esté encendido en un momento exacto.

<img width="899" height="523" alt="Captura de pantalla de 2025-12-12 13-24-47" src="https://github.com/user-attachments/assets/4ff766f3-528a-49fe-a61f-39d6cc15c928" />

### Paso 9 (Automatización con `anacron`)

En esta foto se revisa el archivo `/etc/anacrontab`, que es el fichero de configuración de **anacron**.Anacron se encarga de ejecutar estas tareas cuando el sistema vuelve a encenderse si no pudieron ejecutarse en el momento previsto.
Esto garantiza que las tareas automáticas del sistema **no se pierdan**, incluso si el ordenador ha estado apagado.

<img width="899" height="523" alt="Captura de pantalla de 2025-12-12 13-25-35" src="https://github.com/user-attachments/assets/066a3d9b-ef40-4426-aafc-ae3d40534346" />

### Paso 10

El archivo `/var/spool/anacron/cron.daily` es utilizado internamente por anacron para almacenar la fecha de la última ejecución de las tareas diarias.

Este archivo suele contener un número que representa dicha fecha. Si el archivo está vacío o se elimina su contenido, anacron interpreta que las tareas diarias no se han ejecutado y las lanzará en el siguiente arranque del sistema.

<img width="899" height="523" alt="Captura de pantalla de 2025-12-12 13-26-36" src="https://github.com/user-attachments/assets/27dbf8dc-1387-4e64-9de5-b6c1122590cb" />
<img width="740" height="481" alt="Captura de pantalla de 2025-12-12 13-30-05" src="https://github.com/user-attachments/assets/ef245c70-c40a-4aa2-a55e-3ca7a67ccbe1" />

### Paso 11

Tras configurar la automatización, se comprueba que el script de copias de seguridad se ha ejecutado correctamente, ya que se genera un archivo comprimido con nombre basado en la fecha y la hora: copies_20251212_132850.tar.gz 
Esto confirma que la tarea automática se ha ejecutado.

Se revisa el archivo interno de anacron: /var/spool/anacron/cron.daily

Este archivo contiene un número que representa la **fecha de la última ejecución** de las tareas diarias, en este caso: 20251212

El hecho de que la fecha esté actualizada confirma que **anacron ha ejecutado correctamente las tareas diarias**, incluso si el sistema hubiera estado apagado en el momento programado.

<img width="190" height="190" alt="Captura de pantalla de 2025-12-12 13-29-22" src="https://github.com/user-attachments/assets/d1cd1664-c53d-4b0b-ae25-9b54ca6faf7c" />
<img width="740" height="481" alt="Captura de pantalla de 2025-12-12 13-30-05" src="https://github.com/user-attachments/assets/61dd5cbe-5acd-4d76-8575-c3bc2b3bd02f" />
<img width="740" height="481" alt="Captura de pantalla de 2025-12-12 13-30-26" src="https://github.com/user-attachments/assets/d9c09382-fb6d-4264-8226-e94539319d8c" />




 
