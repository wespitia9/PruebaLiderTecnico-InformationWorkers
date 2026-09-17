# governance/

Referencia de gobernanza de datos, desarrollada en detalle en
[`docs/04-seguridad-gobernanza.md`](../docs/04-seguridad-gobernanza.md):

- `data_catalog/`: catálogo de datos y metadatos con AWS Glue Data
  Catalog y AWS Lake Formation, con dueños de datos por dominio y
  clasificación de sensibilidad por campo (público, interno, confidencial
  o PII).
- `security_policies/`: políticas de acceso de mínimo privilegio y de
  enmascaramiento de PII (información de identificación personal) con
  AWS IAM (Identity and Access Management), AWS Lake Formation y AWS KMS
  (Key Management Service).
- `cost_management/`: gestión de costos con cost allocation tags y AWS
  Budgets, alineada al pilar de optimización de costos del AWS
  Well-Architected Framework.

No contiene configuración funcional. Son placeholders de organización.
