
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

<img width="1016" height="817" alt="Captura de pantalla de 2026-05-07 09-55-02" src="https://github.com/user-attachments/assets/07d7bcda-5223-4f4b-8429-af15d6c7a6ab" />

<img width="1017" height="810" alt="Captura de pantalla de 2026-05-07 09-58-16" src="https://github.com/user-attachments/assets/60faada8-05dd-45ef-9ef1-783fc5ad6709" />


### Pas 20. Identificar processos prescindibles

| Nom del procés | Memòria usada | Justificació per eliminar-lo |
|----------------|--------------|------------------------------|
| OneDrive.exe   | 97.048 KB    | Sincronització al núvol no necessària en entorn local |
| SearchIndexer.exe      | 33.248 KB      | Indexació de cerca, no essencial en MV de pràctiques  |
| MsMpEng.exe   | 229.572 KB       | Windows Defender, consumeix recursos en MV |

<img width="751" height="525" alt="Captura de pantalla de 2026-05-07 10-01-54" src="https://github.com/user-attachments/assets/edc9fe1d-2752-4118-8600-4caf73fe5d0f" />

<img width="751" height="525" alt="Captura de pantalla de 2026-05-07 10-04-21" src="https://github.com/user-attachments/assets/178999b1-830a-4d1d-864b-4048f028ff45" />

<img width="751" height="525" alt="Captura de pantalla de 2026-05-07 10-04-42" src="https://github.com/user-attachments/assets/ce060e4e-01aa-4803-9052-93aa8043e676" />

### Pas 21. Eliminar processos manualment

<img width="1019" height="815" alt="Captura de pantalla de 2026-05-07 10-08-56" src="https://github.com/user-attachments/assets/30a866c1-1110-4c1f-bf64-9a3d021c30ba" />

<img width="616" height="107" alt="Captura de pantalla de 2026-05-07 10-31-41" src="https://github.com/user-attachments/assets/74c42b4f-f11c-4940-8121-553859a2508d" />

 - Els processos d'OneDrive només es poden tancar amb permisos d'administrador. Els usuaris del grup Limitats no tenen aquests privilegis, per tant el script s'ha d'executar com a administrador o desactivar OneDrive des del registre.
   
<img width="684" height="515" alt="Captura de pantalla de 2026-05-07 10-38-58" src="https://github.com/user-attachments/assets/2a21ee32-8297-464a-8541-99a5144b02b0" />

### Pas 22. Automatitzar la fi de processos a l'inici de sessió

<img width="1018" height="810" alt="Captura de pantalla de 2026-05-07 10-19-07" src="https://github.com/user-attachments/assets/febdd8e3-8294-4677-96b9-9916ab908629" />

<img width="673" height="124" alt="Captura de pantalla de 2026-05-07 10-43-46" src="https://github.com/user-attachments/assets/7b5d3db7-8d3a-425b-be78-7ed413da9682" />

### Pas 23. Documentació
#### Explica què passa si mates un procés crític com `explorer.exe` (prova controlada).
- Si tanquem explorer.exe el escriptori desapareix completament, no hi ha barra de tasques ni icones. Es pot recuperar obrint el Administrador de tasques (Ctrl+Shift+Esc) → Archivo → Ejecutar nueva tarea → escriure explorer.exe. És un procés crític que no s'ha d'eliminar mai en producció.

  <img width="1018" height="812" alt="Captura de pantalla de 2026-05-07 10-51-10" src="https://github.com/user-attachments/assets/88edd788-8a6a-4ea1-9e6a-cbfb93914aaa" />

  <img width="1018" height="812" alt="Captura de pantalla de 2026-05-07 10-51-21" src="https://github.com/user-attachments/assets/cf7b436c-c720-47ee-975e-27bb52e486d6" />

  <img width="1018" height="812" alt="Captura de pantalla de 2026-05-07 10-52-12" src="https://github.com/user-attachments/assets/6b738566-81b6-463b-bfb7-86c0de715387" />

  <img width="1018" height="812" alt="Captura de pantalla de 2026-05-07 10-52-22" src="https://github.com/user-attachments/assets/67f3f2bb-f1b3-459c-9a8b-1c71eac93bcb" />


#### Comenta com aquesta gestió pot millorar el rendiment de màquines virtuals o amb pocs recursos​
- En màquines virtuals amb pocs recursos, tancar processos no essencials com OneDrive allibera memòria RAM i CPU. Això és especialment útil en entorns de pràctiques on la MV té assignada poca memòria.

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

<img width="1018" height="814" alt="Captura de pantalla de 2026-05-07 11-33-39" src="https://github.com/user-attachments/assets/78f40238-9db0-4188-9301-320a7cee386c" />

<img width="1018" height="814" alt="Captura de pantalla de 2026-05-07 11-35-37" src="https://github.com/user-attachments/assets/82238be9-97b8-45e0-baa1-152acad053fb" />

<img width="1018" height="814" alt="Captura de pantalla de 2026-05-07 11-35-47" src="https://github.com/user-attachments/assets/66639b6e-2915-4391-8949-3826738a427e" />

<img width="1018" height="814" alt="Captura de pantalla de 2026-05-07 11-38-12" src="https://github.com/user-attachments/assets/9f7bbf54-5324-4151-a243-30fe66af4705" />

<img width="1018" height="814" alt="Captura de pantalla de 2026-05-07 11-38-23" src="https://github.com/user-attachments/assets/0201e49a-fa63-4fb2-a565-9744bba35bea" />

<img width="1018" height="814" alt="Captura de pantalla de 2026-05-07 11-38-31" src="https://github.com/user-attachments/assets/e561210a-e171-44d5-92d9-415c8614be47" />

### Pas 26. Comprovar accés amb alumne1

<img width="1049" height="847" alt="Captura de pantalla de 2026-05-07 11-51-49" src="https://github.com/user-attachments/assets/fcd0cb0a-7629-4efb-900f-955526db4c34" />

<img width="1049" height="847" alt="Captura de pantalla de 2026-05-07 11-52-23" src="https://github.com/user-attachments/assets/b0165adc-ec66-4d71-b5a9-fba7041336b1" />

### Pas 27. Aplicar excepció per alumne2

<img width="1049" height="845" alt="Captura de pantalla de 2026-05-07 11-55-53" src="https://github.com/user-attachments/assets/7950e3c6-3059-4fbb-8a0e-f23dd1e1c4c7" />

 - Això substitueix qualsevol permís anterior d'`alumne2` i li dona **només lectura**.

### Pas 28. Comprovar l'excepció amb alumne2

 - Primer s'ha executat el comando del enunciat:

```cmd
icacls "E:\Projectes" /grant:r alumne2:(R)
```

<img width="1049" height="845" alt="Captura de pantalla de 2026-05-07 11-55-53" src="https://github.com/user-attachments/assets/92cc3122-5d49-4443-9e6d-127e5661e68c" />


 - Però alumne2 encara podia editar fitxers degut a que els permisos 
del grup Limitats (Control total) tenien prioritat sobre el /grant.

<img width="1051" height="879" alt="Captura de pantalla de 2026-05-07 12-12-48" src="https://github.com/user-attachments/assets/98343e4a-78c8-4f95-95fa-cd2d01f9935e" />

 - Per solucionar-ho s'ha afegit una denegació explícita:

```cmd
icacls "E:\Projectes" /deny alumne2:(W,D,DC,WD)
```
<img width="1051" height="879" alt="Captura de pantalla de 2026-05-07 12-14-50" src="https://github.com/user-attachments/assets/e62907ed-980f-44c9-82c7-838f872ce914" />

- A Windows, les **denegacions explícites sempre tenen prioritat** sobre els permisos de grup, per tant encara que Limitats tingui Control total, alumne2 no pot escriure.

<img width="1043" height="840" alt="Captura de pantalla de 2026-05-07 12-02-33" src="https://github.com/user-attachments/assets/0be99e47-5cfd-4773-8cfd-64140d558277" />


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
