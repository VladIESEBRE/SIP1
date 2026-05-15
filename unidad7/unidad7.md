# Informe de Prácticas: Windows Server

## [cite_start]Ejercicio 1. Monitorización básica de Windows Server [cite: 1, 2]

[cite_start]**Objetivo:** Monitorizar el estado del servidor utilizando herramientas integradas de Windows Server[cite: 3, 4].

### Pasos a seguir:

1. **Abrir el Monitor de recursos:**
   * [cite_start]En el servidor, abre el Administrador de tareas[cite: 7, 8].
   * [cite_start]Ve a la pestaña "Rendimiento" y selecciona "Abrir el Monitor de recursos"[cite: 8].

2. [cite_start]**Revisar el uso de CPU[cite: 9]:**
   * [cite_start]Comprueba qué procesos consumen más CPU[cite: 10, 11].
   * [cite_start]Observa el porcentaje total de uso[cite: 12].
   * [cite_start]**Captura de pantalla:** (Inserta aquí tu imagen)[cite: 13].

3. [cite_start]**Revisar la memoria RAM[cite: 14]:**
   * [cite_start]Accede a la pestaña "Memoria"[cite: 15].
   * [cite_start]Comprueba la memoria utilizada y la memoria libre[cite: 16, 17, 18].
   * [cite_start]**Captura de pantalla:** (Inserta aquí tu imagen)[cite: 19].

4. [cite_start]**Revisar el disco[cite: 20]:**
   * [cite_start]Accede a la sección de "Disco"[cite: 21].
   * [cite_start]Comprueba los procesos con más lectura/escritura y la actividad general[cite: 22, 23, 24].

5. [cite_start]**Revisar la red[cite: 25]:**
   * [cite_start]Accede a "Red"[cite: 26].
   * [cite_start]Identifica qué programas utilizan la red y la velocidad de envío/recepción[cite: 27, 28, 29].

6. [cite_start]**Revisar los eventos del sistema[cite: 30]:**
   * [cite_start]Abre: Administrador del servidor > Herramientas > Visor de eventos[cite: 31, 32].
   * [cite_start]Consulta los errores del sistema, advertencias y errores de aplicación[cite: 33, 34, 35, 36].

---

## [cite_start]Ejercicio 3. Consulta de licencias de Windows Server y equipos del dominio [cite: 225, 226]

### Escenario de la empresa:
* [cite_start]**Infraestructura:** 1 servidor Windows Server[cite: 228, 229].
* [cite_start]**Equipos:** 25 ordenadores y 10 portátiles (Total 35 dispositivos)[cite: 230, 231].
* [cite_start]**Usuarios:** 32 personas[cite: 232].
* [cite_start]**Estado:** Todos los equipos están unidos al dominio[cite: 233].

### [cite_start]1. Precios aproximados[cite: 236]:
* [cite_start]**Windows Server Standard o Datacenter:** (Insertar precio buscado)[cite: 237, 238, 239].
* [cite_start]**User CAL:** (Insertar precio buscado)[cite: 240].
* [cite_start]**Device CAL:** (Insertar precio buscado)[cite: 241].

### [cite_start]2. Conceptos de licenciamiento[cite: 242]:
* [cite_start]**CAL:** Client Access License (Licencia de acceso para el cliente)[cite: 243].
* [cite_start]**Diferencia:** La **User CAL** licencia a un usuario para acceder desde cualquier dispositivo, mientras que la **Device CAL** licencia un dispositivo específico para que cualquier usuario acceda desde él[cite: 244].

### [cite_start]3. Cálculo de costes[cite: 245]:
* [cite_start]**Opción A (User CAL):** Coste de 32 licencias de usuario[cite: 246].
* [cite_start]**Opción B (Device CAL):** Coste de 35 licencias de dispositivo[cite: 248].

### [cite_start]4. Justificación del modelo adecuado[cite: 249]:
* **Elección:** Es más adecuado el modelo de **User CAL**.
* **Justificación:** Al tener menos usuarios (32) que dispositivos (35), sale más rentable licenciar por usuario. Además, permite movilidad si los usuarios usan tanto el PC como el portátil.

### [cite_start]5. Equipos del dominio[cite: 250]:
* Para visualizar los equipos, se puede utilizar:
    * [cite_start]**Active Directory:** Usuarios y equipos de Active Directory[cite: 251, 252].
    * [cite_start]**PowerShell:** Mediante comandos específicos[cite: 253].
