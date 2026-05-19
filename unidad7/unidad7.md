
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

## Ejercicio 3. Consulta de licencias de Windows Server y equipos unidos al dominio

## Enunciado

Una empresa dispone de:

- 1 servidor Windows Server
- 25 ordenadores
- 10 portátiles
- 32 usuarios
- Todos los equipos unidos al dominio

La empresa necesita calcular el coste aproximado de las licencias necesarias para el servidor y para los equipos o usuarios que acceden al dominio.

---

## 1. Precios aproximados de las licencias

Los precios varían según el canal de venta (OEM, Retail, Volume Licensing, partner). Como referencia orientativa para el mercado español (año 2026):

| Producto | Precio aproximado (€) |
|---|---|
| Windows Server 2022 **Standard** (16 cores) | ~800 – 1.000 € |
| Windows Server 2022 **Datacenter** (16 cores) | ~5.000 – 6.000 € |
| **User CAL** (1 usuario) | ~35 – 40 € |
| **Device CAL** (1 dispositivo) | ~35 – 40 € |

> **Fuentes consultadas:** `microsoft.com/es-es/windows-server/pricing`, `idealo.es`, distribuidores autorizados Microsoft.

Para los cálculos se utilizan estos valores de referencia:
- Windows Server 2022 Standard = **900 €**
- Windows Server 2022 Datacenter = **5.500 €**
- CAL (User o Device) = **38 €**

---

## 2. Qué es una CAL y diferencia entre User CAL y Device CAL

### Qué es una CAL

Una **CAL (Client Access License)** es la licencia que autoriza a un usuario o a un dispositivo a acceder a los servicios de un servidor Windows Server (compartición de archivos, impresión, dominio, Active Directory, etc.).

La licencia del servidor **no incluye** el derecho de acceso de los clientes: hay que comprar una CAL por cada usuario o dispositivo que se conecte.

### User CAL

- Se asigna a una **persona**.
- Esa persona puede conectarse al servidor desde **cualquier número de dispositivos** (PC sobremesa, portátil, móvil, desde casa, desde la oficina...).
- Ideal para empresas donde los empleados utilizan múltiples dispositivos.

### Device CAL

- Se asigna a un **dispositivo**.
- **Cualquier usuario** puede utilizar ese dispositivo para acceder al servidor.
- Ideal para empresas con turnos rotativos o puestos de trabajo compartidos (un mismo ordenador utilizado por varias personas).

### Regla práctica para elegir

| Situación | Modelo recomendado |
|---|---|
| Más dispositivos que usuarios (turnos, puestos compartidos) | **Device CAL** |
| Más usuarios que dispositivos, o usuarios con múltiples dispositivos | **User CAL** |

---

## 3. Cálculo del coste para esta empresa

**Datos:** 25 ordenadores + 10 portátiles = **35 dispositivos** | **32 usuarios** | 1 servidor.

### Opción A — Windows Server Standard + User CAL

| Concepto | Cantidad | Precio unitario | Subtotal |
|---|---|---|---|
| Windows Server 2022 Standard | 1 | 900 € | 900 € |
| User CAL | 32 | 38 € | 1.216 € |
| **TOTAL** | | | **2.116 €** |

### Opción B — Windows Server Standard + Device CAL

| Concepto | Cantidad | Precio unitario | Subtotal |
|---|---|---|---|
| Windows Server 2022 Standard | 1 | 900 € | 900 € |
| Device CAL | 35 | 38 € | 1.330 € |
| **TOTAL** | | | **2.230 €** |

### Opción C (descartada) — Windows Server Datacenter + User CAL

| Concepto | Cantidad | Precio unitario | Subtotal |
|---|---|---|---|
| Windows Server 2022 Datacenter | 1 | 5.500 € | 5.500 € |
| User CAL | 32 | 38 € | 1.216 € |
| **TOTAL** | | | **6.716 €** |

---

## 4. Modelo recomendado y justificación

### Recomendación: Windows Server 2022 Standard + 32 User CAL (Opción A, ~2.116 €)

### Justificación

**¿Por qué Standard y no Datacenter?**

La edición Datacenter solo se justifica si la empresa virtualiza muchas máquinas (Datacenter permite VMs ilimitadas; Standard permite 2). Una empresa con un solo servidor físico para 35 equipos no necesita esa virtualización masiva. **Ahorro: ~4.600 €** respecto a Datacenter.

**¿Por qué User CAL y no Device CAL?**

1. Hay **menos usuarios (32) que dispositivos (35)**, por lo que se compran menos CALs de entrada.
2. Es muy probable que un usuario con portátil **utilice también un sobremesa** en la oficina, o conecte el móvil al correo del dominio. Con User CAL ese usuario solo necesita 1 licencia; con Device CAL necesitaría 2 o 3.
3. **User CAL aporta más flexibilidad** si la plantilla crece, se introduce teletrabajo, o los empleados cambian de dispositivo.

**Diferencia final: 114 € más barato que Device CAL**, con mucha más flexibilidad futura.

---

## 5. Mostrar los equipos del dominio

### 5.1. Desde Active Directory (interfaz gráfica)

# Anexo. Instalación de Active Directory Domain Services (AD DS)
 
Antes de poder mostrar los equipos del dominio (apartado 5 del ejercicio), es necesario instalar el rol **Servicios de dominio de Active Directory (AD DS)** y promocionar el servidor a controlador de dominio.
 
---
 
## Parte 1. Instalación del rol AD DS
 
### Paso 1. Abrir el asistente
 
En el **Administrador del servidor**:
 
**Administrar → Agregar roles y características**

<img width="1030" height="285" alt="Captura de pantalla de 2026-05-19 10-15-13" src="https://github.com/user-attachments/assets/5b4d030d-ced5-4e4a-988c-2787e8d48d34" />

### Paso 2. Tipo de instalación
 
Seleccionar **"Instalación basada en características o en roles"** y pulsar **Siguiente**.
 
<img width="810" height="615" alt="Captura de pantalla de 2026-05-19 10-07-57" src="https://github.com/user-attachments/assets/48c06a2f-7494-41c1-86b9-89633279faef" />

### Paso 3. Selección de servidor de destino
 
Dejar seleccionado **"Seleccionar un servidor del grupo de servidores"** y elegir el servidor local (en este caso `WIN-FSQ0PG4DRHE` con IP `10.0.2.15`). Pulsar **Siguiente**.
 
<img width="816" height="650" alt="Captura de pantalla de 2026-05-19 10-08-34" src="https://github.com/user-attachments/assets/855c7521-7d16-4155-959e-5af7af20d7f9" />

### Paso 4. Roles de servidor
 
Marcar la casilla de **"Servicios de dominio de Active Directory"**.
 
Aparecerá un popup pidiendo agregar las características requeridas:
 
- Administración de directivas de grupo
- Herramientas de administración remota del servidor
- Herramientas de AD DS y AD LDS
- Módulo de Active Directory para Windows PowerShell
- Centro de administración de Active Directory
Pulsar **"Agregar características"** → **Siguiente**.
 
**📸 CAPTURA:** *(Pantalla con el popup de características requeridas para AD DS)*
 
### Paso 5. Características y AD DS
 
En las siguientes pantallas (Características y AD DS) no hace falta tocar nada. Pulsar **Siguiente** en cada una.
 
### Paso 6. Confirmar la instalación
 
En la pantalla de confirmación se muestra el resumen de lo que se va a instalar:
 
- Administración de directivas de grupo
- Herramientas de administración remota del servidor
- Herramientas de AD DS y AD LDS
- Módulo de Active Directory para Windows PowerShell
- Herramientas de AD DS
- Centro de administración de Active Directory
- Complementos y herramientas de línea de comandos de AD DS
- **Servicios de dominio de Active Directory**
Marcar **"Reiniciar automáticamente el servidor de destino en caso necesario"** y pulsar **Instalar**.
 
**📸 CAPTURA:** *(Pantalla "Confirmar selecciones de instalación")*
 
### Paso 7. Esperar la instalación
 
La barra de progreso tardará entre 1 y 3 minutos. La instalación continúa en segundo plano aunque se cierre el asistente.
 
---
 
## Parte 2. Promoción a Controlador de Dominio
 
Instalar el rol **no crea** el dominio: solo deja el servidor preparado. Hay que promocionarlo a controlador de dominio.
 
### Paso 1. Iniciar la promoción
 
En el **Administrador del servidor**, en la parte superior derecha aparece una **bandera con un triángulo amarillo de aviso** ⚠️. Hacer clic y pulsar:
 
**"Promover este servidor a controlador de dominio"**
 
**📸 CAPTURA:** *(Notificación de promoción en el Administrador del servidor)*
 
### Paso 2. Configuración de implementación
 
Seleccionar **"Agregar un nuevo bosque"** e introducir el nombre del dominio raíz, por ejemplo:
 
```
empresa.local
```
 
Pulsar **Siguiente**.
 
**📸 CAPTURA:** *(Pantalla "Configuración de implementación")*
 
### Paso 3. Opciones del controlador de dominio
 
- Nivel funcional del bosque: **Windows Server 2016** (o superior)
- Nivel funcional del dominio: **Windows Server 2016** (o superior)
- Capacidades: dejar marcado **DNS** y **Catálogo global (GC)**
- Introducir una **contraseña de DSRM** (Directory Services Restore Mode) y anotarla — sirve para recuperaciones de emergencia.
Pulsar **Siguiente**.
 
**📸 CAPTURA:** *(Pantalla "Opciones del controlador de dominio")*
 
### Paso 4. Resto del asistente
 
- **Opciones de DNS:** ignorar el aviso de delegación → Siguiente.
- **Opciones adicionales:** se autocompleta el nombre NetBIOS (ej. `EMPRESA`) → Siguiente.
- **Rutas de acceso:** dejar los valores por defecto → Siguiente.
- **Revisar opciones:** Siguiente.
- **Comprobación de requisitos previos:** debe salir "Todas las comprobaciones de requisitos previos se realizaron correctamente" → pulsar **Instalar**.
**📸 CAPTURA:** *(Pantalla "Comprobación de requisitos previos" correcta)*
 
### Paso 5. Reinicio automático
 
El servidor **se reinicia solo** al terminar la promoción. Tras el reinicio, ya forma parte del dominio creado y es controlador de dominio.
 
---
 
## Parte 3. Verificación
 
Tras el reinicio, comprobar que todo está correcto:
 
1. En **Administrador del servidor → Herramientas** ya aparecen las nuevas opciones:
   - Usuarios y equipos de Active Directory
   - Sitios y servicios de Active Directory
   - Dominios y confianzas de Active Directory
   - Centro de administración de Active Directory
   - Administración de directivas de grupo
2. El comando `dsa.msc` desde **Win + R** ya abre la consola de Usuarios y equipos.
3. En PowerShell ya funciona:
   ```powershell
   Get-ADComputer -Filter *
   ```
 
**📸 CAPTURA:** *(Menú Herramientas mostrando las nuevas opciones de Active Directory)*
 
---
 
> **Nota:** Una vez completado este anexo, ya se pueden hacer las capturas del apartado 5 del ejercicio (mostrar equipos del dominio desde AD y desde PowerShell).
 


---

### 5.2. Desde PowerShell

Abre **PowerShell como Administrador** en el servidor.

> El módulo `ActiveDirectory` viene instalado cuando promocionas el servidor a controlador de dominio. Si no, instálalo con:
> ```powershell
> Install-WindowsFeature RSAT-AD-PowerShell
> ```

**Comandos útiles:**

```powershell
# Listar todos los equipos del dominio
Get-ADComputer -Filter *
```

```powershell
# Versión más legible con campos útiles
Get-ADComputer -Filter * -Properties OperatingSystem, LastLogonDate |
    Select-Object Name, OperatingSystem, LastLogonDate |
    Format-Table -AutoSize
```

```powershell
# Contar cuántos equipos hay en el dominio
(Get-ADComputer -Filter *).Count
```

```powershell
# Exportar la lista a CSV
Get-ADComputer -Filter * -Properties OperatingSystem, LastLogonDate |
    Select-Object Name, OperatingSystem, LastLogonDate |
    Export-Csv -Path C:\equipos_dominio.csv -NoTypeInformation -Encoding UTF8
```

**📸 CAPTURA 2:** *(Captura de pantalla de PowerShell mostrando el resultado del segundo comando: la tabla con Name, OperatingSystem y LastLogonDate)*

---

## Resumen de capturas necesarias

| # | Captura | Herramienta |
|---|---|---|
| 1 | Lista de equipos dentro de **Computers** | Active Directory Users and Computers (`dsa.msc`) |
| 2 | Salida de `Get-ADComputer` con formato tabla | PowerShell |




