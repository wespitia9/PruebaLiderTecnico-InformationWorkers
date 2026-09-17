# infra/

Referencia de infraestructura como código para los servicios de la
arquitectura definida en
[`docs/01-arquitectura-datos-aws.md`](../docs/01-arquitectura-datos-aws.md):
Amazon S3 (Raw, Curated, Refined), AWS Lake Formation, AWS Glue Data
Catalog, Amazon Kinesis, AWS Glue Jobs y Amazon Redshift Serverless.

No contiene plantillas ejecutables ni código funcional. Es un placeholder
que representa cómo organizaría el IaC (Infrastructure as Code, Terraform
o AWS CDK, Cloud Development Kit, a definir con el cliente) una vez
cerrada la revisión de arquitectura: un módulo por servicio, con los
permisos de mínimo privilegio de AWS IAM (Identity and Access Management)
y las llaves de AWS KMS (Key Management Service) que detallo en
[`docs/04-seguridad-gobernanza.md`](../docs/04-seguridad-gobernanza.md).
