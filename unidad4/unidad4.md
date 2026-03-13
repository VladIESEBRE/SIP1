
# Sprint 4: Monitorització, connexió remota i llicenciament

## Parte 1: Monitorización de procesos (Task Manager)
 - En Ubuntu, el equivalente al "Administrador de Tareas" de Windows suele ser una aplicación gráfica llamada Monitor del Sistema (System Monitor). Esta herramienta te permite ver en tiempo real qué programas se están ejecutando y cuántos recursos del ordenador están consumiendo.
 - captura 
 - En esta primera captura observamos el sistema en reposo. Podemos ver el consumo base de CPU y Memoria RAM que necesita el sistema operativo (Ubuntu) simplemente para mantenerse encendido, sin ninguna aplicación de usuario abierta.
 - captura
 - Esta captura muestra la pestaña File Systems. Aquí observamos que la partición raíz tiene un 70% de ocupación.
 - captura
 - En esta captura detectamos el proceso firefox.Se observa un incremento inmediato en el uso de la CPU (14.29%).

## Parte 2: Gestión de Logs (Syslog y Rsyslog)
### 2.1. Rotación de Logs (logrotate)
 - Linux utiliza un sistema llamado rotación de logs para evitar que un archivo de registro crezca infinitamente y llene el disco duro. Cuando el archivo syslog alcanza un tamaño o tiempo determinado, se renombra a syslog.1. Los más antiguos se comprimen (.gz) para ahorrar espacio. Todo esto se configura en /etc/logrotate.conf y en el directorio /etc/logrotate.d/.
 - captura

### 2.2. Visualización en tiempo real (tail -f)
 - Muestra las últimas líneas del log y se queda "escuchando", actualizando la pantalla en tiempo real conforme entran nuevos eventos.
 - captura

### 2.3. Filtrado de Logs en Rsyslog
 - Si hay mucha actividad en el sistema, la pantalla se satura de información (mucho "ruido") y es muy difícil leer los eventos importantes. Por eso necesitamos filtrarlos con rsyslog.
 - captura
 - Para hacer estas pruebas, tenemos que editar el archivo /etc/rsyslog.conf o /etc/rsyslog.d/50-default.conf. Cada vez que modificamos este archivo, debemos reiniciar el servicio con sudo systemctl restart rsyslog para aplicar los cambios.
 - captura
### Prueba 1: mail.alert
 - Añadimos mail.alert /var/log/prueba_mail.log. Esto captura eventos del servicio mail con prioridad alert y superiores (es decir, alert, emerg y panic).
 - Probamos mediante logger -p mail.alert "Prueba 1 alert".
 - logger -p mail.err "Prueba 2 err" (Este NO debe salir porque err es de menor gravedad que alert).
 - cat/var y captura

### Prueba 2: Prioridad exacta (=)
 - Añadimos mail.=crit /var/log/prueba_crit.log. Al poner el símbolo =, le decimos a rsyslog que capture SOLO esa prioridad exacta, ignorando las superiores o inferiores.
 - Probamos mediante mensajes con logger para err, alert y crit ("mail ha fallat 3", "4", "5").
 - Tras reiniciar rsyslog y enviar los mensajes, el cat debe mostrar que solo entró el mensaje enviado con prioridad crit.
 - cat/var y captura

### Prueba 3: Todo tipo de servicios (*)
 - Añadimos *.crit /var/log/mireia.log. El asterisco significa "cualquier servicio" (auth, cron, mail, kern...). Capturará todo lo que sea nivel crítico o superior.
 - Probamos mediante logger -p cron.notice "Prueba cron" (No debería aparecer, es inferior a crit).
 - logger -p auth.alert "Prueba auth" (Sí debería aparecer, alert es superior a crit).
 - cat /var/log/mireia.log demostrando que solo entró el evento de auth.alert y captura

## Parte 3: Servidor de Logs Centralizado
 - Editamos el archivo principal de rsyslog: Buscamos las siguientes líneas y quitamos la almohadilla (#) para descomentarlas.
module(load="imudp")
input(type="imudp" port="514")
 - 
