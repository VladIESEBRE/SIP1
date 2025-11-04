# Sprint 2: Gestió de la Informació del Sistema i Administració
## Sistemes de fitxers i particions
 - Mida del sector: Un sector es la unitat minima fisica on se guarden les dades al disc.L mida no la podem modificar  512 bytes?. Un
 - Mida del block: Un block es la unidat minima lógica com se guarden les dades a nivell se sistema operatiou.4096 bytes.Esta mida si q la podeu modificar quan formateu la partició.
 - Fragmentació interna: Tot aquell espai de diso que no s'aprofita. Bloques se dividen, 4096, si es mayor hay mas memoria , si es menor va mas rapido pero desaprofitas memoria
 - Fragmentació externa: es quan a mesura q es va trreballan amb s.o , els arxius no queden guardats en blocs continuos de memoria ,llavors el rendiment baixa entres altres coses.En windows esta el defragmentador y en linux se diu q el seu sistema de fixers es tan bo q no cal una desfragmentacion.foto defrag.
 - Tipus de sistemes de fitxers: hay muchos , windows-fat32,ntfs,linux-ext4, ntfs para acceder a los 2 , caracteristicas ( so accedir, blocs, mida dels arxius, nom dels arxius, reniment),decir los mas conocidos.
 - Tipus de formateig: alt nivell(rapido,no se borran los archivos cuando foramteamos desde so, se borran los sistemas de fixers,program "recuva"),mig nivell(es mas lento,parecido al alto,mira si hay algun sector defectuos) , lo ,baix nivell(lo borra todo).  
 - Particions/volums : GPARTED primeras capturas aqui, Comandes. Una partición te divide el disco a nivell fisic.Volum-es una capa de abstraccio q es posa per damunt de les particions( une todo el espacio q queda libre en un disco o un aparticion).BLOCK SIZE NO HA CAMBIADO A 2048, HAY Q COREGIR.

## Còpies de seguretat i automatització de tasques




## Gestió d'usuaris, grups i permisos
 - Fitxers implicats // explicar vlad:x:1000:1000 ( q significa cada cosa), diferencies 
   
 - Comandes bàsiques: adduser  añadir usuario , hasat que noinicia usuario se se van a poner las carptasm esasa carpetas se craean automaticamente
 - useradd vesper .tiene que aparecer usuario nuevo y la comprobacion en terminal
 - Personalització de comandes




## Gestió de procesos
