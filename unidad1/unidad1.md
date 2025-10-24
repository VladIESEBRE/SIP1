---
layout: default
title: "Sprint 1: Instalación i Configuración Inicial"
---

 # **"Virtualización e instalación del S.O Ubuntu"**

# **Instalación y particionamiento Ubuntu**

 ## Paso 1
 &nbsp;&nbsp;- En esta foto podemos elegir la memoria RAM y el número de cpus que se van a utilizar en la instalación de Ubuntu en una máquina virtual.
 
 <img width="859" height="478" alt="Captura de pantalla de 2025-09-26 12-45-05" src="https://github.com/user-attachments/assets/9a6edb8b-b134-415e-bc94-46d7e0bde50c" />

  ## Paso 2
&nbsp;&nbsp;- Aquí podemos elegir la capacidad total que tendrá el disco duro.
 
 <img width="859" height="478" alt="Captura de pantalla de 2025-09-26 12-45-47" src="https://github.com/user-attachments/assets/87922ad6-541d-413c-b3b0-57d8050a26ea" />
 
  ## Paso 3
&nbsp;&nbsp;- Aquí podemos ver la pagina inicial de particiones.Con el espacio total indicado por "dev/sda". Podemos empezar la partición manual haciendo click en el botón "Nueva tabla de particiones".
 
<img width="830" height="624" alt="Captura de pantalla de 2025-09-26 12-56-35" src="https://github.com/user-attachments/assets/b4832ebe-b028-4432-a813-170f35c93eec" />

  ## Paso 4
&nbsp;&nbsp;- Seleccionamos cuanto espacio queremos utilizar para la partición.

<img width="830" height="624" alt="Captura de pantalla de 2025-09-26 12-57-03" src="https://github.com/user-attachments/assets/d7e58052-dad4-4dbd-862c-2444124aee33" />

  ## Paso 5
&nbsp;&nbsp; -Damos click a "Utilizar como: Sistema de ficheros ext4 transaccional ,ya que ext4 es el estándar para Linux

<img width="906" height="718" alt="Captura de pantalla de 2025-09-26 12-58-24" src="https://github.com/user-attachments/assets/cbd3f8d0-9d5e-44ce-b982-7573a160a590" />

  ## Paso 6
&nbsp;&nbsp; -Elegimos el punto de montaje ,sda1(/)(es el espeacio reservado para el S.O).Reservamos 20GB en este caso.

<img width="906" height="718" alt="Captura de pantalla de 2025-09-26 12-59-07" src="https://github.com/user-attachments/assets/84732e9b-9593-4b10-b9f1-a03fea89453f" />

  ## Paso 7
 &nbsp;&nbsp; -Después, seleccionamos "espacio libre" y damos click al botón "+" para crear nuevas particiones: sda2 (/home) (el espacio reservado para los documentos de usuario, 10GB en este caso) 

<img width="906" height="718" alt="Captura de pantalla de 2025-09-26 13-01-56" src="https://github.com/user-attachments/assets/3a31622e-08a1-4f7d-a093-4979d3c713bd" />

  ## Paso 8
 
 &nbsp;&nbsp; -Seguimos con el mismo proceso de antes para crear: 
 - sda3(/boot) (Archivos de arranque (kernel)(Facilita acualizaciónes y multi-boot) *5GB*
 - sda4(swap) (Memoria virtual; útil si la RAM es limitada(elegimos "Área de intercambio",en la opción "Utilizar como") *4GB*
 - sda5(efi) (contiene los archivos de arranque necesarios para que el sistema operativo se inicie en un sistema con UEFI(elegimos "FAT32",en la opción "Utilizar como".)) *1GB* 
 - sda6(biosgrub)(área reservada para BIOS(elegimos "Área reservada de la BIOS de arranque" en la opción "Utilizar como")) *98MB*

<img width="906" height="718" alt="Captura de pantalla de 2025-09-26 13-07-54" src="https://github.com/user-attachments/assets/b62dbb33-45c5-4ef9-8386-bfe512526977" />
 <br><br>
  <br><br>

# **Licenciamiento**
 
## **Licencia de Ubuntu**
&nbsp;&nbsp;Ubuntu, no tiene una única licencia, ya que está compuesto por muchos programas, cada uno con su propia licencia.La mayoría del software en Ubuntu está bajo licencias de software libre, principalmente la GNU General Public License (GPL), que permite usar, modificar y distribuir el código libremente, siempre que los derivados mantengan la misma licencia.

## **Por qué hay tantas licencias diferentes en Ubuntu?**
&nbsp;&nbsp;Ubuntu tiene muchas licencias porque está hecho de muchos programas diferentes, y cada uno tiene sus propias reglas. Algunos son completamente libres (como GPL), otros más flexibles (como MIT), y algunos son propietarios (como controladores de NVIDIA). Como Ubuntu junta software de varias fuentes, cada uno trae su licencia, y por eso hay tanta variedad.

<img width="266" height="59" alt="Captura de pantalla de 2025-09-26 11-59-32" src="https://github.com/user-attachments/assets/5c421019-47b9-472a-a5c6-d3e65fbb23c0" />

&nbsp;&nbsp;En este proyecto utilizo la licencia Attribution-NoDerivatives 4.0 International (CC BY-ND 4.0) de Creativer Commons.
 
 - La © indica que la obra está protegida por derechos de autor.
 - Attribution (BY),simbolizado por el icono de la persona ,requiere que se dé crédito al autor original.
 - NoDerivatives (ND),sibolizado por "=", prohíbe modificar o crear obras derivadas de la original.
 - 4.0 International quiere decir que es la versión más reciente de esta licencia, aplicable globalmente con términos estandarizados.

<br><br>
  <br><br>
# Instalaciones duales y gestores de arranque

 ## Paso 1
 &nbsp;&nbsp; - Activamos EFI ya que si no lo activamos nos podríamos enfrentar con problemas de compatibilidad.Tenemos que instalar el Windows en GPT.
 
<img width="874" height="578" alt="Captura de pantalla de 2025-10-03 11-56-28" src="https://github.com/user-attachments/assets/f02d0b70-215d-4a02-9ea0-ae9ed4d58d7d" />

 ## Paso 2
 &nbsp;&nbsp; - Creamos un disco virtual y montamos la imagen ISO con el Windows 10 Enterptrise en "Controlador:IDE"

<img width="874" height="578" alt="Captura de pantalla de 2025-10-03 11-59-31" src="https://github.com/user-attachments/assets/1424ef9b-ad47-49f1-b8d1-c4058580b0d0" />

 ## Paso 3
 &nbsp;&nbsp; - Selecionamos Instalación personalizada,para poder elegir donde instalar en windows.

<img width="1186" height="886" alt="Captura de pantalla de 2025-10-03 12-03-46" src="https://github.com/user-attachments/assets/c395f3ea-d0e8-4482-85e4-1e6d462ba0a5" />
 
 ## Paso 4
 &nbsp;&nbsp; - Seleccionamos "Unidad 0-Particion 8" (es el disco virtual) y le damos al boton nuevo para crear una particion nueva e instalar el windows ahí. 

<img width="1186" height="886" alt="Captura de pantalla de 2025-10-03 12-04-48" src="https://github.com/user-attachments/assets/458fa1b7-bd1f-4392-aa49-ee3a513beed4" />
 
 ## Paso 5 
 &nbsp;&nbsp; - Seguimos con la instalación normal del windows hasta que llegamos al Home Screen y comprobamos que todo se ha instalado correctamente.  

<img width="1186" height="886" alt="Captura de pantalla de 2025-10-03 12-28-39" src="https://github.com/user-attachments/assets/cb21aaeb-7d50-412d-8355-5e2f7d9df452" />
 
 ## Paso 6
 &nbsp;&nbsp; - Borramos el disco virtual del Windows que hemos creado.

<img width="880" height="542" alt="Captura de pantalla de 2025-10-03 12-29-26" src="https://github.com/user-attachments/assets/e5fb4ee1-8454-4233-af71-7c4f60686900" />
 
 ## Paso 7
 &nbsp;&nbsp; - Creamos un disco virtual vacío.

<img width="880" height="542" alt="Captura de pantalla de 2025-10-03 12-29-47" src="https://github.com/user-attachments/assets/608725a0-8125-432c-98bb-c046210dfa49" />
 
 ## Paso 8
 &nbsp;&nbsp; - Montamos la ISO "Spuber_GRUB_2..." que nos permitirá acceder al Ubuntu.

<img width="1104" height="639" alt="Captura de pantalla de 2025-10-03 12-39-50" src="https://github.com/user-attachments/assets/48f1c293-ddf0-4a88-b35f-f4cade900f8c" />
 
 ## Paso 9
 &nbsp;&nbsp; - Entramos en el Boot Manager del VM (apretando la tecla "ESC" rapidamente) y seleccionamos "UEFI V-BOX"( el disco virtual que acabamos de montar)

<img width="651" height="483" alt="Captura de pantalla de 2025-10-03 12-40-43" src="https://github.com/user-attachments/assets/4e2693ce-580f-45f4-b63c-88cca4dfddb6" />
 
 ## Paso 10
 &nbsp;&nbsp; - Le damos a la segunda opción ("Detect and show boot methods) y seleccionamos Ubuntu(o Linux dependiendo del caso).

<img width="641" height="489" alt="Captura de pantalla de 2025-10-03 12-41-20" src="https://github.com/user-attachments/assets/79a04a1b-58e9-43d3-a7a1-3628b83625f0" />
 
 ## Paso 11
 &nbsp;&nbsp; - Al llegar a la página principal de Ubuntu, abrimos el terminal y escribimos "apt install --reinstall grub-pc" (fuerza la reinstalación del paquete que contiene los archivos necesarios para que GRUB funcione en sistemas que arrancan en modo BIOS).

<img width="746" height="486" alt="Captura de pantalla de 2025-10-03 12-46-42" src="https://github.com/user-attachments/assets/3a4a50aa-82a1-4eeb-b4a1-3caed095bef8" />
 
<img width="746" height="486" alt="Captura de pantalla de 2025-10-03 12-49-01" src="https://github.com/user-attachments/assets/05c42854-8a97-49cf-bda1-572091513149" />

 ## Paso 12
 - Abrimos el archivo de configuración de GRUB escribiendo "sudo nano /etc/default/grub".
 - Ponemos una "#" antes de "#GRUB_TIMEOUT_STYLE=menu" y "#GRUB_TIMEOUT=5" para desactivarlas .Sin estas líneas, GRUB puede usar un comportamiento predeterminado, haciendo que el menú no sea visible a menos que presiones una tecla durante el arranque.
 - Añadimos "GRUB_DISABLE_OS_PROBER=false" para activar el os-prober (es una utilidad que escanea los discos en busca de otros sistemas operativos y agrega entradas para ellos en el menú de GRUB).Así GRUB puede buscar y añadir entradas para otros sistemas operativos, en el menú de arranque.
 - Salimos (Ctrl+X) y guardamos.

<img width="746" height="486" alt="Captura de pantalla de 2025-10-03 12-51-43" src="https://github.com/user-attachments/assets/10c47847-be52-46cf-ad35-390b4871f561" />
 
 ## Paso 13
  &nbsp;&nbsp; - Escribimos "update-grub2" para que se guarde la configuración.
  
<img width="746" height="486" alt="Captura de pantalla de 2025-10-03 12-53-05" src="https://github.com/user-attachments/assets/a82c9858-418f-446a-a3b2-9e306f3f8cb8" />

 ## Paso 14
  &nbsp;&nbsp; - Si queremos cambiar el orden de arranque ,escribimos "efibootmgr".Si no está instalado escribimos apt install "efibootmgr".

<img width="746" height="486" alt="Captura de pantalla de 2025-10-03 12-53-49" src="https://github.com/user-attachments/assets/a463d045-65a2-4598-a807-3a4dab15ab2b" />
 
<img width="746" height="486" alt="Captura de pantalla de 2025-10-03 12-54-49" src="https://github.com/user-attachments/assets/01cd6b90-38ba-4e02-8b48-5237f51e4cf7" />

 ## Paso 15
  &nbsp;&nbsp; - Aquí podemos ver como cambiar el orden de arranque(efibootmgr -o y los números en orden de arranque). El primero en iniciarse será UEFI VBOX HRDDISK, después UiApp ,UEFI VBOX CD-ROM etc... y al final el Windows.

<img width="746" height="486" alt="Captura de pantalla de 2025-10-03 12-57-50" src="https://github.com/user-attachments/assets/847b8947-4da3-4331-8cc8-e3113ff74bf5" />

 ## Paso 16
 &nbsp;&nbsp; - Después, al iniciar el sistema podemos entrar en el menú de GRUB y seleccionar qué sistema operativo queremos arrancar.

<img width="1037" height="821" alt="Captura de pantalla de 2025-10-03 13-01-18" src="https://github.com/user-attachments/assets/31c34a3b-7463-4640-b561-b7d93b2069cc" />

<br><br>
  <br><br>
# Particiones y puntos de restauración

## Paso 1
 &nbsp;&nbsp; - Tenemos 2 imágenes (hemos creado una nueva de 25gb en sata)
 
<img width="881" height="537" alt="Captura de pantalla de 2025-10-10 11-49-57" src="https://github.com/user-attachments/assets/015bfb7a-3315-46f1-a28b-6f6ee07e4534" />

 ## Paso 2
 &nbsp;&nbsp; - Entramos en el disco sdb que hemos creado.

<img width="1283" height="886" alt="Captura de pantalla de 2025-10-10 12-01-58" src="https://github.com/user-attachments/assets/3d588daa-73c1-4528-914f-61dbd8dbdbfa" />

 ## Paso 3
 &nbsp;&nbsp; - Creamos la partición. GPT y primaria.

<img width="1283" height="886" alt="Captura de pantalla de 2025-10-10 12-03-25" src="https://github.com/user-attachments/assets/95c4e33e-a59b-45fb-8b66-61ac3cf51b40" />

 
 ## Paso 4
 &nbsp;&nbsp; - Partición creada.
 
<img width="1283" height="886" alt="Captura de pantalla de 2025-10-10 12-04-15" src="https://github.com/user-attachments/assets/8c9b645c-c8b1-434b-9c00-d2cbb5cfb91b" />
  
 ## Paso 5 
 &nbsp;&nbsp; - Formateado la partición /dev/sdb1 con el comando "mkfs.ext4".

<img width="1283" height="886" alt="Captura de pantalla de 2025-10-10 12-05-04" src="https://github.com/user-attachments/assets/60111b4c-47f8-4be3-9fd2-e16e3e3d4b2b" />
  
 
 ## Paso 6
 &nbsp;&nbsp; - Insatalmos TimeShift.

<img width="1283" height="886" alt="Captura de pantalla de 2025-10-10 12-08-53" src="https://github.com/user-attachments/assets/0433cc6d-30e6-4101-a881-1c771197f330" />
 
 
 ## Paso 7
 &nbsp;&nbsp; - TimeShift instalado.

<img width="1283" height="886" alt="Captura de pantalla de 2025-10-10 12-08-43" src="https://github.com/user-attachments/assets/726cd0ec-6093-41d0-a1e7-a9c3e0261dbb" />
 

 ## Paso 8
 &nbsp;&nbsp; - Creamos una carpeta.

<img width="1283" height="886" alt="Captura de pantalla de 2025-10-10 12-10-44" src="https://github.com/user-attachments/assets/80d9ee0d-e5e3-4116-90e9-d5026ae4ecb8" />
 
 ## Paso 9
 &nbsp;&nbsp; - Inicio configuración Timeshift.

<img width="1283" height="886" alt="Captura de pantalla de 2025-10-10 12-11-26" src="https://github.com/user-attachments/assets/c3994f0c-3c0b-47e6-bee9-cc00f1190c28" />
 
 ## Paso 10
 &nbsp;&nbsp; - Marcamos la ubicación de la instantanea, "sdb1" en este caso.

<img width="1283" height="886" alt="Captura de pantalla de 2025-10-10 12-12-11" src="https://github.com/user-attachments/assets/ba65f111-e022-4268-915a-5263992a17f4" />
 

 ## Paso 11
 &nbsp;&nbsp; - Seleccionamos cuando se creara la instantanea (los intervalos de tiempo).

<img width="1283" height="886" alt="Captura de pantalla de 2025-10-10 12-13-06" src="https://github.com/user-attachments/assets/1d50a007-2b17-472e-a903-96b4d0aa7c6a" />
 
 ## Paso 12
  &nbsp;&nbsp; - Seleccionamos los archivos que queremos incluir o excluir. En este caso he seleccionado todos los archivos de "/root" y ningun fichero de "/home/vlad".
  
<img width="1283" height="886" alt="Captura de pantalla de 2025-10-10 12-14-50" src="https://github.com/user-attachments/assets/b076dbb5-10de-46f3-b97f-d6eb6be8cf42" />

 ## Paso 13
  &nbsp;&nbsp; - Los filtros . En este caso solo incluimos la carpeta "/Documentos".
  
<img width="1283" height="886" alt="Captura de pantalla de 2025-10-10 12-16-33" src="https://github.com/user-attachments/assets/9696a499-3f46-4a45-bcb7-b2975ecbb7bb" />

 ## Paso 14
  &nbsp;&nbsp; - Aquí podemos ver que no existe la carpeta que hemos creado(hola-->prova) . La hemos borrado.

<img width="1284" height="889" alt="Captura de pantalla de 2025-10-10 13-09-53" src="https://github.com/user-attachments/assets/4aab3951-85aa-4da4-9862-f46c91f0ad1b" />

 ## Paso 15
 &nbsp;&nbsp; - Después de recuperar los documentos mediante Timeshift ,podemos ver que la carpeta ha vuelto a aparecer.

<img width="1282" height="889" alt="Captura de pantalla de 2025-10-10 13-13-55" src="https://github.com/user-attachments/assets/94e33c6b-8542-418d-a372-c4c541d66191" />
 
     
<br><br>
  <br><br>
# Configuración básica de la red

## Paso 1
 &nbsp;&nbsp;   Para configurar una IP estática tenemos que cambiar algunos parámetros:
  
 - Seleccionamos IPv4:Manual, ya que queremos asignar nosotros la IP, no queremos que lo haga el router automaticamente(DHCP).
 - Dirección : La IP que le queremos asignar.
 - Máscara de red: Indica el tamaño de la red. En este caso, todas las IP que comienzan con 192.168.201 están en la misma red.
 - Puerta de enlace: Es la dirección del router.
 - DNS: 8.8.8 Es el servidor de nombres de Google (traduce nombres como google.com a direcciones IP).

<img width="589" height="482" alt="Captura de pantalla de 2025-10-17 11-54-57" src="https://github.com/user-attachments/assets/62ea1e2a-7df1-41a6-bb4d-9497c97b0ca1" />


## Paso 2
 &nbsp;&nbsp;   Comprobamos que la configuración de red funciona bien: 
 - Mediante el comando "ip a" podemos ver que tenemos la ip correcta "192.168.201.150" y "/24" que equivale a la máscara de red que hemos puesto.

 <img width="746" height="488" alt="Captura de pantalla de 2025-10-17 11-55-32" src="https://github.com/user-attachments/assets/86aa4a28-7c30-4cd1-b50d-6ee2729a6520" />


## Paso 3
 &nbsp;&nbsp; - Después mediante el comando "ping www.google.es" comprobamos que el equipo tiene salida a Internet y que el DNS (8.8.8.8) está funcionando.

 <img width="746" height="488" alt="Captura de pantalla de 2025-10-17 11-56-03" src="https://github.com/user-attachments/assets/46992327-e217-4bd5-a0ad-99ecb9f12541" />


## Paso 4
 &nbsp;&nbsp; - El comando "ping 8.8.8.8" prueba la conexión directa por IP, sin pasar por el DNS.

 <img width="746" height="488" alt="Captura de pantalla de 2025-10-17 11-56-37" src="https://github.com/user-attachments/assets/ff1a71f9-b326-4e1f-8dc4-bd362958ee8f" />


## Paso 5
 &nbsp;&nbsp; - También escribimos "ping 192.168.201.100" para hacer una prueba dentro de la red local (LAN). 

 <img width="746" height="488" alt="Captura de pantalla de 2025-10-17 11-57-56" src="https://github.com/user-attachments/assets/0f93e4df-9873-4ac4-a811-9658cd03887a" />


## Paso 6
 &nbsp;&nbsp; - Seleccionamos "Automático (DHCP) si queremos volver al estado inicial , con IP automática y DNS automático.

 <img width="768" height="503" alt="Captura de pantalla de 2025-10-17 11-58-33" src="https://github.com/user-attachments/assets/da1c17d1-4e71-4201-a0ee-bb8cd68cdb77" />


## Paso 7
 &nbsp;&nbsp;   Aquí tenemos una configuración manual de red (IP estática) mediante NetPlan/NetworkManager:
 - "enp0s3" es el nombre del adaptador Ethernet físico.
 - "dhcp4" y "dhcp6" están desactivados ,lo que significa que todo se configurará manualmente , no se usará DHCP.
 - "Addresses" es la IP fija que asignamos y su máscara de red: 192.168.201.150/24.
 - "routes -to ,via" define la puerta de enlace (router).
 - "nameservers" - configura el servidor DNS , en este caso Google.

 <img width="745" height="482" alt="Captura de pantalla de 2025-10-17 12-06-04" src="https://github.com/user-attachments/assets/374071f6-e022-480d-b5e8-fc0b27ad22f8" />


## Paso 8
 &nbsp;&nbsp;   Aplicamos los cambios mediante el comando "sudo netplan apply".
 - En este caso aparece una advertencia que indica que el archivo "/etc/netplan/01-network-manager-all.yaml" tiene permisos demasiado abiertos.
 - Esto se puede solucionar configurando los permisos para que solo el administrador tenga acceso de lectura y escritura al archivo ("sudo chmod 600 /etc/netplan/01-network-manager-all.yaml").

 <img width="746" height="493" alt="Captura de pantalla de 2025-10-17 12-12-40" src="https://github.com/user-attachments/assets/2e6c8daa-faac-457b-8d74-4e488f84b2e1" />


## Paso 9
 &nbsp;&nbsp; - Comprobamos que funciona bien.

 <img width="746" height="493" alt="Captura de pantalla de 2025-10-17 12-13-05" src="https://github.com/user-attachments/assets/30323ff6-6726-47c2-b6ac-d96914d7bd72" />

     
<br><br>
  <br><br>
# Comandos generales e instalación de aplicaciones

# Instalación mediante "dpkg"(Ninvaders)
## Paso 1
 &nbsp;&nbsp; - Descargamos el archivo ".deb",que contiene el juego Ninvaders.

<img width="1281" height="879" alt="Captura de pantalla de 2025-10-21 12-48-11" src="https://github.com/user-attachments/assets/58436e0f-43de-4b3f-b48b-6db60360616e" />

## Paso 2
 &nbsp;&nbsp; - Instalamos el juego mediante el comando "sudo dpkg -i ninvaders_0.1.1-4_amd64.deb".

<img width="1281" height="879" alt="Captura de pantalla de 2025-10-21 12-50-55" src="https://github.com/user-attachments/assets/95b18115-55bc-4a7d-be11-1d333c4c2045" />

## Paso 3
  &nbsp;&nbsp; - Iniciamos el juego escribiendo "ninvaders" en el terminal.

<img width="1281" height="879" alt="Captura de pantalla de 2025-10-21 12-51-35" src="https://github.com/user-attachments/assets/dc0ba864-73da-4dbb-a439-4a333107a8dd" />

<img width="1281" height="879" alt="Captura de pantalla de 2025-10-21 12-51-46" src="https://github.com/user-attachments/assets/6459439d-2fa4-43de-8f84-65d2f117b2f9" />

## Paso 4
 &nbsp;&nbsp; - Para desinstalar el juego utilizamos el comando "sudo dpkg -r ninvaders". Al volver a escribir "ninvaders" podemos ver que el archivo ya no existe.

<img width="853" height="610" alt="Captura de pantalla de 2025-10-21 13-01-27" src="https://github.com/user-attachments/assets/7e6192a3-4a85-4ac3-9057-0f22fc88cac4" />

<img width="853" height="610" alt="Captura de pantalla de 2025-10-21 13-01-46" src="https://github.com/user-attachments/assets/5e633124-3bbc-4691-8bcb-2c6426117f7d" />

# Instalación mediante "apt"(dia)
## Paso 1
 &nbsp;&nbsp; - Instalamos el juego mediante el comando "sudo apt install dia".

<img width="975" height="489" alt="Captura de pantalla de 2025-10-22 20-58-05" src="https://github.com/user-attachments/assets/c55cb68c-77e9-4bd5-84e0-9d0fe831d028" />


## Paso 2
 &nbsp;&nbsp; - Iniciamos la aplicación escribiendo "dia" en el terminal.

<img width="1281" height="879" alt="Captura de pantalla de 2025-10-21 12-50-55" src="https://github.com/user-attachments/assets/95b18115-55bc-4a7d-be11-1d333c4c2045" />

## Paso 3
  &nbsp;&nbsp; - Para desinstalar la aplicación utilizamos el comando "sudo apt remove dia". Al volver a escribir "dia" podemos ver que el archivo ya no existe.

<img width="973" height="478" alt="Captura de pantalla de 2025-10-22 20-59-52" src="https://github.com/user-attachments/assets/c632dff9-15bf-468b-b4cb-0298099c3555" />


<img width="973" height="478" alt="Captura de pantalla de 2025-10-22 21-00-00" src="https://github.com/user-attachments/assets/42032e6e-0cb5-4dcf-ad27-aefcaa78b4f5" />

# Instalación mediante "aptitude"(geany)
## Paso 1
 &nbsp;&nbsp; - Instalamos el juego mediante el comando "sudo aptitude install geany".

<img width="977" height="487" alt="Captura de pantalla de 2025-10-22 21-06-16" src="https://github.com/user-attachments/assets/ca17191d-e139-4011-816a-b86ed79dd9e2" />


## Paso 2
 &nbsp;&nbsp; - Iniciamos la aplicación escribiendo "geany" en el terminal.

<img width="1160" height="765" alt="Captura de pantalla de 2025-10-22 21-06-43" src="https://github.com/user-attachments/assets/be0b15dd-6b2b-4122-b322-8d7d3429f6bb" />


## Paso 3
  &nbsp;&nbsp; - Para desinstalar la aplicación utilizamos el comando "sudo aptitude purge geany". El "purge" significa que también borramos la configuracion no solo la aplicación como el "remove". Al volver a escribir "geany" podemos ver que el archivo ya no existe.

<img width="970" height="493" alt="Captura de pantalla de 2025-10-22 21-07-56" src="https://github.com/user-attachments/assets/d4c7ad0e-5c4b-4721-a5b0-0b398e81db48" />

# Instalación mediante "Repositorio"(Google Chrome)
## Paso 1
 &nbsp;&nbsp; - Descargamos el fichero .deb desde la página oficial.

<img width="639" height="701" alt="Captura de pantalla de 2025-10-22 21-10-14" src="https://github.com/user-attachments/assets/a9e65227-e068-4558-b493-f476f677ca29" />


## Paso 2
 &nbsp;&nbsp; - Instalamos mediante el comando "sudo apt install ./google-chrome-stable_current_amd64.deb".

<img width="741" height="488" alt="Captura de pantalla de 2025-10-22 21-59-48" src="https://github.com/user-attachments/assets/5cfb0cfc-d9fa-4053-8b30-0917ad6fa365" />



## Paso 3
  &nbsp;&nbsp; - La instalación también añade el repositorio oficial de Google. Lo podemos verificar mediante el comando "cat /etc/apt/sources.list.d/google-chrome.list". Esto confirma que Chrome está instalado desde su repositorio oficial, y que se actualizará automáticamente cuando escribes "sudo apt update" o "sudo apt upgrade".


<img width="740" height="487" alt="Captura de pantalla de 2025-10-22 22-01-46" src="https://github.com/user-attachments/assets/2ac51591-9aba-438e-91e7-93bb76882b9f" />

## Paso 4
  &nbsp;&nbsp; - Podemos ver la version escribiendo en el terminal "google-chrome --version".

<img width="742" height="487" alt="Captura de pantalla de 2025-10-22 22-02-49" src="https://github.com/user-attachments/assets/f8a0c663-3e17-4903-bfa9-f9c49e096974" />

## Paso 5
  &nbsp;&nbsp; - Para desinstalarlo escribimos "sudo apt remove-google-stable.

<img width="742" height="487" alt="Captura de pantalla de 2025-10-22 22-03-24" src="https://github.com/user-attachments/assets/245b1d7b-e0e8-4d8d-84b5-11dc0f4be4a1" />

## Paso6
  &nbsp;&nbsp; - Para una desinstalación más completa podemos escribir:
- "sudo apt autoremove". Esto elimina dependencias que se instalaron junto con un programa, pero que ya no se usan porque desinstalamos el programa principal.
- O también "sudo apt autoclean",que elimina los archivos de paquetes antiguos del caché. Limpia el espacio en disco borrando versiones antiguas de programas que ya fueron reemplazadas por versiones nuevas.

<img width="742" height="487" alt="Captura de pantalla de 2025-10-22 22-05-27" src="https://github.com/user-attachments/assets/4b063c02-f995-4a20-87f6-eeb20e2403a6" />

































