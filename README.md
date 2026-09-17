# Prueba Líder Técnico: Information Workers (IWCO)

Solución propuesta para el caso de negocio de una cadena minorista con datos
fragmentados en POS, e-commerce, CRM y marketing, sin vista unificada del
cliente a través de sus programas de lealtad online y offline.

## Contenido del repositorio

- [`00-contexto-caso.md`](00-contexto-caso.md): situación problemática y las
  12 preguntas del examen, transcritas del PDF original.
- [`docs/`](docs/): un documento por bloque de la prueba (arquitectura de
  datos, calidad y consistencia, generación de insights, seguridad y
  gobernanza, capacitación y desarrollo, tendencias y futuro), la
  comparación multi-nube con su glosario de servicios AWS, y los
  diagramas de soporte de cada bloque.
- [`infra/`](infra/): referencia de infraestructura como código (Terraform
  o AWS CDK) para los servicios de almacenamiento, catálogo, streaming y
  análisis de la arquitectura propuesta.
- [`pipeline/`](pipeline/): referencia de los pipelines de ingesta,
  procesamiento, calidad y orquestación, organizados por capa de la
  arquitectura Medallion.
- [`src/`](src/): referencia de modelado de datos de negocio, agentes del
  roadmap y utilidades compartidas del pipeline.
- [`data/`](data/): placeholders de las tres capas de datos (raw, curated,
  refined) de la arquitectura Medallion.
- [`observability/`](observability/): referencia de dashboards de
  monitoreo y alertas de fallo o de incumplimiento de SLA.
- [`governance/`](governance/): referencia de catálogo de datos, políticas
  de seguridad y gestión de costos.

Este repositorio no contiene código funcional: representa la organización y
las buenas prácticas de un arquitecto de datos senior para este caso.

## Fuente de verdad de la prueba

El documento original de la prueba está en
[`docs/Prueba_de_seleccion_Lider_tecnico_Information_Wokers.pdf`](docs/Prueba_de_seleccion_Lider_tecnico_Information_Wokers.pdf).
