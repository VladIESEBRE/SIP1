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

    foto defrag.

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
exFAT: Muy bueno en memorias externas y discos grandes.
XFS: muy rápido para archivos grandes (servidores).
Btrfs: snapshots, compresión, RAID integrado.
APFS: sistema de archivos moderno de Apple.

#### Tipos de formateo 

##### Formateo de alto nivel

 - Es el que se realiza desde el sistema operativo cuando seleccionamos “formato rápido”. No borra realmente los archivos, solo elimina la información del sistema de archivos. Los datos siguen físicamente en el disco y pueden recuperarse con programas como Recuva. Es muy rápido porque no revisa el contenido del disco.

##### Formateo de nivel medio

 - Similar al formateo de alto nivel, pero además comprueba si existen sectores defectuosos y los marca para no volver a usarlos. Es más lento porque hace esta verificación adicional. A nivel de borrado, se comporta igual que el alto nivel (no elimina completamente los archivos).

##### Formateo de bajo nivel

 - Es el formateo que sobrescribe todos los sectores del disco, eliminando cualquier dato sin posibilidad de recuperación. Borra absolutamente todo y devuelve el disco a un estado vacío.

 - Particions/volums : GPARTED primeras capturas aqui, Comandes. Una partición te divide el disco a nivell fisic.Volum-es una capa de abstraccio q es posa per damunt de les particions( une todo el espacio q queda libre en un disco o un aparticion).BLOCK SIZE NO HA CAMBIADO A 2048, HAY Q COREGIR.

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
