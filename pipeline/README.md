# pipeline/

Referencia de organización de los pipelines de datos, alineada a la
metodología Exploración → Extracción → Refinamiento → Consumo de IWCO y a
la arquitectura Medallion definida en
[`docs/01-arquitectura-datos-aws.md`](../docs/01-arquitectura-datos-aws.md).

- `ingestion/`: extracción desde POS, e-commerce, CRM y marketing hacia la
  capa Raw. AWS DMS (Data Migration Service) para POS vía CDC (Change
  Data Capture), Amazon Kinesis para los eventos de e-commerce, y AWS
  AppFlow para CRM y marketing.
- `processing/`: transformación Raw → Curated → Refined con AWS Glue Jobs
  (PySpark), Kinesis Data Analytics para Apache Flink para el
  enriquecimiento casi en tiempo real de e-commerce, AWS Entity
  Resolution para construir el `loyalty_id` y Amazon SageMaker para los
  modelos predictivos del roadmap.
- `quality/`: reglas y puertas de calidad por fuente y por capa con AWS
  Glue Data Quality (DQDL, Data Quality Definition Language), detalladas
  en
  [`docs/02-calidad-consistencia-datos.md`](../docs/02-calidad-consistencia-datos.md).
- `orchestration/`: coordinación y manejo de fallos y de cumplimiento de
  SLA (Service Level Agreement) del flujo completo con AWS Step
  Functions, Amazon EventBridge y Amazon SNS (Simple Notification
  Service).

No contiene código funcional. Son placeholders de organización para
cuando el cliente apruebe pasar de la propuesta a la construcción.
