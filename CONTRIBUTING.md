# Guía de Contribución — Salud Natura

Marco de trabajo para el equipo de desarrollo (y sus IAs) del proyecto `saludnatura.graduadosfiuba.org`.

## Principios

- Modelo de ramas: **`feature/* → main`** (integración directa a `main` mediante PR).
- `main` (producción) es una **rama protegida**. **No se pushea directo** a ella.
- Todo cambio se hace en una **rama propia** y se integra mediante **Pull Request (PR)** a `main`, revisado y con CI en verde.
- Desarrollo guiado por **SDD + Tests**: spec primero (`TODO/specs/`), test primero, luego implementación (ver `.agents/agent.md`, Secciones 9 y 10).

## Ramas

Crear siempre desde `main` actualizado. Convención de nombres:

| Prefijo      | Uso                                   | Ejemplo                      |
|--------------|---------------------------------------|------------------------------|
| `feature/`   | Nueva característica                   | `feature/remedio-api`        |
| `fix/`       | Corrección de bug                      | `fix/validacion-email`       |
| `chore/`     | Tareas varias / configuración          | `chore/actualizar-deps`      |
| `docs/`      | Documentación                          | `docs/readme-deploy`         |
| `refactor/`  | Refactor sin cambio funcional          | `refactor/servicio-remedios` |

Una rama = una unidad de trabajo acotada. Ramas cortas y enfocadas.

## Commits (Conventional Commits)

```
feat: agrega endpoint de registro de usuarios
fix: corrige validacion de celular
docs: documenta flujo de deploy
chore: actualiza dependencias
refactor: simplifica consulta a base de datos
```

## Ciclo de trabajo

```bash
# 1. Partir de main actualizado
git checkout main
git pull origin main

# 2. Crear la rama de trabajo
git checkout -b feature/mi-caracteristica

# 3. Trabajar con SDD (spec -> test -> implementar) y commitear
git add -A
git commit -m "feat: ..."

# 4. Publicar la rama
git push -u origin feature/mi-caracteristica

# 5. Abrir el Pull Request en GitHub con base 'main'
# 6. Tras aprobación + CI/tests verdes: merge (squash) y borrar la rama
```

## Metodología SDD (Spec-Driven Development)

Antes de implementar una feature o cambio no trivial:

1. Copiar `TODO/specs/_PLANTILLA/` a `TODO/specs/<feature>/`.
2. Completar el trío: **`spec.md`** (qué/por qué + criterios), **`plan.md`** (cómo) y **`tasks.md`** (checklist).
3. Escribir los tests primero (rojo) y luego implementar (verde).

Ejemplo de referencia: `TODO/specs/usuarios_endpoint/` + `tests/test_usuarios.py`.

## Integración Continua (CI)

GitHub Actions (`.github/workflows/ci.yml`) correrá en cada push/PR a `main` una vez configurado: **Lint (Ruff)**, **Dependencias**, **Docker build** y **Tests (pytest)**. El PR debe quedar con el CI en verde.

## Checklist del Pull Request

- [ ] Rama nombrada según la convención y con base `main`.
- [ ] Spec creada/actualizada (si aplica) en `TODO/specs/<feature>/`.
- [ ] CI en verde (lint + build + tests).
- [ ] Tests nuevos/actualizados y **en verde** (`pytest -q`).
- [ ] **Sin secretos en el diff** (nunca commitear `.env`, contraseñas, tokens ni claves).
- [ ] Descripción del PR explica el **qué**, el **por qué** y **cómo probarlo**.
- [ ] Al menos **1 review aprobado**.

## Seguridad y secretos

- Los secretos reales viven **solo** en `.env` (gitignored) o en las variables de entorno del servidor de hosting.
- `.env.example` documenta las variables con **placeholders**.
- Regla práctica: si un valor permite *autenticarse o tomar control* → es secreto y **no va al repo**.

## Tests local

```bash
python -m venv .venv
.venv\Scripts\activate        # Windows
pip install -r requirements.txt
pip install pytest httpx       # Para testing local
pytest -q
```

---

Para el contexto completo del proyecto (arquitectura, deploy, skills), ver `.agents/agent.md`.

