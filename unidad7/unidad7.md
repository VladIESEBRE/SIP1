
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

---

## Ejercicio 3. Consulta de licencias de Windows Server y equipos del dominio

### Escenario de la empresa:
* **Infraestructura:** 1 servidor Windows Server.
* **Equipos:** 25 ordenadores y 10 portátiles (Total 35 dispositivos).
* **Usuarios:** 32 personas.
* **Estado:** Todos los equipos están unidos al dominio.

### 1. Precios aproximados:
* **Windows Server Standard o Datacenter:** (Sustituye por el precio buscado)
* **User CAL:** (Sustituye por el precio buscado)
* **Device CAL:** (Sustituye por el precio buscado)

### 2. Conceptos de licenciamiento:
* **CAL:** Client Access License (Licencia de acceso para el cliente).
* **Diferencia:** La **User CAL** licencia a un usuario para acceder desde cualquier dispositivo, mientras que la **Device CAL** licencia un dispositivo específico para que cualquier usuario acceda desde él.

### 3. Cálculo de costes:
* **Opción A (User CAL):** Coste de 32 licencias de usuario.
* **Opción B (Device CAL):** Coste de 35 licencias de dispositivo.

### 4. Justificación del modelo adecuado:
* **Elección:** Es más adecuado el modelo de **User CAL**.
* **Justificación:** Al tener menos usuarios (32) que dispositivos (35), sale más rentable licenciar por usuario. Además, aporta mayor movilidad a los empleados si necesitan usar tanto el ordenador de sobremesa como el portátil.

### 5. Equipos del dominio:
* Para visualizar los equipos en el dominio, se puede utilizar uno de estos métodos:
    * **Active Directory:** Desde la interfaz gráfica en "Usuarios y equipos de Active Directory".
    * **PowerShell:** Mediante comandos específicos como `Get-ADComputer -Filter *`.
   * **[Inserta tu captura de pantalla aquí: equipos del dominio]**
