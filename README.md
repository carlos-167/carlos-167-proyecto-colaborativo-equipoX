# carlos-167-proyecto-colaborativo-equipoX

Repositorio colaborativo del **Equipo X**.

## Objetivo del repositorio

Practicar y evidenciar el flujo de trabajo profesional de control de versiones con Git y
GitHub. Cada integrante documenta su rol en un archivo propio, pero el entregable real es
**el proceso**: ramas con nomenclatura correcta, commits atómicos, Pull Requests revisados
por los compañeros e integración limpia a `main`.

Objetivos concretos:

- Demostrar dominio de `commit`, `branch`, `merge` y Pull Request.
- Aplicar buenas prácticas de colaboración y revisión de código entre pares.
- Mantener `main` siempre estable, sin conflictos y sin pushes directos.
- Simular el flujo real de integración continua de un equipo de desarrollo.

## Equipo

**Nombre del equipo:** Equipo X

| Integrante | Usuario de GitHub | Rol declarado | Tarea asignada |
|---|---|---|---|
| Carlos | [@carlos-167](https://github.com/carlos-167) | DevOps Engineer | Autenticación de usuarios |
| Alexis | [@alexisTG2004](https://github.com/alexisTG2004) | DevOps Engineer | Desarrollo de API CRUD |
| Aramis | [@aramis-lopez](https://github.com/aramis-lopez) | DevOps Engineer | Diseño del panel de control |
| Axel | [@AxelOrtiz31](https://github.com/AxelOrtiz31) | DevOps Engineer | Pruebas automatizadas |
| Elsy | [@elsyyanez](https://github.com/elsyyanez) | DevOps Engineer / Database Specialist | Bases de datos |
| Erik | [@Erik2259](https://github.com/Erik2259) | DevOps Engineer | Contenedorización con Docker |
| Kevin | [@KFPympex](https://github.com/KFPympex) | Integración y consumo de API | Integración y consumo de API |
| Erick Alexander | [@ErickrU](https://github.com/ErickrU) | DevOps Engineer | Documentación del proyecto |

Ficha de cada integrante: [`carlos.md`](carlos.md) · [`alexis.md`](alexis.md) ·
[`aramis.md`](aramis.md) · [`Axel.md`](Axel.md) · [`elsy.md`](elsy.md) ·
[`erik.md`](erik.md) · [`kevin.md`](kevin.md) · [`erick-alexander.md`](erick-alexander.md)

## Flujo de trabajo: GitHub Flow

Elegimos **GitHub Flow** por ser simple, continuo y el estándar para equipos que integran
cambios de forma frecuente. Reglas del equipo:

1. `main` siempre es estable y desplegable. **Nunca** se hace push directo a `main`.
2. Todo cambio nace en una rama descriptiva creada a partir de `main` actualizada.
3. Los commits son pequeños, atómicos y con mensajes claros.
4. El cambio se propone mediante un **Pull Request** hacia `main`.
5. Al menos un compañero **revisa y comenta** el Pull Request.
6. Una vez aprobado, se hace **merge** a `main` y se elimina la rama.

```text
main ─────●───────────────●───────────────●──────▶
           \             / \             /
            ●───────────●   ●───────────●
        feature/desarrollo-   feature/pruebas-
        api-crud-alexis       automatizadas-axel
```

### Nomenclatura de ramas

| Prefijo | Uso | Ejemplo |
|---|---|---|
| `feature/` | Nueva funcionalidad o contenido | `feature/desarrollo-api-crud-alexis` |
| `fix/` | Corrección de un defecto | `fix/enlace-roto-readme` |
| `docs/` | Cambios sólo de documentación | `docs/actualizar-flujo-trabajo` |

Reglas: todo en minúsculas, palabras separadas por guiones, sin espacios ni acentos, y el
nombre debe reflejar la tarea. Incluir el nombre del autor al final ayuda a identificar de
quién es la rama.

### Convención de mensajes de commit

Formato: `<Prefijo>: <descripción con contexto>`

| Prefijo | Cuándo usarlo | Ejemplo |
|---|---|---|
| `Add` | Se agrega algo nuevo | `Add: información de Kevin al equipo` |
| `Update` | Se modifica algo existente | `Update: mover archivo de Erik a la raíz` |
| `Fix` | Se corrige un error | `Fix: corregir enlace roto en el README` |
| `Remove` | Se elimina algo | `Remove: eliminar archivo duplicado` |

Un commit = un cambio coherente. No se aceptan mensajes como `cambios`,
`arreglos varios`, `add.` o `update` sin contexto.

## Protección de la rama `main`

`main` está protegida con el ruleset **Proteccion-main**:

| Regla | Estado |
|---|---|
| Push directo a `main` | Bloqueado, requiere Pull Request |
| Force push / reescritura de historial | Bloqueado |
| Borrado de la rama `main` | Bloqueado |
| Métodos de merge permitidos | merge, squash, rebase |

Si intentas `git push origin main` directamente, GitHub responde con el error
`GH006: Protected branch update failed` y rechaza el push. Es el comportamiento esperado:
todo entra por Pull Request.

## Estructura del repositorio

```text
.
├── .github/
│   └── pull_request_template.md   Plantilla de PR con checklist obligatorio
├── <nombre>.md                    Una ficha por integrante
├── CONTRIBUTING.md                Guía paso a paso de contribución
├── .gitignore
├── LICENSE                        MIT
└── README.md
```

## Cómo contribuir

El procedimiento completo está en [CONTRIBUTING.md](CONTRIBUTING.md). Resumen:

```bash
git switch main
git pull origin main
git switch -c feature/mi-tarea-minombre
# ...editar archivos...
git add minombre.md
git commit -m "Add: información de MiNombre al equipo"
git push -u origin feature/mi-tarea-minombre
# Abrir Pull Request hacia main y pedir revisión a un compañero
```

## Licencia

Distribuido bajo licencia MIT. Ver [LICENSE](LICENSE).
