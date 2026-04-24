
# Instal·lació i configuració de Windows

---

## Fase 1 – Instal·lació del sistema operatiu

- **Pas 1** Crear màquina virtual amb VirtualBox
- **Pas 2** Assignar recursos (RAM mínim 4 GB, disc mínim 40 GB)
  
  <img width="1008" height="619" alt="Captura de pantalla de 2026-04-24 12-04-55" src="https://github.com/user-attachments/assets/f382ee5b-6734-446c-bd2f-9fc5be5e6a7d" />

  <img width="1008" height="619" alt="Captura de pantalla de 2026-04-24 12-05-47" src="https://github.com/user-attachments/assets/3201c749-54f0-465a-8fe1-4c056a0c3b93" />


- **Pas 3** Carregar ISO de Windows 10 o Windows 11

  <img width="1009" height="624" alt="Captura de pantalla de 2026-04-24 12-03-34" src="https://github.com/user-attachments/assets/26d2f5b0-c426-47a9-be14-4287b6d9a56b" />

- **Pas 4** Instal·lar el sistema (idioma, usuari, contrasenya)
- **Pas 5** Comprovar que arrenca correctament

---

## Fase 2 – Punts de restauració

- **Pas 6** Cercar "Crear un punt de restauració"
- **Pas 7** Activar protecció del sistema al disc C:
- **Pas 8** Crear un punt manual
- **Pas 9** Fer un canvi (instal·lar app o configuració)
- **Pas 10** Restaurar i comprovar

---

## Fase 3 – Llicències de Windows

- **Pas 11** Obrir Configuració → Sistema → Activació
- **Pas 12** Veure si Windows està activat
- **Pas 13** Executar al cmd: `slmgr /xpr`
- **Pas 14** Esbrinar llicenciament Windows i explicar breument
- **Pas 15** Consultar preu aproximat d'una llicència Windows (web oficial o botigues)

---

## Fase 4 – Gestor d'arrencada

- **Pas 16** Obrir Command Prompt com administrador
- **Pas 17** Executar `bcdedit`
- **Pas 18** Identificar els blocs
  - Administrador de arranque de Windows (Boot Manager)
  - Cargador de arranque de Windows (Boot Loader)

> **Del bloc Boot Manager, identificar:**
> - `default {current}` → sistema que arrenca per defecte
> - `timeout 30` → temps d'espera abans d'arrencar
>
> **Del bloc Boot Loader, identificar:**
> - `device partition=C:` → on està instal·lat Windows
> - `path \Windows\system32\winload.efi` → fitxer que carrega el sistema
> - `description Windows 11` → sistema operatiu

- **Pas 19** Interpretar dades concretes
- **Pas 20** Respondre preguntes curtes
  - Quin sistema s'està arrencant
  - A quin disc o partició està instal·lat
  - Quant temps espera abans d'arrencar
  - Quin fitxer inicia Windows
- **Pas 21** Interpretació final. *Explicar amb una frase:*
  - Qui decideix l'arrencada (Boot Manager)
  - Qui carrega el sistema (Boot Loader)

---

## Fase 5 – Xarxa bàsica

- **Pas 22** Obrir configuració de xarxa
- **Pas 23** Consultar IP amb: `ipconfig`
- **Pas 24** Configurar IP dinàmica (DHCP automàtic)
- **Pas 25** Configurar IP fixa (manual: IP, màscara, gateway, DNS)
- **Pas 26** Comprovar connexió amb: `ping google.com`

---

## Fase 6 – Comandes generals

- **Pas 27** Obrir PowerShell
- **Pas 28** Diferenciar cmd i PowerShell
  - `cmd` → comandes bàsiques i clàssiques
  - `PowerShell` → més potent, permet treballar amb objectes i automatitzar tasques
- **Pas 29** Comandes bàsiques (provar-les)
  - `dir` → veure fitxers
  - `cd` → moure's per carpetes
  - `mkdir prova` → crear carpeta
  - `echo hola > fitxer.txt` → crear fitxer
  - `del fitxer.txt` → eliminar fitxer
- **Pas 30** Comandes útils del sistema
  - `tasklist` → veure processos actius
  - `taskkill /IM notepad.exe /F` → tancar un procés
  - `systeminfo` → informació completa del sistema
  - `hostname` → nom de l'equip
  - `whoami` → usuari actual
- **Pas 31** Comandes de xarxa
  - `ipconfig` → veure configuració IP
  - `ping google.com` → comprovar connexió
  - `netstat -an` → connexions obertes
- **Pas 32** Comandes interessants (una mica més avançades)
  - `tree` → veure estructura de carpetes
  - `cls` → netejar pantalla
  - `help` → veure ajuda
  - `shutdown /s /t 0` → apagar l'equip
- **Pas 33** Mini interpretació
  - Indicar què mostra `tasklist`
  - Indicar què mostra `ipconfig`
  - Indicar què mostra `systeminfo`

---

## Fase 7 – Instal·lació d'aplicacions

- **Pas 34** Descarregar un programa des del navegador (ex: Chrome o VS Code)
- **Pas 35** Instal·lar-lo seguint l'assistent
- **Pas 36** Obrir-lo i comprovar que funciona
- **Pas 37** Instal·lar una aplicació des de Microsoft Store
- **Pas 38** Obrir-la i comprovar funcionament
- **Pas 39** Desinstal·lar una aplicació: *Configuració → Aplicacions → Desinstal·lar*
- **Pas 40** Verificació: *Comprovar que el programa ja no apareix al sistema*
