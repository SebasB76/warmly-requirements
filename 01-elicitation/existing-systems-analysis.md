# Análisis de los sistemas existentes de Warmi Energy

**Técnica:** análisis de documentos y sistemas.

| Sistema | Qué hace hoy | Datos que Warmly reutiliza | Requerimientos derivados |
|---|---|---|---|
| Base de datos central (Supabase / PostgreSQL) | Modela clientes, sitios, proyectos con su pipeline, planillas, dimensionamientos, propuestas versionadas, equipos e inspecciones. Autenticación con roles (técnico, ventas, gerencia, contabilidad, sistemas) y Row Level Security. | Clientes, sitios, proyectos, planillas, roles | FR-1.6, FR-4.1–4.3, NFR-11, NFR-15 |
| Dimensionador fotovoltaico | Calcula la planta (kWp, producción, cobertura) desde las planillas y el pliego tarifario; permite varios escenarios por proyecto. | Escenarios de dimensionamiento | FR-5.2, FR-5.3 |
| Sitio de propuestas | Genera la propuesta técnico-comercial a partir del dimensionamiento. | Versiones de propuesta | FR-5.4–5.6 |
| App de visitas técnicas | Checklist de inspección en campo con geolocalización, fotos, viabilidad y hallazgos. | Visitas y su resultado | FR-5.7, FR-7.6 |

## Hallazgos
- No existe un módulo comercial: leads, seguimiento y postventa no tienen soporte en ningún sistema.
- El pipeline de proyectos ya está definido en la base de datos (lead → dimensionamiento → visita → simulación → propuesta → aprobado → permisos → ejecución), con requisitos de transición configurables.
- Las visitas técnicas ya están resueltas por la app de visitas: Warmly no debe duplicarlas.
