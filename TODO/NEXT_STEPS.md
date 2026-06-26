# NEXT_STEPS — Salud Natura

**Source of Truth** del desarrollo activo. Actualizar al cerrar hitos.

---

## 🟢 Estado actual

| Área | Estado |
|------|--------|
| **Grimorio (FastAPI + Jinja2)** | ✅ Funcionando (`/` con listado, `/health`) |
| **API de Remedios** | ✅ ABM básico en SQLite (`GET /api/remedios`, `GET /api/remedios/{id}`, `POST /api/remedios`) |
| **Registro de Usuarios (Leads)** | ✅ Almacenamiento en SQLite (`POST /api/usuarios`) |
| **Docker** | ✅ `Dockerfile` y `docker-compose.yml` configurados |
| **Deploy** | ⏳ Pendiente definir y montar hosting web |
| **Marco de trabajo (SDD + Git)** | ✅ Establecido |
| **Tests** | ⏳ Pendiente (crear estructura de tests con `pytest` y `httpx`) |

---

## 🚀 Próximos pasos

### Infraestructura y Deploy
- [ ] Definir hosting para desplegar la aplicación Salud Natura.
- [ ] Activar protección de la rama `main` en GitHub (ver `docs/technical/guides/CONFIGURACION_PROTECCION_RAMAS.md`).

### Frontend y Diseño (Identidad Visual)
- [ ] Sustituir las imágenes de la plantilla por fotos propias y logo oficial (Opción C - Árbol de la Vida con nudos celtas).
- [ ] Diseñar y enlazar la descarga del Lead Magnet (PDF místico).
- [ ] Mejorar la estética del catálogo interactivo "El Grimorio" siguiendo los pilares de la marca (Saber Científico, Tradición Alquímica, Conexión Espiritual).

### Producto e Integraciones (Fase 2)
- [ ] Implementar la base de datos de productos de afiliados (Amazon/Mercado Libre) en `CATALOGO_PRODUCTOS_EXTERNAL`.
- [ ] Configurar la red de herbolarios/franquicias con geolocalización de cercanía (`RED_FRANQUICIAS`).
- [ ] Diseñar panel de administración interno para visualización de usuarios registrados y geolocalización.

### Calidad
- [ ] Crear test suite inaugural (`tests/conftest.py`, `tests/test_health.py` y `tests/test_usuarios.py`).
- [ ] Configurar Ruff como linter y formateador pre-commit.

