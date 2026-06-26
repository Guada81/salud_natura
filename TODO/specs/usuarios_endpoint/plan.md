# Plan de Implementación: Endpoint de registro de usuarios

## Archivos a crear/modificar

| Archivo | Acción | Descripción |
|---|---|---|
| `app/main.py` | EXISTENTE | Endpoint `/api/usuarios` (POST) y modelo `UsuarioIn` ya implementados. |
| `tests/conftest.py` | CREAR | Fixture `client` con `TestClient` de FastAPI. |
| `tests/test_health.py` | CREAR | Test del healthcheck. |
| `tests/test_usuarios.py` | CREAR | Tests de happy-path, validación y almacenamiento en base de datos de usuarios. |

## Dependencias
- `pytest` y `httpx` (para `TestClient`). Se instalan para testing local (`pip install pytest httpx`).

## Consideraciones técnicas
- El almacenamiento es persistente en SQLite en la tabla `usuarios_y_clientes`. Los tests deben ejecutarse garantizando que no se ensucie la base de datos de desarrollo, o limpiando la base de datos tras las pruebas.
- La validación de `UsuarioIn` se realiza de forma automática mediante Pydantic y FastAPI, arrojando error `422` en caso de entrada mal estructurada.

