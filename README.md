# EquipCheck Pro

Aplicación web para la gestión integral del ciclo de vida de equipos en operaciones industriales. Desarrollada en React + TypeScript con backend en Supabase (PostgreSQL), orientada a entornos Oil & Gas donde la trazabilidad documental y la inspección sistemática son requisitos críticos.

> **v1.0 — Producción**  
> Desplegado y en uso activo en Petroleum Blending International SAS ESP (PBI), Bogotá, Colombia.

---

## Funcionalidades

| Módulo | Descripción |
|---|---|
| **Gestión de equipos (master)** | Registro centralizado de equipos con ficha técnica completa, categorización y estado operativo |
| **Hoja de vida del equipo** | Trazabilidad completa del historial de cada equipo: inspecciones, mantenimientos y novedades |
| **Inspecciones con firma digital** | Formularios de inspección configurables con captura de firma digital del responsable |
| **Historial de inspecciones** | Consulta y filtrado de inspecciones por equipo, fecha, responsable y resultado |
| **Generación de reportes PDF** | Reportes de inspección en PDF con logo corporativo, datos del equipo y firma del inspector |
| **Autenticación por roles** | Control de acceso basado en roles (administrador, inspector, consulta) mediante Supabase Auth |
| **Inventario** | Vista consolidada del parque de equipos con estados, ubicaciones y próximas inspecciones |

---

## Stack

- **Frontend:** React 18 + TypeScript + Vite
- **Backend:** Supabase (PostgreSQL + Auth + Storage)
- **Estilos:** Tailwind CSS
- **Generación PDF:** jsPDF
- **Despliegue:** Vercel / Netlify

---

## Arquitectura de base de datos

```
master_equipo          → Registro maestro de equipos
historial_hseq         → Inspecciones y eventos por equipo
profiles               → Usuarios y roles del sistema
```

Base de datos migrada de SQLite a PostgreSQL (Supabase) en producción, resolviendo limitaciones de concurrencia y escalabilidad del sistema original.

---

## Decisiones técnicas destacadas

- **Migración SQLite → Supabase:** Migración completa en producción sin pérdida de datos, incluyendo resolución de incompatibilidades de tipos de fecha entre SQLite y PostgreSQL
- **Autenticación:** Race condition en el flujo de auth resuelta mediante guards de sesión asincrónicos
- **PDF con logo corporativo:** Carga de imagen vía proxy para resolver restricciones CORS en entorno de producción
- **API key management:** Eliminación de claves hardcodeadas y migración a variables de entorno

---

## Contexto normativo

Desarrollado para dar cumplimiento a los requisitos de inspección y mantenimiento de equipos establecidos en:

- **Decreto 1072 de 2015** — Estándares mínimos del SG-SST
- **ISO 45001:2018** — Gestión de activos y controles operacionales
- **NORSOK SWA-006** — Estándares de seguridad en operaciones Oil & Gas

---

## Problema que resuelve

La inspección de equipos en operaciones industriales suele gestionarse con listas de chequeo en papel o Excel, sin trazabilidad, sin firma del responsable y sin historial consolidado por equipo. EquipCheck Pro digitaliza y centraliza ese proceso, garantizando evidencia auditada de cada inspección y visibilidad en tiempo real del estado del parque de equipos.

---

## Autor

**Holman Moreno** — HSEQ Coordinator · Petroleum Engineer  
📧 hmoreno@pbi.com.co  
🔗 [github.com/induccionhse](https://github.com/induccionhse)
