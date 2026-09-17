# data/

Placeholders de las tres capas de la arquitectura Medallion definida en
[`docs/01-arquitectura-datos-aws.md`](../docs/01-arquitectura-datos-aws.md):

- `raw/` (Bronze): extracto tal cual llega de cada fuente, inmutable,
  particionado por fecha de ingesta.
- `curated/` (Silver): datos deduplicados y estandarizados, con
  `loyalty_id` como llave común entre fuentes, manejo de dimensiones de
  cambio lento (SCD, Slowly Changing Dimension) y enmascaramiento de PII
  (información de identificación personal) ya aplicados.
- `refined/` (Gold): tablas de negocio modeladas, listas para consumo en
  Power BI o mediante el acceso conversacional (MCP con Claude) definido
  en el Bloque 1.

No contiene datos reales. Son placeholders de estructura.
