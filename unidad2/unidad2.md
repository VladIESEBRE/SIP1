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

## 1.

 - Aquí podemos ver que cada sector lógico mide 512 bytes y cada sector físico real del disco también es de 512 bytes.
   
    <img width="743" height="491" alt="Captura de pantalla de 2025-10-31 11-55-03" src="https://github.com/user-attachments/assets/176f8cb0-743d-434b-a2ab-d974b7ac8d98" />
## 2.

 - El comando que sí sirve para ver el tamaño de bloque es: "tune2fs -l /dev/sdb1 | grep Block". Podemos ver que es de 4096 bytes.
   
 <img width="742" height="501" alt="Captura de pantalla de 2025-10-31 11-58-35" src="https://github.com/user-attachments/assets/44b761fe-87d9-4c5c-acc9-6d769a42321d" />

## 3.

 - Creamos un archivo llamado div.text con el contenido: "Per fi divendres"
 - Comprobamos el tamaño real del archivo mediante el comando "du -b div.text"
 - El 17 significa que 17 bytes es el tamaño real del contenido del archivo(cada carácter ocupa 1 byte y la frase tiene 17 caracteres).
 - "du -sh div.text" nos muestra el tamaño ocupado en disco. Aunque el archivo solo contiene 17 bytes,ocupa 4 KB reales en el disco.
 - El sistema de archivos ext4 usa bloques de 4096 bytes (4 KB).Aunque el archivo tenga 1, 10 o 17 bytes, siempre ocupará mínimo 1 bloque = 4 KB.


<img width="742" height="501" alt="Captura de pantalla de 2025-10-31 12-01-36" src="https://github.com/user-attachments/assets/f95e0125-2dd2-45d2-840b-8fe66047c6e2" />

## 4.
 - La herramienta e4defrag muestra que la partición /dev/sda1 tiene el fragmentation score a 0, por lo que no necesita desfragmentación.
Aunque hay algunos archivos del sistema (sobre todo en /var/log) con varios fragmentos. Siguen el sistema  now/best, 13/1 por ejemplo quiere decir que el 13 es el número de fragmentos actuales del archivo y el 1 es el número óptimo si estuviera completamente contiguo (normalmente 1).

 <img width="742" height="501" alt="Captura de pantalla de 2025-10-31 12-17-23" src="https://github.com/user-attachments/assets/d53dc9cd-df48-4695-bc74-ef0d722113f1" />

## 5.
 - El comando "e4defrag /dev/sda1" analiza y desfragmenta la partición /dev/sda1. Reorganiza los bloques de los archivos para que estén contiguos, minimizando la fragmentación externa y mejorando el rendimiento.
   
   <img width="737" height="490" alt="Captura de pantalla de 2025-10-31 12-19-17" src="https://github.com/user-attachments/assets/f5227d50-958d-4db9-9be2-bac8d2b767d5" />

#### Tipos de sistemas de archivos

##### FAT32 (Windows)
 - Acceso: Compatible con Windows, Linux, macOS, consolas, cámaras, etc.
 - Tamaño de bloques: Normalmente 4 KB (dependiendo del tamaño del disco).
 - Tamaño máximo de archivo: 4 GB (límite más problemático).
 - Nombre de archivos: Hasta 255 caracteres, compatible con UTF-8.
 - Rendimiento: Bueno en dispositivos pequeños, pero limitado para discos grandes.
 - Uso típico: Pendrives, tarjetas SD.

##### NTFS (Windows y Linux)
 - Acceso: Windows: lectura y escritura total. Linux: lectura y escritura mediante ntfs-3g.
 - Tamaño de bloques: Normalmente 4 KB.
 - Tamaño máximo de archivo: Hasta 16 TB o más.
 - Nombre de archivos: Hasta 255 caracteres.
 - Rendimiento: Muy bueno para sistemas Windows; gestiona bien archivos grandes.
 - Uso típico: Partición principal de Windows, discos internos.

##### EXT4 (Linux)

 - Acceso: Linux: lectura y escritura.Windows: lectura/escritura solo con programas especiales (no nativo).
 - Tamaño de bloques: Normalmente 4 KB (configurable a 1024, 2048 o 4096).
 - Tamaño máximo de archivo: Hasta 16 TB.
 - Nombre de archivos: Hasta 255 caracteres.
 - Rendimiento: Excelente, muy poca fragmentación, fiable y rápido.
 - Uso típico: Particiones de Linux.

##### Otros  
 - exFAT: Muy bueno en memorias externas y discos grandes.
 - XFS: muy rápido para archivos grandes (servidores).
 - Btrfs: snapshots, compresión, RAID integrado.
 - APFS: sistema de archivos moderno de Apple.

#### Tipos de formateo 

##### Formateo de alto nivel

 - Es el que se realiza desde el sistema operativo cuando seleccionamos “formato rápido”. No borra realmente los archivos, solo elimina la información del sistema de archivos. Los datos siguen físicamente en el disco y pueden recuperarse con programas como Recuva. Es muy rápido porque no revisa el contenido del disco.

##### Formateo de nivel medio

 - Similar al formateo de alto nivel, pero además comprueba si existen sectores defectuosos y los marca para no volver a usarlos. Es más lento porque hace esta verificación adicional. A nivel de borrado, se comporta igual que el alto nivel (no elimina completamente los archivos).

##### Formateo de bajo nivel

 - Es el formateo que sobrescribe todos los sectores del disco, eliminando cualquier dato sin posibilidad de recuperación. Borra absolutamente todo y devuelve el disco a un estado vacío.

#### Particiones / Volúmenes
 
 - Una partición es una división del disco a nivel físico. Un volumen es una capa de abstracción que se coloca por encima de las particiones físicas.
 - Los volúmenes permiten unir el espacio libre de varias particiones o discos y gestionarlo como si fuese una sola unidad.  
 
## 1.Añadir disco virtual.
  - En VirtualBox añadí un nuevo disco virtual de 10 GB (archivo Ubuntu clona_2.vdi).
  
   <img width="875" height="533" alt="Captura de pantalla de 2025-10-31 12-41-48" src="https://github.com/user-attachments/assets/32acfc5e-1114-419c-89b7-fa8021062e3d" />

## 2.Comprobación
 - Comprobamos que el sistema lo detecta como /dev/sdc.
    <img width="731" height="478" alt="Captura de pantalla de 2025-10-31 12-55-18" src="https://github.com/user-attachments/assets/a981e6e3-c0e3-400d-8d84-a2b4e7af01c6" />

## 3.Instalamos Gparted
 - GParted (GNOME Partition Editor) es un programa gráfico para gestionar particiones del disco. En este caso ya está instalado.
   
<img width="731" height="478" alt="Captura de pantalla de 2025-10-31 12-49-33" src="https://github.com/user-attachments/assets/11860273-1388-4241-8b27-1cebb0b75a70" />

 ## 4.Crear y comprobar particiones
  - Creamos una partición de 4,8GB en /sdc1 y 5,2GB en /sdc2
    <img width="731" height="478" alt="Captura de pantalla de 2025-10-31 12-57-13" src="https://github.com/user-attachments/assets/22adbf6b-a73e-4f75-a9ce-b3bbfce321f0" />
    <img width="731" height="478" alt="Captura de pantalla de 2025-10-31 12-58-02" src="https://github.com/user-attachments/assets/170824b7-2dbb-4389-97de-7138e68c6e47" />
    <img width="731" height="478" alt="Captura de pantalla de 2025-10-31 12-58-53" src="https://github.com/user-attachments/assets/20dedf64-56b2-43ab-b983-2f0e19749d0d" />
 
 ## 5.Formatear una partición
 - En esta captura se formatea la partición /dev/sdc1 usando el comando "mkfs.ext4 -b 2048". De esta forma se consigue un tamaño de bloque distinto al valor por defecto (4096 bytes).
 
  <img width="742" height="480" alt="Captura de pantalla de 2025-11-14 13-21-03" src="https://github.com/user-attachments/assets/c3847f18-7fa3-470f-b335-eb26b7bb1062" />


 ## 6.


 
 ## 1.
 
 
 
 
 
 
 
 
 
 - GPARTED primeras capturas aqui, Comandes. Una partición te divide el disco a nivell fisic.Volum-es una capa de abstraccio q es posa per damunt de les particions( une todo el espacio q queda libre en un disco o un aparticion).BLOCK SIZE NO HA CAMBIADO A 2048, HAY Q COREGIR.

## Còpies de seguretat i automatització de tasques




## Gestió d'usuaris, grups i permisos
 - Fitxers implicats // explicar vlad:x:1000:1000 ( q significa cada cosa), diferencies 1000 numero usuario /el otro 1000 git number(es el grup principal q te asignat el ususari)
   passwd--tots usuaris ,shadow--estan las contraseñas(q es cada campo del final), group(usuarios de cada group), gshadow(contraseñas y usuarios, se ve quien es el usuario administrador a diferencia del group , se ve entre los dos puntos)
 - Comandes bàsiques: adduser  añadir usuario , hasat que noinicia usuario se se van a poner las carptasm esasa carpetas se craean automaticamente
 - useradd vesper (comanda larga o paso a paso)ponerle contraseña,crear carpeta home(si la creamo como root le pasamos permisos"chown". .tiene que aparecer usuario nuevo y la comprobacion en terminal//usermod. Para borrar usuario ,userdel o userdel -r paraborar todo  usermod-L (bloquea usuario, signo exclamacion) usermod -U(para desbloquear), creamos grupo y cambiamos el nombre,
   // para cambiar el grupo principal usermod -g proves prova4// Si hay un usuario principal del grupo , el grupo se se puede borrar//directorio skel tiene 3 ficheros ocultos para todos los usuarios
Todo lo q hay en esta carpeta aparecen en todos los usuarios//skel para adduser adduser.conf, logind defs tmb useradd,default/useradd solo useradd// PRACTICA uno para adduser y otro para useradd(hacer cambios)(las fotos q he hecho son solo de explicación)// nano profilee(en sker)//PRACTICA en cada uno d elos 3 nano .profile etc...///VAR--.profile,
 
 - Personalització de comandes



## Gestió de procesos
