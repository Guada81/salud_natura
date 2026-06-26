# TODO — Gestión de Tareas y Specs

Carpeta de seguimiento del proyecto **Salud Natura** (`saludnatura.graduadosfiuba.org`). Adaptado del sistema de trabajo de `cargas.graduadosfiuba`.

## 📁 Estructura

```
TODO/
├── README.md          # Este archivo
├── NEXT_STEPS.md      # ⭐ Roadmap y tareas pendientes (Source of Truth)
└── specs/             # Especificaciones Spec-Driven Development (SDD)
    ├── _PLANTILLA/    # Plantilla del trío spec.md + plan.md + tasks.md
    └── <feature>/     # Una carpeta por feature
        ├── spec.md    # QUÉ y POR QUÉ (contrato, criterios de aceptación)
        ├── plan.md    # CÓMO (archivos a tocar, dependencias)
        └── tasks.md   # Checklist accionable (incluye crear tests)
```

## 🧪 Metodología SDD

Antes de implementar una feature o cambio no trivial:

1. Copiar `specs/_PLANTILLA/` a `specs/<nombre-feature>/`.
2. Completar **`spec.md`** (objetivo, contrato, criterios de aceptación, casos borde).
3. Completar **`plan.md`** (archivos a crear/modificar, dependencias, consideraciones).
4. Completar **`tasks.md`** (checklist; el paso final SIEMPRE es crear tests y verificar que pasan).
5. Trabajar en una rama `feature/<nombre>` y abrir PR a `main` (ver `CONTRIBUTING.md`).

> El detalle del flujo está en `.agents/agent.md` (Secciones 9 y 10) y en `CONTRIBUTING.md`.
