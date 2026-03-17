
# Sprint 4: Monitorització, connexió remota i llicenciament

## 1. Monitorización de Procesos (Task Manager)

En esta primera parte de la práctica, utilizamos la herramienta gráfica **Monitor del Sistema** (el equivalente al Task Manager en Ubuntu) para observar cómo el sistema operativo gestiona los recursos (CPU, Memoria RAM y Disco) al iniciar una nueva aplicación.

### 1.1. Estado Inicial del Sistema (En Reposo)

Antes de iniciar ninguna aplicación pesada, analizamos el estado base del sistema operativo. 

[Monitor del Sistema - Procesos en reposo]<img width="701" height="501" alt="Captura de pantalla de 2026-03-13 11-59-47" src="https://github.com/user-attachments/assets/4d2b9e98-d852-4e38-b073-8d8e3a016f00" />

[Monitor del Sistema - Recursos en reposo]<img width="701" height="501" alt="Captura de pantalla de 2026-03-13 11-59-51" src="https://github.com/user-attachments/assets/48bba2d5-979d-4840-adeb-ec6b94c6bdcf" />


**Comentarios sobre el estado inicial:**
* En la pestaña de **Procesos**, observamos que solo se están ejecutando los servicios básicos del entorno de escritorio GNOME (`gnome-shell`, `bash`, servicios de red, etc.).
* En la pestaña de **Recursos**, podemos ver que el sistema está muy relajado. El consumo de **CPU** fluctúa en niveles muy bajos (entre el 1% y el 2.9%). 
* La **Memoria RAM** base consumida por el sistema operativo es de **1.2 GB** (un 30.3% del total disponible), lo cual es normal para mantener el entorno gráfico y los servicios en segundo plano.

### 1.2. Estado del Sistema de Archivos

[Monitor del Sistema - File Systems]<img width="701" height="501" alt="Captura de pantalla de 2026-03-13 11-59-56" src="https://github.com/user-attachments/assets/a13f777f-7223-45eb-b4ee-13c680f6ca89" />


**Comentarios:**
* En la pestaña de **File Systems**, verificamos la capacidad del disco. La partición principal (`/dev/sda3`) se encuentra al **70% de su capacidad** (14.1 GB usados). Es importante monitorizar esto, ya que los navegadores web como Firefox consumen espacio de disco creando archivos temporales y caché.

### 1.3. Cambios en el Sistema al abrir Firefox

A continuación, ejecutamos el navegador web Mozilla Firefox para observar el impacto inmediato en los recursos del sistema.

[Monitor del Sistema - Proceso Firefox]<img width="699" height="75" alt="Captura de pantalla de 2026-03-13 12-00-17" src="https://github.com/user-attachments/assets/80c8130f-d1b7-44b2-a978-0f1a0a07fed2" />

**Conclusión de esta fase:**
El sistema gestiona dinámicamente los recursos. Una vez que Firefox termine de arrancar completamente, el pico de CPU volverá a bajar estabilizándose cerca del 0-2%, pero la Memoria RAM consumida se mantendrá retenida por el proceso `firefox` hasta que cerremos la aplicación.
