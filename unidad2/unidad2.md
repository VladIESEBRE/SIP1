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
 
 En Linux, los permisos controlan quién puede acceder a archivos y directorios. Se basan en el modelo UGO, que distingue entre usuario propietario (U), grupo (G) y otros (O).
Los permisos básicos son:
 - r (read): permite leer el contenido.
 - w (write): permite modificar el contenido.
 - x (execute): permite ejecutar un archivo o acceder a un directorio.

 Estos permisos pueden representarse de forma simbólica (rwx) o numérica. El comando chmod permite modificar los permisos, mientras que chown y chgrp sirven para cambiar el propietario y el grupo de un archivo o directorio.
 La umask define los permisos por defecto al crear archivos y carpetas, restando permisos a los valores base (666 para archivos y 777 para directorios).
 Existen permisos especiales como el sticky bit, el SUID y el SGID, que aportan un control adicional en situaciones concretas.
 Por último, las ACL (Access Control Lists) permiten asignar permisos más detallados a usuarios o grupos específicos, más allá del sistema tradicional UGO.

  La primera letra indica el tipo de archivo:
 - "-" → archivo normal 

 - "d" → directorio

 - "l" → enlace simbólico 

  En el caso de la foto :

 - prova empieza por "-" → archivo
 - prova2 empieza por "d" → directorio

 Después del primer carácter vienen 9 letras, divididas en 3 bloques de 3: r, w, x. En directorios, x significa poder entrar ,si no aparece la letra, no tiene ese permiso.
 En "prova" (rw-) el usuario :  r → puede leer, w → puede modificar, x → no puede ejecutar, el grupo: (r--) solo lectura, Otros: (r--) solo lectura.
 En "prova2" el usuario: (rwx) puede ver, entrar y crear/borrar cosas dentro, el grupo y otros: (r-x) pueden ver y entrar, no pueden crear ni borrar archivos.

 <img width="746" height="493" alt="Captura de pantalla de 2025-12-09 11-43-58" src="https://github.com/user-attachments/assets/55a4014e-19ad-4048-8598-f6a903235680" />


 #### Paso 1
 
 - Creamos 4 usuarios(roig, verd,groc y blau),añadimos los usuarios roig y blau al grupo parchis q hemos creado.

<img width="746" height="493" alt="Captura de pantalla de 2025-12-09 11-46-33" src="https://github.com/user-attachments/assets/a108e2eb-e565-48e8-8258-16803862d43c" />

 #### Paso 2
 
 - Vamos a "/var" y hacemos una carpeta llamada "compartida".

 <img width="746" height="493" alt="Captura de pantalla de 2025-12-09 11-47-54" src="https://github.com/user-attachments/assets/c769a530-0fb6-4403-8842-712084abfdac" />

 #### Paso 3

 - Utilizamos el comando chown para cambiar el propietario de la carpeta y chgrp para modificar el grupo propietario.

<img width="746" height="493" alt="Captura de pantalla de 2025-12-09 11-52-21" src="https://github.com/user-attachments/assets/dd472021-f692-464b-a44c-d483afca02e3" />

 
 #### Paso 4

 - En el directorio compartida, hemos quitado los permisos de acceso usando tres métodos distintos con chmod:
 - Forma numérica (octal) "chmod 750 compartida"
 - Forma simbólica quitando permisos a otros "chmod o=--- compartida"
 - Forma simbólica quitando solo el permiso de ejecución "chmod o-r,o-x compartida" o equivalente "chmod o-rx compartida".Al quitar la x, los usuarios no pueden entrar en la carpeta.

<img width="736" height="485" alt="Captura de pantalla de 2025-12-09 11-55-44" src="https://github.com/user-attachments/assets/03f37b7a-ba7d-4f90-adcf-595403397cfa" />

 
 #### Paso 5
 
 - Comprobamos que groc tiene todos los permisos,entramos y creamos una carpeta.

<img width="736" height="485" alt="Captura de pantalla de 2025-12-09 11-56-50" src="https://github.com/user-attachments/assets/44a3aa2b-1723-4653-97c8-21f416ad3855" />
 
 #### Paso 6

 - Comprobamos que el usuario groc no puede crear o borrar ficheros.

<img width="736" height="485" alt="Captura de pantalla de 2025-12-09 11-58-36" src="https://github.com/user-attachments/assets/e08a035a-05d0-43eb-adb8-f3917bee6f5b" />

 #### Paso 7
 
 - Comprobamos que el usuario verd no tiene ningun permiso.

<img width="736" height="485" alt="Captura de pantalla de 2025-12-09 12-00-00" src="https://github.com/user-attachments/assets/c9592f62-cc1b-4120-a540-587bdde2fb26" />

 
 ### PERMISOS ESPECIALES

 - Creamos un nuevo usuario llamado "morat"
 - Mediante setfacl hemos asignado permisos completos al usuario morat y lo hemos hemos verificado mediante el comando getfacl; el símbolo + confirma que existen ACL activas y que el usuario tiene permisos efectivos.
 - En la segunda foto comprobamos que "morat" tiene los permisos.

 <img width="732" height="481" alt="Captura de pantalla de 2025-12-09 12-06-28" src="https://github.com/user-attachments/assets/adc60ccd-3260-4b34-86f9-a62ce597c439" />

<img width="732" height="481" alt="Captura de pantalla de 2025-12-09 12-08-09" src="https://github.com/user-attachments/assets/14ccdbb6-f946-4dce-91e2-17023b67230e" />


 #### Paso 8
 - Denegamos al usuario roig permisos y comprobamos 
 <img width="741" height="483" alt="Captura de pantalla de 2025-12-09 12-10-24" src="https://github.com/user-attachments/assets/ea5232e1-85b7-4618-8289-1bd44090cf5e" />
 <img width="741" height="483" alt="Captura de pantalla de 2025-12-09 12-10-57" src="https://github.com/user-attachments/assets/73472222-205d-4c75-9938-332edd7b8e11" />


 #### Paso 9

 - Con setfacl -b se han eliminado todas las excepciones ACL, restaurando únicamente los permisos estándar UGO del directorio.

<img width="741" height="490" alt="Captura de pantalla de 2025-12-09 12-12-40" src="https://github.com/user-attachments/assets/84b72e7a-ce9e-4fc8-a493-9ffbebc1eac4" />

 
 #### Paso 10

 - Cambiamos el propietario y el grupo del directorio a root y concedimos permisos completos a todos los usuarios mediante chmod 777.
 <img width="741" height="490" alt="Captura de pantalla de 2025-12-09 12-14-17" src="https://github.com/user-attachments/assets/a838eea1-a5ab-4dd6-8cb0-39b4c45e2625" />

 #### Paso 11

 - Al conceder permisos 777, cualquier usuario puede acceder al directorio y borrar archivos aunque no sean de su propiedad, como se comprueba con el usuario blau.

 <img width="741" height="490" alt="Captura de pantalla de 2025-12-09 12-16-05" src="https://github.com/user-attachments/assets/f52ca467-9a95-410a-a755-91c9af73625a" />

 #### Paso 12

 - Para evitar que los usuarios borren archivos ajenos en una carpeta compartida, se ha activado el sticky bit mediante chmod o+t o chmod 1777.

<img width="741" height="490" alt="Captura de pantalla de 2025-12-09 12-19-45" src="https://github.com/user-attachments/assets/42113733-b9bc-4f7d-b409-fc159af03b69" />


 #### Paso 10

  - Con el sticky bit activado, los usuarios pueden crear archivos en la carpeta compartida, pero solo pueden borrar los que son de su propiedad, como se comprueba con el usuario verd.


 <img width="741" height="490" alt="Captura de pantalla de 2025-12-09 12-21-41" src="https://github.com/user-attachments/assets/f91fbb5e-0093-4dc3-98f4-08df00a1a4ef" />

# 📦 Copias de Seguridad y Automatización

## 📑 Índice

### 1. Teoría de las copias de seguridad
- Qué es una copia de seguridad
- Tipos de copias de seguridad (completa, incremental y diferencial)

### 2. Teoría de comandos para copias de seguridad
- `cp`
- `rsync`
- `dd`

### 3. Práctica: comandos de copias de seguridad
- Práctica con `cp`
- Práctica con `rsync`
- Práctica con `dd`

### 4. Práctica: programas de copias de seguridad
- Deja-Dup
- Duplicity

### 5. Teoría de automatización
- Scripts
- `cron`
- `anacron`

### 6. Práctica de automatización
- Automatización con `cron`
- Automatización con `anacron`


 #### Paso 10



 
 #### Paso 10


 
 #### Paso 10


 
 #### Paso 10


 
 #### Paso 10
