
# Sprint 4: Monitorització, connexió remota i llicenciament

## 1. Monitorización de Procesos (Task Manager)

En esta primera parte de la práctica, utilizamos la herramienta gráfica **Monitor del Sistema** (el equivalente al Task Manager en Ubuntu) para observar cómo el sistema operativo gestiona los recursos (CPU, Memoria RAM y Disco) al iniciar una nueva aplicación.

### 1.1. Estado Inicial del Sistema (En Reposo)

Antes de iniciar ninguna aplicación pesada, analizamos el estado base del sistema operativo. 

![Monitor del Sistema - Procesos en reposo](ruta_de_tu_captura_11-59-47.png)
![Monitor del Sistema - Recursos en reposo](ruta_de_tu_captura_11-59-51.png)

**Comentarios sobre el estado inicial:**
* En la pestaña de **Procesos**, observamos que solo se están ejecutando los servicios básicos del entorno de escritorio GNOME (`gnome-shell`, `bash`, servicios de red, etc.).
* En la pestaña de **Recursos**, podemos ver que el sistema está muy relajado. El consumo de **CPU** fluctúa en niveles muy bajos (entre el 1% y el 2.9%). 
* La **Memoria RAM** base consumida por el sistema operativo es de **1.2 GB** (un 30.3% del total disponible), lo cual es normal para mantener el entorno gráfico y los servicios en segundo plano.

### 1.2. Estado del Sistema de Archivos

![Monitor del Sistema - File Systems](ruta_de_tu_captura_11-59-56.png)

**Comentarios:**
* En la pestaña de **File Systems**, verificamos la capacidad del disco. La partición principal (`/dev/sda3`) se encuentra al **70% de su capacidad** (14.1 GB usados). Es importante monitorizar esto, ya que los navegadores web como Firefox consumen espacio de disco creando archivos temporales y caché.

### 1.3. Cambios en el Sistema al abrir Firefox

A continuación, ejecutamos el navegador web Mozilla Firefox para observar el impacto inmediato en los recursos del sistema.

![Monitor del Sistema - Proceso Firefox](ruta_de_tu_captura_12-00-17.png)

**Análisis de los cambios:**
Al abrir Firefox, el comportamiento del sistema cambia drásticamente para acomodar la nueva carga de trabajo:

1. **Asignación de PID:** El Kernel de Linux reconoce la nueva petición y le asigna un Identificador de Proceso (**ID o PID**) único. En este caso, a Firefox se le ha asignado el ID **42570**.
2. **Pico de CPU:** Observamos un incremento inmediato en la columna de `% CPU`, alcanzando un **14.29%**. Esto ocurre porque el procesador tiene que hacer un esfuerzo intensivo para leer los binarios del programa desde el disco y cargarlos en la memoria RAM, además de renderizar la interfaz gráfica inicial.
3. **Consumo de Memoria:** El proceso empieza a reservar memoria RAM para poder funcionar (en el instante de la captura, 8.7 MB, cifra que aumenta rápidamente conforme carga el perfil del usuario y las pestañas).

**Conclusión de esta fase:**
El sistema gestiona dinámicamente los recursos. Una vez que Firefox termine de arrancar completamente, el pico de CPU volverá a bajar estabilizándose cerca del 0-2%, pero la Memoria RAM consumida se mantendrá retenida por el proceso `firefox` hasta que cerremos la aplicación.
