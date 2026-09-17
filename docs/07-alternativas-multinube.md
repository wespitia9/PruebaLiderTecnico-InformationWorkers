# 7. Alternativas Multi-nube y Glosario de Servicios AWS

## Propósito de este documento

Desarrollé esta solución sobre AWS (Amazon Web Services) porque es la
nube con la que tengo más experiencia práctica de implementación.

IWCO maneja una estrategia real multi-nube: no se limita a un único
proveedor, sino que adapta la solución a la infraestructura que ya tiene
cada cliente. Históricamente tiene un arraigo fuerte en el ecosistema de
Microsoft, al punto de haber sido reconocida como Partner del año de
Microsoft, y divide su desarrollo entre tres proveedores según el rol que
cada uno cumple mejor:

- **Microsoft Azure** es su entorno más tradicional, por su
  especialización en analítica corporativa, Power BI, SharePoint y
  automatización de procesos.
- **AWS** se usa para complementar arquitecturas robustas, aportando
  soluciones flexibles sobre la nube líder del mercado global.
- **Google Cloud Platform (GCP)** se integra para consolidar una
  estrategia de tripleta de nubes, con alternativas avanzadas en Big
  Data e inteligencia artificial.

Este documento no rediseña la arquitectura completa en Azure o en Google
Cloud: muestro qué servicio equivalente usaría en cada nube y con qué
criterio elegiría una sobre otra, para que la decisión quede argumentada
según el contexto real de cada cliente, y no fijada por la nube con la
que construí este primer borrador.

## Glosario de servicios AWS utilizados

Definiciones simples, pensadas para que cualquier persona del equipo de
marketing u operaciones, sin conocimiento técnico, entienda para qué
sirve cada servicio mencionado en los Bloques 1 a 6.

### Ingesta

- **AWS AppFlow.** Conecta de forma automática con aplicaciones como el
  CRM o las herramientas de marketing para traer sus datos, sin que
  alguien tenga que copiarlos a mano.
- **AWS DMS (Data Migration Service).** Copia y mantiene actualizada la
  información de una base de datos, como la del sistema de ventas en
  tienda, hacia el nuevo sistema, casi al mismo tiempo en que ocurre.
- **Amazon Kinesis.** Recibe y organiza datos que llegan de forma
  continua y a gran velocidad, como los clics y compras que se hacen en
  la página web o app en el momento en que ocurren.

### Almacenamiento

- **Amazon S3.** Es el almacén central donde se guardan todos los datos
  de todas las fuentes, de forma segura y organizada.
- **AWS Lake Formation.** Controla quién puede ver qué parte de ese
  almacén, por ejemplo que alguien de marketing vea las campañas pero no
  el número de documento de un cliente puntual.
- **AWS Glue Data Catalog.** Es el índice que dice qué información hay
  guardada, dónde está y qué significa cada campo.

### Procesamiento y calidad

- **AWS Glue Jobs.** Es el motor que limpia, ordena y transforma los
  datos crudos para que sean útiles y confiables.
- **AWS Glue Data Quality.** Revisa automáticamente que los datos
  cumplan reglas básicas, por ejemplo que un correo tenga formato de
  correo, antes de darlos por buenos.
- **AWS Entity Resolution.** Identifica que "Juan Pérez" en la tienda
  física y "J. Pérez" en la app son la misma persona, y une su
  información bajo un solo identificador de cliente.
- **AWS Lambda.** Ejecuta tareas automáticas puntuales y pequeñas, como
  enviar un resultado ya calculado de vuelta al CRM.
- **Amazon SageMaker.** Es donde se construyen y entrenan los modelos que
  predicen cosas, como qué cliente podría dejar de comprar.

### Análisis y presentación

- **Amazon Redshift Serverless.** Es la base de datos analítica donde se
  consultan los reportes de negocio ya listos, ventas, campañas y
  clientes.
- **Amazon Athena.** Permite hacer consultas puntuales directamente
  sobre los datos guardados, sin tener que moverlos antes a otro lugar.

### Seguridad y gobernanza

- **AWS IAM (Identity and Access Management).** Decide quién puede
  entrar al sistema y qué puede hacer cada persona o servicio dentro de
  él.
- **AWS KMS (Key Management Service).** Cifra la información guardada,
  como poner bajo llave los datos para que nadie no autorizado los
  pueda leer.
- **Amazon VPC (Virtual Private Cloud).** Es la red privada donde viven
  todos estos servicios, aislada de internet público.
- **AWS PrivateLink.** Permite que los servicios se comuniquen entre sí
  de forma privada, sin exponer ese tráfico a internet.
- **AWS CloudTrail.** Guarda un registro de quién hizo qué y cuándo
  dentro del sistema, la base para cualquier auditoría.
- **AWS Audit Manager.** Organiza esos registros de forma ordenada para
  poder demostrarle a un regulador que se está cumpliendo la normativa.

### Observabilidad y orquestación

- **Amazon CloudWatch.** Vigila que todo esté funcionando bien y avisa
  cuando algo sale de lo normal.
- **Amazon SNS (Simple Notification Service).** Envía las alertas a
  quien deba enterarse, por correo o por mensaje.
- **Amazon EventBridge.** Conecta un evento que pasa en un sistema con
  la acción que debe dispararse en otro.
- **AWS Step Functions.** Coordina el orden en que deben ejecutarse
  todos los pasos del proceso, como una receta paso a paso.

## Tabla de equivalencias entre nubes

| Componente | AWS (elegido) | Azure | Google Cloud |
|---|---|---|---|
| Ingesta CRM/Marketing | AWS AppFlow | Azure Data Factory (conectores SaaS) | Google Cloud Data Fusion |
| Ingesta POS (CDC) | AWS DMS | Azure Database Migration Service | Datastream |
| Ingesta e-commerce (streaming) | Amazon Kinesis | Azure Event Hubs | Google Cloud Pub/Sub |
| Almacenamiento (data lake) | Amazon S3 + Lake Formation | Azure Data Lake Storage + Microsoft Purview | Google Cloud Storage + Dataplex |
| Procesamiento batch | AWS Glue Jobs | Azure Data Factory + Databricks | Dataflow / Dataproc |
| Procesamiento streaming | Kinesis Data Analytics (Apache Flink) | Azure Stream Analytics | Dataflow (Apache Beam) |
| Calidad de datos | AWS Glue Data Quality | Microsoft Purview Data Quality | Dataplex Data Quality |
| Resolución de identidad de cliente | AWS Entity Resolution | Sin equivalente administrado directo; se construye a medida (Databricks/ML) | Sin equivalente administrado directo; se construye a medida (Dataflow + Vertex AI) |
| Machine learning | Amazon SageMaker | Azure Machine Learning | Vertex AI |
| Data warehouse | Amazon Redshift Serverless | Azure Synapse Analytics | BigQuery |
| Consultas ad hoc | Amazon Athena | Azure Synapse Serverless SQL | BigQuery (mismo servicio) |
| Presentación | Power BI | Power BI (integración nativa) | Looker o Power BI vía conector |
| Identidad y accesos | AWS IAM + Lake Formation | Microsoft Entra ID + Purview | Google Cloud IAM + Dataplex |
| Cifrado | AWS KMS | Azure Key Vault | Cloud KMS |
| Red privada | Amazon VPC + AWS PrivateLink | Azure VNet + Private Link | Google Cloud VPC + Private Service Connect |
| Monitoreo (métricas y logs) | Amazon CloudWatch | Azure Monitor | Google Cloud Monitoring / Logging |
| Auditoría | AWS CloudTrail | Azure Monitor (Activity Log) | Cloud Audit Logs |
| Orquestación y alertas | Step Functions + EventBridge + SNS | Azure Data Factory triggers + Azure Monitor Alerts | Cloud Composer / Workflows + Cloud Monitoring |

## Cómo elegir entre las tres nubes

No se elige una nube por precio de lista, se elige por cómo encaja con el
contexto puntual del cliente. Tres criterios, en este orden de peso para
este caso:

1. **Encaje con lo que el cliente ya usa.** Si el cliente ya tiene
   Microsoft 365 o Azure AD (ahora Microsoft Entra ID) como directorio
   corporativo, Azure tiene una ventaja real: Power BI, la herramienta de
   consumo insignia de este proyecto, es nativa de Azure. Si el cliente
   usa Google Workspace o ya tiene equipos con fuerte cultura de SQL a
   gran escala, BigQuery de Google Cloud suele ser muy bien recibido por
   los propios analistas. Si no hay una relación fuerte previa con
   ningún proveedor, AWS es una opción sólida por la madurez y amplitud
   de su catálogo, pero no la única razonable.

2. **Madurez del servicio puntual para este caso.** El punto más
   diferenciador de este proyecto es la resolución de identidad del
   cliente entre POS, e-commerce, CRM y marketing. AWS Entity Resolution
   resuelve esto como servicio administrado; ni Azure ni Google Cloud
   tienen hoy un equivalente directo, habría que construirlo a medida.
   Este es un argumento técnico real a favor de AWS específicamente para
   este caso, independiente de que sea la nube en la que yo tengo más
   experiencia.

3. **Modelo de costo.** Las tres nubes ya ofrecen opciones serverless
   equivalentes (Redshift Serverless, Synapse Serverless, BigQuery on
   demand), así que el costo por sí solo rara vez inclina la decisión
   entre las tres. Lo que sí cambia el cálculo son los compromisos de
   gasto que el cliente ya tenga negociados con algún proveedor.

- **Punto a validar con el cliente:** si ya tiene un acuerdo empresarial
  vigente con Microsoft, Google o AWS que incluya compromisos de gasto o
  descuentos por volumen, porque eso puede pesar en la decisión final
  tanto o más que el análisis técnico de arriba.

## Conexión con la misión de IWCO

La estrategia real de tripleta de nubes de IWCO, con Azure como entorno
más tradicional, AWS para complementar arquitecturas robustas y Google
Cloud para Big Data e inteligencia artificial avanzada, existe
precisamente porque su rol no es vender una nube en particular, sino
simplificar el aprovechamiento del dato del cliente sin importar dónde
viva. Los principios de esta solución, el patrón ELT (Extracción, Carga y
Transformación), la arquitectura Medallion, la resolución de identidad y
la gobernanza por capas, son portables entre nubes; lo que cambia es el
servicio puntual que los implementa. Este documento existe para que esa
elección quede argumentada según el cliente real, no fijada por mi propia
experiencia al construir este primer borrador.
