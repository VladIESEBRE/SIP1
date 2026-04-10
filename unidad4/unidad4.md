
# Sprint 4: Monitorització, connexió remota i llicenciament

## 1. Monitorización de Procesos (Task Manager)

En esta primera parte de la práctica, utilizamos la herramienta gráfica **Monitor del Sistema** (el equivalente al Task Manager en Ubuntu) para observar cómo el sistema operativo gestiona los recursos (CPU, Memoria RAM y Disco) al iniciar una nueva aplicación.

### 1.1. Estado Inicial del Sistema (En Reposo)

Antes de iniciar ninguna aplicación pesada, analizamos el estado base del sistema operativo. 

[Monitor del Sistema - Procesos en reposo]

<img width="701" height="501" alt="Captura de pantalla de 2026-03-13 11-59-47" src="https://github.com/user-attachments/assets/4d2b9e98-d852-4e38-b073-8d8e3a016f00" />

[Monitor del Sistema - Recursos en reposo]

<img width="701" height="501" alt="Captura de pantalla de 2026-03-13 11-59-51" src="https://github.com/user-attachments/assets/48bba2d5-979d-4840-adeb-ec6b94c6bdcf" />


**Comentarios sobre el estado inicial:**
* En la pestaña de **Procesos**, observamos que solo se están ejecutando los servicios básicos del entorno de escritorio GNOME (`gnome-shell`, `bash`, servicios de red, etc.).
* En la pestaña de **Recursos**, podemos ver que el sistema está muy relajado. El consumo de **CPU** fluctúa en niveles muy bajos (entre el 1% y el 2.9%). 
* La **Memoria RAM** base consumida por el sistema operativo es de **1.2 GB** (un 30.3% del total disponible), lo cual es normal para mantener el entorno gráfico y los servicios en segundo plano.

### 1.2. Estado del Sistema de Archivos

[Monitor del Sistema - File Systems]

<img width="701" height="501" alt="Captura de pantalla de 2026-03-13 11-59-56" src="https://github.com/user-attachments/assets/a13f777f-7223-45eb-b4ee-13c680f6ca89" />


**Comentarios:**
* En la pestaña de **File Systems**, verificamos la capacidad del disco. La partición principal (`/dev/sda3`) se encuentra al **70% de su capacidad** (14.1 GB usados). Es importante monitorizar esto, ya que los navegadores web como Firefox consumen espacio de disco creando archivos temporales y caché.

### 1.3. Cambios en el Sistema al abrir Firefox

A continuación, ejecutamos el navegador web Mozilla Firefox para observar el impacto inmediato en los recursos del sistema.

[Monitor del Sistema - Proceso Firefox]

<img width="699" height="75" alt="Captura de pantalla de 2026-03-13 12-00-17" src="https://github.com/user-attachments/assets/80c8130f-d1b7-44b2-a978-0f1a0a07fed2" />

**Conclusión de esta fase:**
El sistema gestiona dinámicamente los recursos. Una vez que Firefox termine de arrancar completamente, el pico de CPU volverá a bajar estabilizándose cerca del 0-2%, pero la Memoria RAM consumida se mantendrá retenida por el proceso `firefox` hasta que cerremos la aplicación.

## 2. Gestión de Logs (Syslog, Rsyslog y Logrotate)

En esta segunda fase de la práctica, analizamos cómo Ubuntu gestiona, almacena y filtra los registros del sistema (logs). 

### 2.1. El directorio `/var/log` y la Rotación de Logs

Por defecto, casi todos los eventos del sistema operativo se envían al archivo general `/var/log/syslog`. Sin embargo, si estos archivos crecieran indefinidamente, llenarían el disco duro.

[Directorio de Logs y Logrotate]

<img width="737" height="484" alt="Captura de pantalla de 2026-03-13 12-03-27" src="https://github.com/user-attachments/assets/5dbfb062-8fc3-4c58-a9c4-e8b6213f4d52" />

<img width="573" height="536" alt="Captura de pantalla de 2026-03-17 12-16-22" src="https://github.com/user-attachments/assets/f189ff87-7652-452a-9df5-4f25f2c84ca4" />

**Análisis de la captura:**
* En el primer comando (`ls /var/log`), vemos múltiples archivos terminados en números o extensiones comprimidas (ej. `dmesg.1.gz`, `vboxadd-setup.log.1`). Esto es el resultado de la **Rotación de Logs**.
* **¿Qué es la rotación?** El sistema renombra periódicamente el log actual (pasando a ser `.1`). Los archivos más antiguos se comprimen en `.gz` para ahorrar espacio.
* **Configuración:** Esto es gestionado por el servicio `logrotate`. Las reglas globales (por ejemplo, cambiar el tiempo de rotación de semanal `weekly` a diario `daily`) se definen en el archivo `/etc/logrotate.conf`. Las reglas específicas para cada programa se guardan en el directorio `/etc/logrotate.d/`, como se observa en la segunda parte de la captura.

### 2.2. Visualización en tiempo real y el "Problema del Ruido"

Para monitorizar eventos en tiempo real, utilizamos el comando `tail -f`.

[Monitorización con tail -f syslog]

<img width="897" height="394" alt="Captura de pantalla de 2026-03-13 12-06-44" src="https://github.com/user-attachments/assets/00549609-e979-4c20-a641-081df120b2bd" />


**Análisis:**
* El comando `tail -f /var/log/syslog` muestra las últimas líneas del log general y mantiene la terminal "escuchando", actualizándose al instante con cada nuevo evento.
* **El problema:** Como se ve en la captura, en un sistema real (o si un servicio como `gnome-shell` está lanzando advertencias), la pantalla se satura de información irrelevante a gran velocidad. Es imposible leer errores críticos entre tanto "ruido". Por eso es vital configurar filtros con `rsyslog`.

---

### 2.3. Filtrado con Rsyslog: Servicios y Prioridades

El servicio `rsyslog` permite clasificar los logs. Funciona leyendo el archivo de configuración `/etc/rsyslog.d/50-default.conf` basándose en la sintaxis: `servicio.prioridad   /ruta/destino`.

Las prioridades van de **menor a mayor gravedad**:
1. `debug` | 2. `info` | 3. `notice` | 4. `warning` | 5. `err` | 6. `crit` | 7. `alert` | 8. `emerg`

> **Nota:** Al indicar una prioridad (ej. `alert`), el sistema captura esa y todas las superiores (`emerg` y `panic`). Si usamos `=` (ej. `=alert`), captura **solo** esa.

#### Prueba 1: Todo va a Syslog por defecto
[Prueba de logger y syslog general]

<img width="898" height="797" alt="Captura de pantalla de 2026-03-13 12-14-18" src="https://github.com/user-attachments/assets/1ae49e67-250b-47f0-a75e-3a9b452eb866" />

* Usamos el comando `logger -i -s -p mail.err "Mail ha fallat"`. 
    * `-i`: Añade el PID del proceso (en este caso `[43254]`).
    * `-s`: Muestra el mensaje por pantalla.
    * `-p mail.err`: Define el servicio (`mail`) y la prioridad (`err`).
* **Conclusión:** Observamos en el `tail` inferior que, aunque sea un error de correo, termina en `/var/log/syslog` mezclado con eventos de red, demostrando que syslog es el "cajón de sastre" por defecto.

#### Prueba 2: Redirigir un servicio específico a su propio log
[Comprobación del log de correo]

<img width="863" height="396" alt="Captura de pantalla de 2026-03-13 12-15-30" src="https://github.com/user-attachments/assets/e4b70c68-bc28-4c4c-a594-d8c91ab703fc" />

* Tras añadir la regla para el servicio de correo en el archivo de configuración, hacemos un `cat /var/log/mail.log`.
* **Conclusión:** Comprobamos que el mensaje "Mail ha fallat" se ha registrado correctamente en su archivo dedicado, logrando separar los eventos.

#### Prueba 3: Filtro de prioridad mínima (`mail.crit`)
[Configuración de mail.crit en nano]

<img width="863" height="396" alt="Captura de pantalla de 2026-03-13 12-17-45" src="https://github.com/user-attachments/assets/5f889678-4e13-4366-815b-81d1c0fc049d" />

[Prueba de reinicio y filtro restrictivo]

<img width="895" height="796" alt="Captura de pantalla de 2026-03-13 12-19-30" src="https://github.com/user-attachments/assets/f1de8c5c-8506-4751-972b-1985c44da28f" />

* **Objetivo:** Filtrar solo los errores críticos o superiores del correo.
* Entramos con `nano` y configuramos la regla: `mail.crit /var/log/mail.log`. Guardamos y **reiniciamos el servicio** obligatoriamente con `systemctl restart rsyslog`.
* Mandamos un mensaje de nivel inferior: `logger -i -s -p mail.err "Mail ha fallat2"`.
* **Conclusión:** El mensaje **no** entra en `mail.log` porque un `err` (nivel 5) está por debajo del umbral `crit` (nivel 6). Sin embargo, como se ve en la terminal inferior, el sistema general (`syslog`) sí lo recoge.

#### Prueba 4: Prioridad Exacta (`mail.=crit`)
[Prueba de prioridad exacta con rsyslog]

<img width="783" height="736" alt="Captura de pantalla de 2026-03-17 11-57-40" src="https://github.com/user-attachments/assets/38cc25df-1b5d-4bef-863f-4476130df923" />

* Si editamos la regla para que sea `mail.=crit`, el comportamiento cambia.
* Al enviar tres eventos: `err` (fallo 3), `alert` (fallo 4) y `crit` (fallo 5).
* Tras hacer `cat`, **solo aparece el "fallo 5"**. El `err` se descarta por ser menor, y el `alert` se descarta porque el símbolo `=` fuerza a ignorar las prioridades superiores.

#### Prueba 5: El comodín global (`*.crit`)
[Prueba de comodín global y cat mireia.log]

<img width="895" height="796" alt="Captura de pantalla de 2026-03-13 12-29-24" src="https://github.com/user-attachments/assets/c8164c94-9d9f-43e9-bff7-79f6a9cf4703" />

* **Objetivo:** Capturar cualquier evento crítico de todo el sistema.
* Modificamos la regla a `*.crit /var/log/mireia.log` y reiniciamos el servicio.
* Generamos dos logs distintos:
    1. `logger -p cron.notice "Este no"` (Aviso de tareas programadas - Nivel bajo).
    2. `logger -p auth.alert "Este si"` (Alerta de autenticación - Nivel alto).
* **Conclusión:** Al hacer `cat /var/log/mireia.log`, comprobamos que el sistema ha creado el archivo personalizado y que **solo ha registrado el mensaje de autenticación ("Este si")**, ya que `alert` es superior a `crit`. El mensaje de cron fue correctamente ignorado.

  ## 3. Servidor de Logs Centralizado

En esta última parte de la práctica, simulamos un entorno real de producción configurando un **Servidor de Logs Centralizado**. El objetivo es que una máquina cliente envíe sus registros a través de la red a una máquina servidora. Esto es vital por motivos de seguridad: si el cliente es comprometido o falla, sus registros históricos estarán a salvo en el servidor.

Para ello, utilizamos dos máquinas virtuales:
* **Servidor (UbuntuLimpio1):** Recibe y almacena los logs (IP: 10.0.2.15).
* **Cliente (UbuntuLimpio2):** Genera y envía los logs.

### 3.1. Configuración del Servidor (Receptor)

Primero, debemos indicarle al servicio `rsyslog` del servidor que escuche peticiones externas a través de la red.

[Configuración rsyslog.conf en Servidor]

<img width="713" height="397" alt="Captura de pantalla de 2026-03-13 13-10-42" src="https://github.com/user-attachments/assets/fd9360a4-e2e6-44b9-82cf-8964233ad7d8" />

[Reinicio y UFW en Servidor]

<img width="713" height="397" alt="Captura de pantalla de 2026-03-13 13-11-37" src="https://github.com/user-attachments/assets/dbfde840-0ac3-41a7-b131-d60008e066d4" />


**Pasos realizados:**
1. Editamos el archivo principal `/etc/rsyslog.conf`.
2. Descomentamos las líneas `module(load="imudp")` e `input(type="imudp" port="514")`. Esto carga el módulo UDP y pone a la máquina a escuchar en el puerto estándar de Syslog (514).
3. Reiniciamos el servicio con `systemctl restart rsyslog`.
4. Añadimos una regla al cortafuegos (`ufw allow 514/udp`) para asegurarnos de que el tráfico entrante no sea bloqueado.

### 3.2. Configuración del Cliente (Emisor)

En la máquina cliente, debemos decirle a `rsyslog` dónde tiene que enviar una copia de la información.

[Configuración 50-default.conf en Cliente]

<img width="743" height="487" alt="Captura de pantalla de 2026-03-13 13-14-40" src="https://github.com/user-attachments/assets/fcc29ad7-3fe6-4a83-a97d-4d21bc004104" />


**Pasos realizados:**
1. Editamos el archivo de reglas `/etc/rsyslog.d/50-default.conf`.
2. Añadimos la siguiente regla en la parte superior: `*.* @10.0.2.15`.
   * `*.*`: Indica que se enviarán logs de **todos** los servicios y de **todas** las prioridades.
   * `@`: El uso de una sola arroba especifica que la transmisión se hará mediante el protocolo **UDP** (si fueran dos `@@`, sería TCP).
   * `10.0.2.15`: Es la dirección IP de nuestra máquina Servidor.
3. Reiniciamos el servicio en el cliente para aplicar la nueva regla.

### 3.3. Comprobación de la Conexión 

Para verificar que la centralización funciona, generamos un evento manual en el Cliente y comprobamos si llega al Servidor.

**1. Generación del log en el Cliente:**
[Generación del log en el Cliente]

<img width="732" height="118" alt="Captura de pantalla de 2026-03-13 13-18-09" src="https://github.com/user-attachments/assets/98ea612a-e4ed-486d-8f00-49efaddc5475" />

* Ejecutamos: `logger -p user.notice "¡Hola! Este es un log de prueba enviado al SERVIDOR CENTRAL"`.

**2. Recepción del log en el Servidor:**
[Recepción del log en el Servidor]

<img width="646" height="96" alt="Captura de pantalla de 2026-03-13 13-18-29" src="https://github.com/user-attachments/assets/a86782fa-c344-408c-990d-102c0a9673b3" />

* En el servidor, filtramos el registro general en busca de nuestra frase clave usando: `cat /var/log/syslog | grep -a "SERVIDOR CENTRAL"`.


# Práctica: Conexión Remota mediante VNC en Ubuntu

## 🖥️ Parte 1: Configuración de la Máquina Servidor 

En esta máquina instalaremos `x11vnc`, una herramienta que nos permite compartir la sesión gráfica que ya está iniciada en Ubuntu.

### Paso 1: Instalar el servidor VNC
Primero, debemos asegurarnos de que el sistema esté actualizado y luego instalar el paquete necesario.

```bash
sudo apt update
sudo apt install x11vnc -y
```
<img width="668" height="428" alt="Captura de pantalla de 2026-04-10 12-16-46" src="https://github.com/user-attachments/assets/b02053c6-63a9-4c74-bbc3-295d9826f3a8" />

### Paso 2: Crear una contraseña de seguridad
Para evitar que cualquier persona en la red se conecte a nuestra máquina sin permiso, debemos establecer una contraseña.

```bash
x11vnc -storepasswd
```
<img width="653" height="113" alt="Captura de pantalla de 2026-04-10 12-19-34" src="https://github.com/user-attachments/assets/c7806dc4-f0b0-45f2-a94d-15549c11300f" />

### Paso 3: Averiguar la dirección IP del servidor
Necesitamos saber la "dirección" de esta máquina para que el cliente sepa a dónde llamar.

```bash
ip a
```
<img width="652" height="310" alt="Captura de pantalla de 2026-04-10 12-22-01" src="https://github.com/user-attachments/assets/0091e54d-9dfd-416c-b642-876e06c95bbc" />

### Paso 4: Iniciar el servidor VNC
Ahora vamos a encender el servicio para que se quede "escuchando" a la espera de que el cliente se conecte.

```bash
x11vnc -usepw -display :0
```
<img width="735" height="487" alt="Captura de pantalla de 2026-04-10 12-28-31" src="https://github.com/user-attachments/assets/ab75b3fb-bd95-4c24-b1a1-235f7e341436" />

---

### ⚠️ Nota importante sobre el entorno gráfico (Wayland vs Xorg)

Las versiones recientes de Ubuntu utilizan **Wayland** como servidor gráfico por defecto. Sin embargo, la herramienta `x11vnc` que estamos utilizando está diseñada específicamente para interactuar con el sistema tradicional **Xorg** (X11).

Si se intenta iniciar el servidor `x11vnc` estando en una sesión de Wayland, el sistema bloqueará la captura de pantalla y la terminal devolverá un error del tipo `X Error of failed request: BadMatch`. 

**Solución aplicada:** Para solucionar esto y permitir la conexión, fue necesario cambiar el entorno gráfico del servidor. Para ello:
1. Se cerró la sesión del usuario actual.
2. En la pantalla de inicio de sesión, se hizo clic en el icono del engranaje (⚙️) situado en la esquina inferior derecha.
3. Se seleccionó la opción **"Ubuntu en Xorg"**.
4. Se volvió a iniciar sesión normalmente y se ejecutó el comando de `x11vnc`, funcionando esta vez sin errores.

## 💻 Parte 2: Configuración de la Máquina Cliente (Desde donde vamos a mirar)

Ahora nos vamos a la segunda máquina virtual de Ubuntu. Aquí instalaremos el programa que nos servirá como "visor".

### Paso 1: Instalar el cliente VNC
Abre la terminal en la máquina cliente y ejecuta:

```bash
sudo apt update
sudo apt install xtightvncviewer -y
```
<img width="743" height="484" alt="Captura de pantalla de 2026-04-10 12-33-38" src="https://github.com/user-attachments/assets/4b3a8dce-a5b5-4bf9-ab7a-c3d240e962b7" />

### Paso 2: Conectarse al servidor
Vamos a iniciar la conexión utilizando la IP que averiguamos en el Paso 3 del servidor. 

```bash
vncviewer IP_DEL_SERVIDOR
```
<img width="734" height="304" alt="Captura de pantalla de 2026-04-10 12-36-57" src="https://github.com/user-attachments/assets/6c92f364-28a5-41f8-b517-201a64d3199a" />

### Paso 3: ¡Conexión establecida!
Una vez introduzcas la contraseña, se abrirá una nueva ventana mostrándote el escritorio exacto de tu máquina Servidor.

<img width="1351" height="858" alt="Captura de pantalla de 2026-04-10 12-39-20" src="https://github.com/user-attachments/assets/683b485e-21f3-4407-8ab6-b7105e9f9fdb" />

