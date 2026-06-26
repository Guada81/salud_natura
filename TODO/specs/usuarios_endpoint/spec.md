# Spec: Endpoint de registro de usuarios

## Resumen
Endpoint que recibe los datos de registro de un usuario o cliente desde el frontend de Salud Natura y los persiste en la base de datos SQLite. Es la primera spec del proyecto y sirve de ejemplo de la metodología SDD sobre código ya existente.

## Problema
La plataforma necesita capturar la información de usuarios interesados y clientes (para geolocalización, campañas de correo y contacto), validando los datos requeridos y persistiendo la información de forma local.

## Solución propuesta

### Contrato
- **Método y ruta:** `POST /api/usuarios` (JSON).
- **Entrada:**
  - `nombre_completo` (str, requerido).
  - `celular` (str, opcional, ej: "+54...").
  - `email` (str, opcional).
  - `direccion_completa` (str, opcional).
  - `ciudad_prov_pais` (str, opcional).
  - `latitud` (float, opcional).
  - `longitud` (float, opcional).
- **Salida:**
  - `200` → `{"ok": true, "id_usuario": <int>}` (usuario registrado e insertado en la base de datos).
  - `422` → JSON de error de validación estándar de FastAPI (si falta el nombre u otros campos tienen tipos incorrectos).

## Criterios de aceptación
- [ ] Un usuario con campos válidos devuelve `200` con `ok=true` e `id_usuario` numérico.
- [ ] Si se omite `nombre_completo`, devuelve `422` (Unprocessable Entity).
- [ ] Los campos opcionales (`celular`, `email`, `direccion_completa`, `ciudad_prov_pais`, `latitud`, `longitud`) pueden ser omitidos o enviados como `null`.
- [ ] El registro se inserta correctamente en la tabla `usuarios_y_clientes` de la base de datos SQLite.
- [ ] `GET /health` devuelve `200` con `status="ok"`.

## Casos borde / errores
- `nombre_completo` vacío o nulo → `422`.
- Formato de coordenadas `latitud` / `longitud` inválido (no numérico) → `422`.

## Restricciones
- Almacenamiento en base de datos **SQLite** (`data/salud_natura.db`).
- Sin autenticación en esta fase.

