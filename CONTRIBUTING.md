# Guía de contribución

Este repositorio sigue **GitHub Flow**. `main` está protegida por el ruleset
`Proteccion-main`: no acepta pushes directos, todo cambio entra por Pull Request.

## 1. Partir de `main` actualizada

```bash
git switch main
git pull origin main
```

Este paso evita la mayoría de los conflictos. Si creas la rama desde una `main` vieja,
tu PR va a aparecer "behind" y puede marcar conflictos.

## 2. Crear tu rama

```bash
git switch -c feature/mi-tarea-minombre
```

Nomenclatura: prefijo (`feature/`, `fix/`, `docs/`), minúsculas, guiones en lugar de
espacios, sin acentos, y el nombre debe describir la tarea.

| Correcto | Incorrecto | Por qué |
|---|---|---|
| `feature/pruebas-automatizadas-axel` | `Axel branch` | Espacios y sin prefijo |
| `docs/actualizar-readme` | `docs/Actualizar_README` | Mayúsculas y guion bajo |
| `fix/validacion-login` | `arreglos` | No describe la tarea |

## 3. Hacer commits atómicos

```bash
git status
git diff
git add minombre.md
git commit -m "Add: información de MiNombre al equipo"
```

Un commit = un cambio coherente. Prefijos permitidos: `Add`, `Update`, `Fix`, `Remove`.
Revisa siempre `git status` y `git diff --staged` antes de confirmar, para no incluir
archivos que no pertenecen al cambio.

## 4. Publicar la rama

```bash
git push -u origin feature/mi-tarea-minombre
```

## 5. Abrir el Pull Request

Destino: `main`. El título usa el mismo formato que el commit. La descripción se llena con
la [plantilla de PR](.github/pull_request_template.md) y debe responder:

- **Qué** se agregó o cambió.
- **Por qué** era necesario.
- **Evidencia** del cambio (rama, commit, salida de `git diff --stat`, capturas).

Además hay que marcar el checklist de la plantilla antes de pedir revisión.

## 6. Revisión por pares

Al menos un compañero revisa y comenta antes del merge. La revisión es sobre el trabajo,
nunca sobre la persona: comentarios concretos, accionables y respetuosos.

Ejemplos de comentarios útiles:

- "Buen uso de la nomenclatura en la rama."
- "Sugiero agregar tu rol completo, quedó abreviado."
- "El commit está claro y el alcance coincide con el título."
- "Este archivo duplica `kevin.md`, ¿lo consolidamos?"

Si te piden cambios, corriges en la **misma rama** y vuelves a hacer push: el PR se
actualiza solo, no hace falta abrir otro.

## 7. Merge y limpieza

Con el PR aprobado:

```bash
# Desde la interfaz de GitHub, o con la CLI
gh pr merge <numero> --merge --delete-branch
```

Después sincroniza tu copia local y limpia las ramas ya integradas:

```bash
git switch main
git pull origin main
git fetch --prune
```

## Resolución de conflictos

Los conflictos se resuelven **en tu rama**, nunca en `main`:

```bash
git switch feature/mi-rama
git fetch origin
git merge origin/main
# Git marca los archivos en conflicto. Los editas y eliges qué queda.
git add <archivos-resueltos>
git commit -m "Fix: resolver conflictos con main"
git push
```

## Errores comunes

| Situación | Qué hacer |
|---|---|
| `GH006: Protected branch update failed` | Intentaste push directo a `main`. Crea una rama y abre un PR. |
| Trabajaste por error en `main` | `git switch -c feature/mi-rama` conserva tus commits en una rama nueva. |
| El PR dice "This branch is out-of-date" | `git merge origin/main` en tu rama y vuelve a hacer push. |
| Subiste un archivo que no querías | `git rm --cached <archivo>`, agrégalo al `.gitignore` y haz un commit nuevo. |
