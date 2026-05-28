# Catálogo Público del Contrato de Licencia de Entregables (DLA) — Factor BI

Este repositorio constituye el **Catálogo Público** referido en la Cláusula 1.11 del Contrato de Licencia de Entregables (DLA) celebrado entre **PANEL CRUNCH DATA ANALYTICS, S.A. DE C.V.** y sus clientes o representantes, bajo la marca comercial **Factor BI**.

Su propósito es describir, de forma pública y actualizable, los componentes que conforman la plataforma del Licenciante, a efecto de permitir su identificación inequívoca en los servidores y cuentas de los clientes.

---

## ⚠️ Aviso importante: este repositorio NO es software de código abierto

Este repositorio **no distribuye software bajo ninguna licencia de código abierto** (MIT, Apache, GPL, MPL, BSD ni equivalente). El contenido aquí publicado es un **instrumento legal de identificación**, no código fuente entregado para uso libre.

- **No se otorga licencia alguna** sobre los componentes descritos por el solo hecho de su publicación en este repositorio.
- **No se autoriza** el uso, reproducción, distribución, modificación ni implementación de los componentes aquí descritos sin un Contrato de Licencia de Entregables (DLA) vigente con PANEL CRUNCH DATA ANALYTICS, S.A. DE C.V.
- La presencia de archivos en formato Markdown, YAML o cualquier otro **no implica** que se trate de un proyecto de software libre.

La descripción categórica de los componentes aquí publicada tiene como única finalidad servir de referencia para la identificación de Entregables Licenciados conforme al DLA correspondiente.

---

## ¿A quién se dirige este repositorio?

Este Catálogo está dirigido principalmente a:

- **Clientes de Factor BI** que han suscrito un DLA y desean verificar el alcance de los Entregables Licenciados desplegados en su Cuenta AWS Designada y Servidor MySQL Designado.
- **Representantes de Factor BI** que han suscrito su propio DLA con Factor BI y operan despliegues en Cuentas AWS Designadas y Servidores MySQL Designados propios o de sus clientes finales. Las Partes reconocen que, bajo este modelo, tanto el Representante como cada cliente final firman, cada uno por separado, su propio DLA directamente con Factor BI.
- **Terceros Autorizados** (consultores, desarrolladores independientes, contratistas, integradores, partners) a quienes el Cliente haya otorgado acceso a los Entregables Licenciados conforme a la Cláusula Quinta del DLA.
- **Auditores y peritos técnicos** que requieran verificar la titularidad de componentes en disputa o auditar el cumplimiento del DLA.
- **Asesores legales** que requieran interpretar el alcance de los Entregables Licenciados.

El Catálogo no está dirigido al público general y su consulta no genera derechos sobre los componentes descritos.

---

## Titularidad y mantenimiento

Este repositorio es propiedad y es mantenido exclusivamente por:

**PANEL CRUNCH DATA ANALYTICS, S.A. DE C.V.**
RFC: PCD190724QD9
Marca comercial: Factor BI

Únicamente los commits firmados o aprobados por personal autorizado de PANEL CRUNCH DATA ANALYTICS, S.A. DE C.V. se consideran modificaciones oficiales al Catálogo Público.

---

## Vigencia del Catálogo y trazabilidad histórica

Las Partes del DLA reconocen que:

- Este Catálogo Público **inicia su vigencia el 19 de mayo de 2026**.
- **No existen versiones del Catálogo anteriores a dicha fecha.**
- La trazabilidad histórica completa de las versiones del Catálogo se conserva mediante el **registro de cambios (commit history)** de este repositorio Git.

El contenido del Catálogo puede ser actualizado por el Licenciante de tiempo en tiempo, **sin requerir aviso previo ni modificación al DLA**, conforme a lo previsto en la Cláusula 1.11 del propio Contrato. La cobertura de la licencia se determina conforme a los criterios establecidos en el Anexo B del DLA; este Catálogo Público es un instrumento de referencia auxiliar y no limitativo.

---

## Relación con el DLA

Este Catálogo es referido expresamente por el Contrato de Licencia de Entregables en las siguientes disposiciones:

- **Cláusula 1.11** — Define el Catálogo Público como instrumento descriptivo y referencial, y establece su vigencia, mecanismo de actualización y trazabilidad histórica.
- **Anexo B, Sección 1.A** — Establece que la inclusión en este Catálogo es uno de los criterios de identificación de las **Rutinas MySQL Licenciadas**.
- **Anexo B, Sección 1.B** — Refiere a este Catálogo para la lista de Sistemas de Origen soportados y la descripción de las familias funcionales de las Rutinas MySQL.
- **Anexo B, Sección 2.A** — Establece que la inclusión en este Catálogo es uno de los criterios de identificación de los **Activos QuickSight Licenciados**.
- **Anexo B, Sección 2.B** — Refiere a este Catálogo para el detalle de layouts, composición visual y arquitectura de navegación de cada producto QuickSight.

El presente Catálogo no sustituye al DLA ni a sus Anexos. En caso de cualquier discrepancia interpretativa entre este Catálogo y el DLA, prevalecerá lo dispuesto en el DLA y sus Anexos firmados.

---

## Estructura del repositorio

```
dla-catalog/
├── README.md                  Este documento. Portada del Catálogo.
├── mysql/                     Catálogo de Rutinas MySQL Licenciadas.
│   ├── README.md              Descripción narrativa de las familias funcionales.
│   ├── inventory.yaml         Inventario estructurado para verificación técnica.
│   └── families.yaml          Definición formal de las familias funcionales.
└── quicksight/                Catálogo de Activos QuickSight Licenciados.
    ├── README.md              Descripción narrativa de los productos.
    ├── inventory.yaml         Inventario estructurado para verificación técnica.
    └── families.yaml          Definición formal de las familias funcionales.
```

Cada subcarpeta dispone de su propio `README.md` que describe las familias de componentes en lenguaje natural, y de uno o más archivos en formato `YAML` que contienen la información estructurada para consulta automatizada.

---

## Cómo verificar la presencia de marcadores en un despliegue

A continuación se resumen los comandos que un cliente o auditor puede emplear para verificar la presencia de los marcadores embebidos en su entorno. El detalle completo y los criterios alternativos de identificación se describen en el Anexo B del DLA.

### Para Rutinas MySQL

Sobre el Servidor MySQL Designado:

```sql
-- Marcadores en PROCEDURE y FUNCTION
SELECT ROUTINE_SCHEMA, ROUTINE_NAME, ROUTINE_TYPE, ROUTINE_COMMENT
FROM INFORMATION_SCHEMA.ROUTINES
WHERE ROUTINE_COMMENT LIKE '%Factor BI Licensed Component%';

-- Marcadores en EVENT
SELECT EVENT_SCHEMA, EVENT_NAME, EVENT_COMMENT
FROM INFORMATION_SCHEMA.EVENTS
WHERE EVENT_COMMENT LIKE '%Factor BI Licensed Component%';
```

### Para Activos QuickSight

Sobre la Cuenta AWS Designada, usando AWS CLI con permisos de lectura sobre QuickSight:

```bash
# Inventario general
aws quicksight list-data-sets   --aws-account-id <ACCOUNT_ID>
aws quicksight list-analyses    --aws-account-id <ACCOUNT_ID>
aws quicksight list-dashboards  --aws-account-id <ACCOUNT_ID>

# Verificación del marcador embebido en una definición
aws quicksight describe-analysis-definition  --aws-account-id <ACCOUNT_ID> --analysis-id  <ID>
aws quicksight describe-dashboard-definition --aws-account-id <ACCOUNT_ID> --dashboard-id <ID>
aws quicksight describe-data-set             --aws-account-id <ACCOUNT_ID> --data-set-id  <ID>
```

El marcador embebido se identifica por la presencia de un parámetro nombrado `FactorBI` cuyo valor estático por defecto contiene la leyenda:

```
Factor BI Licensed Component | PANEL CRUNCH DATA ANALYTICS S.A. DE C.V. | DLA | https://github.com/factorbi/dla-catalog
```

La **ausencia** del marcador en un componente **no excluye** su carácter de Entregable Licenciado, conforme se establece en el Anexo B del DLA: existen criterios adicionales de identificación basados en pertenencia a familia funcional e inclusión en el presente Catálogo.

---

## Contacto

Para cualquier consulta, notificación, reporte de uso no autorizado, o solicitud de aclaración relacionada con el presente Catálogo o con el DLA, dirigirse a:

**Correo electrónico:** legal@factorbi.com

**Atención:** Representante Legal
PANEL CRUNCH DATA ANALYTICS, S.A. DE C.V.

---

*Última actualización de este documento: ver historial de commits del repositorio.*
