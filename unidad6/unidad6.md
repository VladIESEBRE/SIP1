
# Guia Sprint 2 – Gestió de Discs, Quotes, Scripts i Permisos

---

## Fase 1 – Preparació del sistema

### Pas 1. Afegir un nou disc virtual a la màquina virtual

<img width="924" height="821" alt="Captura de pantalla de 2026-05-07 08-28-38" src="https://github.com/user-attachments/assets/2335a10b-6906-43a1-9185-235be49428e2" />

### Pas 2. Iniciar Windows i obrir Gestió de discs

<img width="1021" height="809" alt="Captura de pantalla de 2026-05-07 08-32-50" src="https://github.com/user-attachments/assets/33284766-a1c8-40b2-8acf-e3b82a2905cd" />


### Pas 3. Inicialitzar el disc i crear les particions

<img width="1021" height="809" alt="Captura de pantalla de 2026-05-07 08-35-06" src="https://github.com/user-attachments/assets/0ec61904-4a92-40a8-8393-74caea513a28" />

<img width="1021" height="809" alt="Captura de pantalla de 2026-05-07 08-37-05" src="https://github.com/user-attachments/assets/bfffd8df-10c2-451a-bec8-acecd394e5fc" />

<img width="1021" height="809" alt="Captura de pantalla de 2026-05-07 08-37-41" src="https://github.com/user-attachments/assets/d8d3df31-e81c-4f8b-9659-e65290760ecf" />

<img width="1021" height="809" alt="Captura de pantalla de 2026-05-07 08-38-05" src="https://github.com/user-attachments/assets/13ebbd30-9165-40a6-ac1f-690b3be8fabd" />

<img width="1021" height="809" alt="Captura de pantalla de 2026-05-07 08-38-20" src="https://github.com/user-attachments/assets/a06d5016-7451-4bfc-b56b-e7aabd2bf87b" />


### Pas 4. Assignar lletres i comprovar amb diskpart

<img width="1021" height="809" alt="Captura de pantalla de 2026-05-07 08-40-53" src="https://github.com/user-attachments/assets/d17335da-5185-4218-b787-061ce03c751b" />

---

## Fase 2 – Quotes i usuaris

### Pas 5. Activar quotes de disc a la partició Dades (NTFS)

<img width="1022" height="810" alt="Captura de pantalla de 2026-05-07 08-45-23" src="https://github.com/user-attachments/assets/803cec91-2114-442a-b7fe-41012ca83753" />

### Pas 6. Establir límit de 300 MB per usuari

<img width="1022" height="810" alt="Captura de pantalla de 2026-05-07 08-46-54" src="https://github.com/user-attachments/assets/a0c64ea2-54dc-4b30-9128-fd3fc7ad70f2" />


### Pas 7. Crear dos usuaris locals

<img width="1022" height="810" alt="Captura de pantalla de 2026-05-07 08-49-58" src="https://github.com/user-attachments/assets/9126b17c-752e-45b3-8f32-971a3d85a1d5" />

### Pas 8. Crear el grup Limitats i afegir els usuaris

<img width="1022" height="810" alt="Captura de pantalla de 2026-05-07 08-52-39" src="https://github.com/user-attachments/assets/f68b6acf-7f27-4d45-95b1-0edd39fb4c79" />

### Pas 9. Provar les quotes

<img width="1020" height="807" alt="Captura de pantalla de 2026-05-07 09-13-05" src="https://github.com/user-attachments/assets/0f62a21f-c89a-427c-ace4-28a333863d20" />


---

## Fase 3 – Script de còpia i automatització

### Pas 10. Afegir tercer disc virtual i formatar-lo

<img width="1021" height="813" alt="Captura de pantalla de 2026-05-07 09-25-13" src="https://github.com/user-attachments/assets/57c0c3c9-49fd-40d5-ad15-2df886e1b7d0" />

<img width="1021" height="813" alt="Captura de pantalla de 2026-05-07 09-25-31" src="https://github.com/user-attachments/assets/fd78407f-4636-4e0a-9645-8123ee721012" />

### Pas 11. Crear la carpeta CòpiesUsuaris

<img width="1022" height="815" alt="Captura de pantalla de 2026-05-07 09-27-39" src="https://github.com/user-attachments/assets/a956ebec-83c3-45a4-b44c-8d4f1c3c3d83" />

### Pas 12. Crear l'script de còpia

Crea el fitxer `copia_usuari.bat` amb el contingut següent:

<img width="1022" height="813" alt="Captura de pantalla de 2026-05-07 09-36-52" src="https://github.com/user-attachments/assets/374200e5-8988-487b-96cb-167e4aa65a68" />

### Pas 13. Obrir gpedit.msc i anar als scripts d'inici de sessió

<img width="1022" height="813" alt="Captura de pantalla de 2026-05-07 09-41-29" src="https://github.com/user-attachments/assets/420d0873-840f-435d-b391-147299a560fd" />

### Pas 14. Assignar l'script als usuaris alumne1 i alumne2

<img width="1022" height="813" alt="Captura de pantalla de 2026-05-07 09-42-42" src="https://github.com/user-attachments/assets/08fdff6f-15c0-44b5-8613-40633a4bf577" />


---

## Fase 4 – Verificació i documentació

### Pas 15. Verificar que tot funciona correctament

<img width="1022" height="813" alt="Captura de pantalla de 2026-05-07 09-45-33" src="https://github.com/user-attachments/assets/bb59beff-38c2-40fb-961f-864df358a06c" />

<img width="1022" height="813" alt="Captura de pantalla de 2026-05-07 09-46-15" src="https://github.com/user-attachments/assets/31b36a80-7151-4e15-a63b-eec5f1fe5e4a" />

<img width="1022" height="813" alt="Captura de pantalla de 2026-05-07 09-46-29" src="https://github.com/user-attachments/assets/832c71a1-7db7-4f15-8c94-a2e2605f8398" />

<img width="1020" height="807" alt="Captura de pantalla de 2026-05-07 09-13-05" src="https://github.com/user-attachments/assets/5a373c1c-763f-4a38-a90d-c5fe6b26a58b" />

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
