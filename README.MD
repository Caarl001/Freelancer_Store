Proyecto en el cual crearemos una pagina web de contenido de Freelancer
### INFORMACION ###
pwd significa print working directory, o sea "imprime el directorio de trabajo"

---

# Guía: conectar el proyecto local con GitHub

## Conceptos básicos

- **Repositorio local**: la carpeta del proyecto en tu computador, controlada por Git.
- **Repositorio remoto**: la copia del proyecto que vive en GitHub.
- **Commit**: una "foto" guardada del estado de tus archivos.
- **Rama (branch)**: una línea de trabajo. La principal suele llamarse `main` (antes se usaba `master`).
- **origin**: el nombre (apodo) que se le da por defecto a la dirección del repositorio remoto.

## Paso 1: Crear el repositorio en GitHub

1. Entrar a https://github.com e iniciar sesión.
2. Arriba a la derecha: **+** → **New repository**.
3. Escribir el nombre del repositorio (en este proyecto: `Freelancer_Storer`).
4. Elegir **Public** o **Private**.
5. **NO** marcar "Add a README", ".gitignore" ni "license" si el proyecto local ya tiene commits.
   Si se marcan, GitHub crea archivos que el proyecto local no tiene y eso provoca conflictos al subir.
6. Clic en **Create repository** y copiar la URL que aparece:
   ```
   https://github.com/Caarl001/Freelancer_Storer.git
   ```

## Paso 2: Conectar el proyecto local con GitHub

En la terminal de VS Code (`Ctrl + ñ`), dentro de la carpeta del proyecto:

```bash
git remote add origin https://github.com/Caarl001/Freelancer_Storer.git
git branch -M main
git push -u origin main
```

| Comando | Qué hace |
|---|---|
| `git remote add origin <url>` | Guarda la dirección de GitHub con el apodo `origin`. |
| `git branch -M main` | Renombra la rama actual a `main` (opcional; si no, usar `master` en el push). |
| `git push -u origin main` | Sube los commits a GitHub y deja la rama enlazada, para que después baste con `git push`. |

La primera vez se abre una ventana para iniciar sesión en GitHub: hay que autorizar.

## Error que nos apareció: `remote origin already exists`

```
git remote add origin https://github.com/Caarl001/Freelancer_Storer.git
error: remote origin already exists.
```

**Qué significa:** el proyecto ya tenía un `origin` configurado, apuntando a otra dirección
(`https://github.com/Caarl001/Store_freelancer.git`). Git no permite dos remotos con el mismo nombre.

**Cómo revisarlo:**
```bash
git remote -v
```

**Cómo solucionarlo** (cambiar la dirección del `origin` existente en vez de crear otro):
```bash
git remote set-url origin https://github.com/Caarl001/Freelancer_Storer.git
git remote -v
```

Otra opción es borrar el remoto y volver a agregarlo:
```bash
git remote remove origin
git remote add origin https://github.com/Caarl001/Freelancer_Storer.git
```

> Ojo: el nombre en la URL debe ser **exactamente** igual al del repositorio en GitHub
> (mayúsculas, guiones bajos, letras). Si no coincide, aparece el error `repository not found`.

## Paso 3: Verificar

```bash
git remote -v
```
Debe mostrar la URL correcta. Luego, al recargar la página del repositorio en GitHub, deben aparecer los archivos.

## Flujo de trabajo diario

Cada vez que hagas cambios:

```bash
git status                          # ver qué archivos cambiaron
git add .                           # preparar todos los cambios
git commit -m "Describe el cambio"  # guardar una "foto" con un mensaje
git push                            # subir los cambios a GitHub
```

## Resumen de comandos útiles

| Comando | Para qué sirve |
|---|---|
| `pwd` | Muestra en qué carpeta estás. |
| `git status` | Muestra el estado de los archivos. |
| `git branch` | Lista las ramas y marca con `*` la actual. |
| `git log --oneline` | Muestra el historial de commits resumido. |
| `git remote -v` | Muestra a qué repositorio remoto está conectado el proyecto. |
| `git remote set-url origin <url>` | Cambia la dirección del remoto `origin`. |
| `git push` | Sube los commits a GitHub. |
| `git pull` | Trae los cambios desde GitHub. |
