# Configuración de Protección de Ramas

**Para:** Administrador del repositorio `centrograduadosFIUBA/saludnatura.graduadosfiuba.org`

## 🎯 Objetivo
Garantizar que todo el código pase por Pull Request + CI antes de llegar a `main`.

## 📋 Instrucciones

1. Ir a: `https://github.com/centrograduadosFIUBA/saludnatura.graduadosfiuba.org/settings/branches`
2. Click en **"Add branch protection rule"**.

### Proteger `main`
**Branch name pattern:** `main`

- ✅ **Require a pull request before merging**
  - ✅ Require approvals: **1**
  - ✅ Dismiss stale pull request approvals when new commits are pushed
- ✅ **Require status checks to pass before merging**
  - ✅ Require branches to be up to date before merging
  - Status checks requeridos (aparecen tras la primera corrida del CI):
    - `🔍 Linting (Ruff)`
    - `📦 Verificar Dependencias`
    - `🐳 Verificar Docker Build`
    - `🧪 Tests (Pytest)`
- ✅ Require conversation resolution before merging
- ✅ Do not allow bypassing the above settings

## ✅ Verificación
```bash
git checkout main
git commit --allow-empty -m "test: verificar proteccion"
git push origin main
```
Resultado esperado:
```
remote: error: GH006: Protected branch update failed
```
Si ves ese error, la protección funciona.

---
*Adaptado del flujo de cargas.graduadosfiuba para saludnatura.graduadosfiuba.org.*
