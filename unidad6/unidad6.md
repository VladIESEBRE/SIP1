
# Guia Sprint 2 – Gestió de Discs, Quotes, Scripts i Permisos

---

## Fase 1 – Preparació del sistema

### Pas 1. Afegir un nou disc virtual a la màquina virtual

<img width="924" height="821" alt="Captura de pantalla de 2026-05-07 08-28-38" src="https://github.com/user-attachments/assets/2335a10b-6906-43a1-9185-235be49428e2" />

### Pas 2. Iniciar Windows i obrir Gestió de discs

<img width="1021" height="809" alt="Captura de pantalla de 2026-05-07 08-32-50" src="https://github.com/user-attachments/assets/33284766-a1c8-40b2-8acf-e3b82a2905cd" />


### Pas 3. Inicialitzar el disc i crear les particions
- Fes clic dret sobre el disc nou → **Inicialitzar disc** → tria `MBR` o `GPT`.
- Crea la primera partició:
  - Format: **NTFS**
  - Nom: `Dades`
- Crea la segona partició:
  - Format: **FAT32**
  - Nom: `Portable`

### Pas 4. Assignar lletres i comprovar amb diskpart
- Assigna lletres de unitat a cada partició (p. ex. `D:` i `E:`).
- Obre CMD com a administrador i executa:

```cmd
diskpart
list disk
list volume
```

- Comprova que les dues particions apareixen correctament.

---

## Fase 2 – Quotes i usuaris

### Pas 5. Activar quotes de disc a la partició Dades (NTFS)
- A l'Explorador de fitxers, fes clic dret sobre `D:` → **Propietats** → pestanya **Quota**.
- Activa **Habilitar la gestió de quotes**.

### Pas 6. Establir límit de 300 MB per usuari
- Marca **Denega espai al disc als usuaris que superin el límit de quota**.
- Estableix:
  - **Límit de quota:** `300 MB`
  - **Nivell d'advertència:** `250 MB`
- Fes clic a **Aplica**.

### Pas 7. Crear dos usuaris locals
Obre CMD com a administrador i executa:

```cmd
net user alumne1 Password1 /add
net user alumne2 Password2 /add
```

### Pas 8. Crear el grup Limitats i afegir els usuaris

```cmd
net localgroup Limitats /add
net localgroup Limitats alumne1 /add
net localgroup Limitats alumne2 /add
```

### Pas 9. Provar les quotes
- Inicia sessió com `alumne1`.
- Copia fitxers grans a `D:\` fins a superar els 300 MB.
- Comprova que el sistema bloqueja la còpia en arribar al límit.

---

## Fase 3 – Script de còpia i automatització

### Pas 10. Afegir tercer disc virtual i formatar-lo
- Afegeix un tercer disc virtual des del gestor de virtualització.
- A Gestió de discs, inicialitza'l i formata'l en **NTFS**.
- Nom: `Backups` (p. ex. lletra `E:`).

### Pas 11. Crear la carpeta CòpiesUsuaris

```cmd
mkdir E:\CòpiesUsuaris
```

### Pas 12. Crear l'script de còpia

Crea el fitxer `copia_usuari.bat` amb el contingut següent:

```bat
@echo off
xcopy /E /I /Y "C:\Users\%USERNAME%" "E:\CòpiesUsuaris\%USERNAME%"
```

Desa l'script en una ubicació accessible, per exemple: `C:\Scripts\copia_usuari.bat`

### Pas 13. Obrir gpedit.msc i anar als scripts d'inici de sessió

```
gpedit.msc
→ Configuració d'usuari
  → Configuració de Windows
    → Scripts (Inici i tancament de sessió)
      → Inici de sessió
```

### Pas 14. Assignar l'script als usuaris alumne1 i alumne2
- Fes doble clic a **Inici de sessió**.
- Fes clic a **Afegir** → busca `C:\Scripts\copia_usuari.bat`.
- Aplica i tanca.

---

## Fase 4 – Verificació i documentació

### Pas 15. Verificar que tot funciona correctament
- Inicia sessió com `alumne1`.
- Comprova que l'script ha creat la carpeta `E:\CòpiesUsuaris\alumne1` amb els fitxers.
- Intenta superar el límit de quota a `D:\` i verifica que el sistema ho bloqueja.
- Documenta les comprovacions amb captures de pantalla.

---

## Fase 5 – Gestió de processos i serveis

### Pas 19. Llistar processos actius

```cmd
tasklist
tasklist > C:\Users\%USERNAME%\processos_inici.txt
```

Processos típics que pots observar: `explorer.exe`, `SearchIndexer.exe`, `OneDrive.exe`.

### Pas 20. Identificar processos prescindibles

Elabora una taula com la següent:

| Nom del procés | Memòria usada | Justificació per eliminar-lo |
|----------------|--------------|------------------------------|
| OneDrive.exe   | ~50 MB       | No necessari en entorn local |
| Teams.exe      | ~150 MB      | No necessari per a l'usuari  |
| SkypeApp.exe   | ~80 MB       | No s'utilitza en aquest context |

### Pas 21. Eliminar processos manualment

```cmd
taskkill /IM OneDrive.exe /F
tasklist
```

> Fes una captura de pantalla **abans** i **després** d'executar la comanda.

### Pas 22. Automatitzar la fi de processos a l'inici de sessió

Afegeix les línies següents a l'script `copia_usuari.bat`:

```bat
taskkill /IM OneDrive.exe /F
taskkill /IM Teams.exe /F
```

- Tanca la sessió i inicia com `alumne2`.
- Comprova que els processos no s'executen.

### Pas 23. Documentació
- Afegeix el fitxer `processos_inici.txt` i la taula justificativa a la documentació amb **MkDocs**.
- Explica què passa si mates un procés crític com `explorer.exe` (prova controlada).
- Comenta com aquesta gestió pot millorar el rendiment en màquines virtuals o amb pocs recursos.

---

## Fase 6 – Gestió de permisos (ACLs)

### Concepte: Què són les ACLs?

A Windows, cada fitxer i carpeta té una **llista de control d'accés (ACL)**. Cada entrada es diu **ACE** (Access Control Entry) i defineix:
- Quina identitat (usuari o grup) és afectada.
- Quins permisos té (lectura, escriptura, execució, control total, etc.).

Les ACLs permeten:
- Configurar permisos per fitxer o carpeta específica.
- Aplicar-se tant a usuaris com a grups.
- Combinar permisos personalitzats.
- Heretar-se d'una carpeta superior o assignar-se manualment.

> **Objectiu d'aquesta fase:** El grup `Limitats` tindrà control total sobre `D:\Projectes`, però `alumne2` tindrà només lectura, tot i pertànyer al grup.

### Pas 24. Crear la carpeta Projectes

Inicia sessió com a administrador i executa:

```cmd
mkdir D:\Projectes
```

### Pas 25. Assignar permisos al grup Limitats
1. Fes clic dret sobre `D:\Projectes` → **Propietats** → pestanya **Seguretat**.
2. Fes clic a **Avançat** → **Desactiva la herència** → **Conserva els permisos existents**.
3. Elimina les entrades de `Users` o `Everyone` si hi apareixen.
4. Fes clic a **Afegir** → busca el grup `Limitats` → dona-li **Control total**.
5. Aplica els canvis.

### Pas 26. Comprovar accés amb alumne1
- Inicia sessió com `alumne1`.
- Crea un fitxer dins `D:\Projectes`, modifica'l i elimina'l.
- Tot hauria de funcionar correctament (permisos heretats del grup `Limitats`).

### Pas 27. Aplicar excepció per alumne2

Torna a iniciar sessió com a administrador i executa:

```cmd
icacls "D:\Projectes" /grant:r alumne2:(R)
```

Això substitueix qualsevol permís anterior d'`alumne2` i li dona **només lectura**.

### Pas 28. Comprovar l'excepció amb alumne2
- Inicia sessió com `alumne2`.
- Intenta **obrir** un fitxer → ha de poder llegir-lo ✅
- Intenta **editar-lo o crear-ne un de nou** → ha de rebre un missatge de denegació ❌

### Pas 29. Consultar els permisos aplicats

Torna a la consola com a administrador i executa:

```cmd
icacls "D:\Projectes"
```

La sortida hauria de mostrar:

```
D:\Projectes
  Limitats:(OI)(CI)(F)
  alumne2:(R)
```

Això confirma que el grup té **control total** i `alumne2` té **només lectura**.

---

> **Nota final:** Documenta cada fase amb captures de pantalla i afegeix-les a la documentació del projecte (MkDocs o similar).
