
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

 **Tipus de llicències de Windows:**

- OEM → ve preinstal·lada amb el PC, lligada a la placa base, no es pot transferir a un altre equip
- Retail → es compra per separat, es pot transferir a un altre equip
- Volume → per a empreses, s'activen moltes llicències alhora amb una clau única

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
  - **`device`** = `partition=\Device\HarddiskVolume1` → disc on està el gestor d'arrencada
  - **`default`** = `{current}` → arrenca el sistema actual per defecte
  - **`timeout`** = `30` → espera 30 segons abans d'arrencar automàticament

  **Bloc Boot Loader (Cargador de arranque):**
  - **`device`** = `partition=C:` → Windows està instal·lat al disc C:
  - **`path`** = `\Windows\system32\winload.efi` → fitxer que carrega Windows
  - **`description`** = `Windows 10` → el sistema operatiu instal·lat és Windows 10
  - **`systemroot`** = `\Windows` → carpeta principal del sistema
  
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

  <img width="929" height="769" alt="Captura de pantalla de 2026-04-28 08-09-00" src="https://github.com/user-attachments/assets/88067ef0-a555-4a83-b453-69225cba4ca0" />


- **Pas 24** Configurar IP dinàmica (DHCP automàtic)

  <img width="929" height="769" alt="Captura de pantalla de 2026-04-28 08-11-15" src="https://github.com/user-attachments/assets/def6d1f0-1c5a-4275-8f26-4353c4dd25eb" />


- **Pas 25** Configurar IP fixa (manual: IP, màscara, gateway, DNS)

  <img width="851" height="773" alt="Captura de pantalla de 2026-04-28 08-16-51" src="https://github.com/user-attachments/assets/bbd9d1fd-185e-43c1-b18a-72a76304a46e" />

  
- **Pas 26** Comprovar connexió amb: `ping google.com`

  <img width="866" height="607" alt="Captura de pantalla de 2026-04-28 08-18-28" src="https://github.com/user-attachments/assets/e6640486-f188-4e13-990b-27aa1ce7f246" />

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

   <img width="885" height="766" alt="Captura de pantalla de 2026-04-28 08-32-51" src="https://github.com/user-attachments/assets/217c2ccd-58ff-4cde-b51f-e295ea0bb975" />

- **Pas 30** Comandes útils del sistema
  - `tasklist` → veure processos actius
  
  <img width="595" height="726" alt="Captura de pantalla de 2026-04-28 08-34-29" src="https://github.com/user-attachments/assets/7197c92a-d32e-4ce3-a00d-29e87ff6a603" />

  - `taskkill /IM notepad.exe /F` → tancar un procés
 
    <img width="780" height="312" alt="Captura de pantalla de 2026-04-28 08-36-50" src="https://github.com/user-attachments/assets/2bed84d2-c56d-4215-90ef-5b0a74a40cbd" />
    
    <img width="593" height="205" alt="Captura de pantalla de 2026-04-28 08-38-27" src="https://github.com/user-attachments/assets/9806b60d-97c8-4f91-8aa8-eb1a75f5d3d3" />

  - `systeminfo` → informació completa del sistema

   <img width="775" height="737" alt="Captura de pantalla de 2026-04-28 08-40-48" src="https://github.com/user-attachments/assets/a745a941-c884-4c00-963c-e18022930ded" />

  - `hostname` → nom de l'equip
  - `whoami` → usuari actual
 
    <img width="209" height="126" alt="Captura de pantalla de 2026-04-28 08-41-37" src="https://github.com/user-attachments/assets/4aafbe09-bea0-4a3b-b067-a94575c5dcf1" />

- **Pas 31** Comandes de xarxa
  - `ipconfig` → veure configuració IP
  - `ping google.com` → comprovar connexió

   <img width="555" height="429" alt="Captura de pantalla de 2026-04-28 08-43-17" src="https://github.com/user-attachments/assets/f48b6188-dcae-418d-87dc-0e93bb4c878c" />

    
  - `netstat -an` → connexions obertes
 
  <img width="526" height="679" alt="Captura de pantalla de 2026-04-28 08-43-30" src="https://github.com/user-attachments/assets/6464c584-a328-4c08-9482-3be8840d3b5a" />

- **Pas 32** Comandes interessants (una mica més avançades)
  - `tree` → veure estructura de carpetes
    
    <img width="449" height="395" alt="Captura de pantalla de 2026-04-28 08-44-31" src="https://github.com/user-attachments/assets/3fd37947-4ac9-442c-8734-6ae192a503f6" />

  - `cls` → netejar pantalla
 
    <img width="408" height="152" alt="Captura de pantalla de 2026-04-28 08-45-13" src="https://github.com/user-attachments/assets/b42b252c-6c72-4e0e-ab4c-97ade2ddca51" />

  - `help` → veure ajuda
 
    <img width="603" height="718" alt="Captura de pantalla de 2026-04-28 08-45-33" src="https://github.com/user-attachments/assets/8be71056-a209-4e75-87c6-a8a660cbe24e" />

  - `shutdown /s /t 0` → apagar l'equip
 
    <img width="305" height="61" alt="Captura de pantalla de 2026-04-28 08-46-21" src="https://github.com/user-attachments/assets/720a718d-2805-45fa-a611-6e0c98c1ccf4" />

- **Pas 33** Mini interpretació
  - Indicar què mostra `tasklist`
    - `tasklist` mostra → llista de tots els processos que s'estan executant
  - Indicar què mostra `ipconfig`
     - `ipconfig` mostra → la configuració de xarxa de l'equip (IP, màscara, gateway)
  - Indicar què mostra `systeminfo`
     - `systeminfo` mostra → informació detallada del sistema (OS, RAM, processador...)

---

## Fase 7 – Instal·lació d'aplicacions

- **Pas 34** Descarregar un programa des del navegador (ex: Chrome o VS Code)

  <img width="914" height="716" alt="Captura de pantalla de 2026-04-28 08-51-03" src="https://github.com/user-attachments/assets/cce2ec8e-fa0c-45da-860e-f8359d4a3850" />

- **Pas 35** Instal·lar-lo seguint l'assistent

  <img width="914" height="716" alt="Captura de pantalla de 2026-04-28 08-52-16" src="https://github.com/user-attachments/assets/a22d7de2-edde-48de-acd0-cffd8d6c7434" />
   
- **Pas 36** Obrir-lo i comprovar que funciona
- 
  <img width="1021" height="809" alt="Captura de pantalla de 2026-04-28 08-54-04" src="https://github.com/user-attachments/assets/dd0b3570-82f1-45de-8949-0f70de01e398" />

- **Pas 37** Instal·lar una aplicació des de Microsoft Store
  
  <img width="798" height="640" alt="Captura de pantalla de 2026-04-28 08-56-13" src="https://github.com/user-attachments/assets/917ed88e-fafb-49b4-b00c-481ebd5ccf0f" />

- **Pas 38** Obrir-la i comprovar funcionament

  <img width="1021" height="812" alt="Captura de pantalla de 2026-04-28 09-02-24" src="https://github.com/user-attachments/assets/9c4e5480-4494-49ca-825b-451a478d2b72" />

- **Pas 39** Desinstal·lar una aplicació: *Configuració → Aplicacions → Desinstal·lar*

  <img width="1021" height="812" alt="Captura de pantalla de 2026-04-28 09-04-38" src="https://github.com/user-attachments/assets/a5cec6e2-8a6f-457f-a4fd-d75ce42b94ff" />

  <img width="1021" height="812" alt="Captura de pantalla de 2026-04-28 09-04-46" src="https://github.com/user-attachments/assets/5bf3417a-ecb7-4e1d-a800-6488bdfc0bcf" />

- **Pas 40** Verificació: *Comprovar que el programa ja no apareix al sistema*
  
  <img width="1021" height="812" alt="Captura de pantalla de 2026-04-28 09-04-52" src="https://github.com/user-attachments/assets/17f097f5-0a81-484b-84a9-4e5cf4214eb9" />
