
# Informe de Prácticas: Windows Server

## Ejercicio 1. Monitorización básica de Windows Server

**Objetivo:** Monitorizar el estado del servidor utilizando herramientas integradas de Windows Server.

### Pasos a seguir:

1. **Abrir el Monitor de recursos:**
   * En el servidor, abre el Administrador de tareas.
   * Ve a la pestaña "Rendimiento" y selecciona "Abrir el Monitor de recursos".

2. **Revisar el uso de CPU:**
   * Comprueba qué procesos consumen más CPU.
   * Observa el porcentaje total de uso.
     
   <img width="1023" height="747" alt="Captura de pantalla de 2026-05-15 13-20-57" src="https://github.com/user-attachments/assets/119a306b-74e1-4cf8-a70d-94aa37c8dac1" />

3. **Revisar la memoria RAM:**
   * Accede a la pestaña "Memoria".
   * Comprueba la memoria utilizada y la memoria libre.
     
   <img width="1023" height="747" alt="Captura de pantalla de 2026-05-15 13-19-55" src="https://github.com/user-attachments/assets/c91c55b7-ae5e-43f2-8c2a-42a66b874596" />


4. **Revisar el disco:**
   * Accede a la sección de "Disco".
   * Comprueba los procesos con más lectura/escritura y la actividad general.
  
     <img width="1023" height="747" alt="Captura de pantalla de 2026-05-15 13-22-22" src="https://github.com/user-attachments/assets/cb6d7936-1c60-4026-bf3e-52cc899f4804" />


5. **Revisar la red:**
   * Accede a "Red".
   * Identifica qué programas utilizan la red y la velocidad de envío/recepción.
  
     <img width="1023" height="747" alt="Captura de pantalla de 2026-05-15 13-22-53" src="https://github.com/user-attachments/assets/49e2a83c-f618-46da-b824-eb2982401a6a" />


6. **Revisar los eventos del sistema:**
   * Abre: Administrador del servidor > Herramientas > Visor de eventos.
   * Consulta los errores del sistema, advertencias y errores de aplicación.
  
     <img width="1051" height="796" alt="Captura de pantalla de 2026-05-18 14-26-32" src="https://github.com/user-attachments/assets/6e682ea9-18f6-4165-a1e8-401a119d2dcc" />


---

# Ejercicio 3. Consulta de licencias de Windows Server y equipos unidos al dominio

## 1. Precios aproximados

| Producto | Precio aproximado |
|---|---|
| Windows Server Standard | ~900€ |
| Windows Server Datacenter | ~6.000€ |
| User CAL | ~40€/usuario |
| Device CAL | ~40€/dispositivo |

## 2. Qué es una CAL

Una **CAL (Client Access License)** es una licencia de acceso de cliente que necesita cada usuario o dispositivo para conectarse legalmente a un Windows Server.

### Diferencia entre User CAL y Device CAL

- **User CAL**: se asigna a una persona. Permite que ese usuario acceda desde cualquier dispositivo.
- **Device CAL**: se asigna a un dispositivo. Permite que cualquier usuario acceda desde ese equipo concreto.

## 3. Cálculo del coste

La empresa dispone de:
- 25 ordenadores + 10 portátiles = **35 dispositivos**
- **32 usuarios**

**Coste con User CAL:**
32 usuarios × 40€ = **1.280€**

**Coste con Device CAL:**
35 dispositivos × 40€ = **1.400€**

## 4. Modelo más adecuado

El modelo más adecuado es el de **User CAL**, ya que la empresa tiene menos usuarios (32) que dispositivos (35), lo que hace que el coste total sea inferior.

## 5. Equipos del dominio

### Desde Active Directory
Administrador del servidor → Herramientas → Usuarios y equipos de Active Directory → Expandir el dominio → Carpeta "Computers"

### Desde PowerShell
```powershell
Get-ADComputer -Filter * | Select-Object Name
```
