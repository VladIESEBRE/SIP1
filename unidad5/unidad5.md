
# Instal·lació i configuració de Windows

---

## Fase 1 – Instal·lació del sistema operatiu

- **Pas 1** Crear màquina virtual amb VirtualBox
- **Pas 2** Assignar recursos (RAM mínim 4 GB, disc mínim 40 GB)
  
  <img width="1008" height="619" alt="Captura de pantalla de 2026-04-24 12-04-55" src="https://github.com/user-attachments/assets/f382ee5b-6734-446c-bd2f-9fc5be5e6a7d" />

  <img width="1008" height="619" alt="Captura de pantalla de 2026-04-24 12-05-47" src="https://github.com/user-attachments/assets/3201c749-54f0-465a-8fe1-4c056a0c3b93" />


- **Pas 3** Carregar ISO de Windows 10 o Windows 11

  <img width="1009" height="621" alt="Captura de pantalla de 2026-04-24 12-11-39" src="https://github.com/user-attachments/assets/62d18025-e07d-49dc-94f3-3703f10887de" />

- **Pas 4** Instal·lar el sistema (idioma, usuari, contrasenya)
- **Pas 5** Comprovar que arranca correctament
  
  <img width="1244" height="974" alt="Captura de pantalla de 2026-04-24 12-09-32" src="https://github.com/user-attachments/assets/5235c051-d2a2-4803-a8ba-73a805667f38" />


---

## Fase 2 – Punts de restauració

- **Pas 6** Cercar "Crear un punt de restauració"
- **Pas 7** Activar protecció del sistema al disc C:

  <img width="497" height="569" alt="Captura de pantalla de 2026-04-24 12-14-58" src="https://github.com/user-attachments/assets/c55273ac-8228-4528-bf10-0ab7042fb2fe" />

  <img width="496" height="591" alt="Captura de pantalla de 2026-04-24 12-15-08" src="https://github.com/user-attachments/assets/c702c46b-c878-49dd-93e2-0f1b4ffef10a" />

- **Pas 8** Crear un punt manual

  <img width="496" height="591" alt="Captura de pantalla de 2026-04-24 12-17-02" src="https://github.com/user-attachments/assets/8088b3e4-c62e-4df8-9ea7-5b1dfe818885" />

  <img width="496" height="591" alt="Captura de pantalla de 2026-04-24 12-16-54" src="https://github.com/user-attachments/assets/b1fab00f-0604-4ecd-abfc-c9d7ff35364d" />


- **Pas 9** Fer un canvi (instal·lar app o configuració)

  <img width="291" height="936" alt="Captura de pantalla de 2026-04-24 12-20-59" src="https://github.com/user-attachments/assets/1da2aae2-572f-41d8-bc07-11661c17dd20" />

- **Pas 10** Restaurar i comprovar

  <img width="1245" height="970" alt="Captura de pantalla de 2026-04-24 12-33-02" src="https://github.com/user-attachments/assets/ce1851ac-80b0-4fea-82f6-66ff902212e8" />

  <img width="1245" height="970" alt="Captura de pantalla de 2026-04-24 13-03-00" src="https://github.com/user-attachments/assets/436bf1f3-edac-4824-bd21-19e32db5f9c5" />


---

## Fase 3 – Llicències de Windows

- **Pas 11** Obrir Configuració → Sistema → Activació
- **Pas 12** Veure si Windows està activat

<img width="491" height="229" alt="Captura de pantalla de 2026-04-27 12-19-55" src="https://github.com/user-attachments/assets/9997439f-470c-4c3e-b5e9-43ed8d7eeaab" />

- **Pas 13** Executar al cmd: `slmgr /xpr`
  
<img width="752" height="378" alt="Captura de pantalla de 2026-04-27 12-20-57" src="https://github.com/user-attachments/assets/51191ef7-19f7-43a8-875b-3a6febb96202" />

- **Pas 14** Esbrinar llicenciament Windows i explicar breument
- Tipus de llicències de Windows:

OEM → ve preinstal·lada amb el PC, lligada a la placa base, no es pot transferir a un altre equip
Retail → es compra per separat, es pot transferir a un altre equip
Volume → per a empreses, s'activen moltes llicències alhora amb una clau única

- **Pas 15** Consultar preu aproximat d'una llicència Windows (web oficial o botigues)

  **Preu oficial en Microsoft Store:**
- Windows 10 Home → **145 €**
- Windows 10 Pro → **259 €**

  <img width="1663" height="294" alt="Captura de pantalla de 2026-04-27 12-26-38" src="https://github.com/user-attachments/assets/37203326-0e14-46f1-9ca3-e7c5d4174645" />

## Fase 4 – Gestor d'arrencada

- **Pas 16** Obrir Command Prompt com administrador
- **Pas 17** Executar `bcdedit`

  <img width="563" height="603" alt="Captura de pantalla de 2026-04-27 12-25-36" src="https://github.com/user-attachments/assets/005d148b-b45f-4abf-8695-f8066c0b8276" />

- **Pas 18** Identificar els blocs
  
  - Administrador de arranque de Windows (Boot Manager)

    <img width="521" height="227" alt="Captura de pantalla de 2026-04-27 12-28-45" src="https://github.com/user-attachments/assets/a792242a-1a2a-4848-8be2-6aede2336b38" />

  - Cargador de arranque de Windows (Boot Loader)

    <img width="506" height="318" alt="Captura de pantalla de 2026-04-27 12-31-03" src="https://github.com/user-attachments/assets/1cf38fbd-f9db-4e96-a880-515ed09c9913" />

- **Pas 19** Interpretar dades concretes

  **Bloc Boot Manager (Administrador de arranque):**
- `device` = `partition=\Device\HarddiskVolume1` → disc on està el gestor d'arrencada
- `default` = `{current}` → arrenca el sistema actual per defecte
- `timeout` = `30` → espera 30 segons abans d'arrencar automàticament

  **Bloc Boot Loader (Cargador de arranque):**
- `device` = `partition=C:` → Windows està instal·lat al disc C:
- `path` = `\Windows\system32\winload.efi` → fitxer que carrega Windows
- `description` = `Windows 10` → el sistema operatiu instal·lat és Windows 10
- `systemroot` = `\Windows` → carpeta principal del sistema
  
- **Pas 20** Respondre preguntes curtes
  
 - **Quin sistema s'està arrencant?**
  → Windows 10 (valor `description` del Boot Loader)

- **A quin disc o partició està instal·lat?**
  → Al disc C: (valor `device partition=C:`)

- **Quant temps espera abans d'arrencar?**
  → 30 segons (valor `timeout` del Boot Manager)

- **Quin fitxer inicia Windows?**
  → `\Windows\system32\winload.efi` (valor `path` del Boot Loader)
  
- **Pas 21** Interpretació final. *Explicar amb una frase:*

  - Qui decideix l'arrencada (Boot Manager)

     - **Boot Manager** → és el que decideix quin sistema operatiu arrencar. 
  Llegeix el menú d'arrencada i aplica el timeout de 30 segons 
  abans de carregar el sistema per defecte.

  - Qui carrega el sistema (Boot Loader)
 
    - **Boot Loader** → és el que carrega el sistema operatiu a la memòria. 
  Un cop el Boot Manager li passa el control, localitza el fitxer 
  `winload.efi` i inicia Windows 10.

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
