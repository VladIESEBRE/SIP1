# Sprint 2: Gestió de la Informació del Sistema i Administració
## Sistemes de fitxers i particions
### Mida del sector
 - Un sector es la unidad física mínima donde un disco puede leer o escribir datos.Su tamaño no se puede modificar porque depende del hardware del disco. Tradicionalmente 512 bytes por sector era el estándar, actualmente muchos discos modernos usan 4.096 bytes , pero también pueden emular 512 bytes para compatibilidad.El sistema operativo organiza los datos basándose en esta unidad mínima, si quieres guardar un archivo de 1 byte, el disco igual usa un sector completo.

### Mida del block
 - Un bloque es la unidad mínima lógica que utiliza el sistema operativo para guardar y gestionar los datos dentro de una partición. Mientras que el sector es una unidad física fija del disco, el bloque es una unidad lógica definida por el sistema de archivos (ext4, NTFS, FAT32, etc.).El tamaño habitual del bloque normalmente es de 4096 bytes. Este tamaño si que se puede modificar cuando formateas una partición y eliges el sistema de archivos.Si un archivo ocupa 1 byte, igualmente utilizará un bloque completo por eso si trabajas con archivos grandes, bloques más grandes pueden dar mejor rendimiento. Si tienes muchos archivos pequeños, conviene usar bloques pequeños para no desperdiciar espacio.

### Fragmentació interna 
 - La fragmentación interna es todo el espacio del disco que se desperdicia dentro de un bloque porque no se utiliza completamente. Si un archivo ocupa 1 byte, igualmente utilizará un bloque completo(4096 bytes) por eso si trabajas con archivos grandes, bloques más grandes pueden dar mejor rendimiento. Si hay muchos archivos pequeños, es mejor usar bloques pequeños para no desperdiciar espacio.

### Fragmentació externa 
  - es quan a mesura q es va trreballan amb s.o , els arxius no queden guardats en blocs continuos de memoria ,llavors el rendiment baixa entres altres coses.En windows esta el defragmentador y en linux se diu q el seu sistema de fixers es tan bo q no cal una desfragmentacion.foto defrag.
 - Tipus de sistemes de fitxers: hay muchos , windows-fat32,ntfs,linux-ext4, ntfs para acceder a los 2 , caracteristicas ( so accedir, blocs, mida dels arxius, nom dels arxius, reniment),decir los mas conocidos.
 - Tipus de formateig: alt nivell(rapido,no se borran los archivos cuando foramteamos desde so, se borran los sistemas de fixers,program "recuva"),mig nivell(es mas lento,parecido al alto,mira si hay algun sector defectuos) , lo ,baix nivell(lo borra todo).  
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
