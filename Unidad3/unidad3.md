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
 -  Crear la NAT Network
 
 - Esto permitirá que cliente y servidor se comuniquen sin problemas de IP.

   <img width="925" height="780" alt="Captura de pantalla de 2026-01-14 12-08-39" src="https://github.com/user-attachments/assets/056d5d75-3c59-496a-b442-330af478b717" />

## Paso 2
 -  Configurar la red del Servidor y del cliente Ubuntu

<img width="881" height="549" alt="Captura de pantalla de 2026-01-14 12-09-18" src="https://github.com/user-attachments/assets/c11e5f20-b07a-4e12-9f12-b2e68e0b0934" />

<img width="884" height="548" alt="Captura de pantalla de 2026-01-14 12-20-32" src="https://github.com/user-attachments/assets/d934ff92-1504-4f9c-961e-3163df7183c9" />

## Paso 3
 - Comprobar la conexión entre cliente y servidor y configurar la red del servidor con direccionamiento IPv4 manual.

<img width="845" height="506" alt="Captura de pantalla de 2026-01-14 12-25-42" src="https://github.com/user-attachments/assets/1367e7ec-d796-494f-9d90-39ce9a85fc16" />

<img width="586" height="478" alt="Captura de pantalla de 2026-01-16 09-30-55" src="https://github.com/user-attachments/assets/f96c77ed-8631-4a4b-94b8-bfabfdd6f2db" />

## Paso 4
 
 -  Configurar el nombre del equipo servidor modificando los archivos /etc/hostname y /etc/hosts

<img width="739" height="485" alt="Captura de pantalla de 2026-01-16 09-32-18" src="https://github.com/user-attachments/assets/c1f6267a-8a50-4538-bc56-2dbae90d4e98" />

<img width="743" height="482" alt="Captura de pantalla de 2026-01-16 09-42-40" src="https://github.com/user-attachments/assets/e53f3a27-6bf8-4c1f-ab2d-defec7f680a1" />

## Paso 5



























