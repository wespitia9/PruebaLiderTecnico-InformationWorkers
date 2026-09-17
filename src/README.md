# src/

Referencia de organización del código de la solución.

- `models/`: modelado de las tablas de negocio (`customer_360`,
  `campaign_performance`, `loyalty_attribution`) sobre la capa Refined,
  detallado en
  [`docs/01-arquitectura-datos-aws.md`](../docs/01-arquitectura-datos-aws.md).
- `agents/`: soluciones agénticas del roadmap descrito en
  [`docs/06-tendencias-futuro.md`](../docs/06-tendencias-futuro.md), como
  el acceso conversacional vía MCP (Model Context Protocol) con Claude, un
  agente de calidad de datos y un agente de recomendación de campañas,
  todos con aprobación humana obligatoria antes de ejecutar cualquier
  acción.
- `utils/`: utilidades compartidas del pipeline, como el mapeo del
  `loyalty_id` y validaciones comunes entre jobs.

No contiene código funcional. Son placeholders de organización.
