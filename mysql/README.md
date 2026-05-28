# Catálogo de Rutinas MySQL Licenciadas — Factor BI

Este documento describe las **familias funcionales de Rutinas MySQL** desarrolladas por **PANEL CRUNCH DATA ANALYTICS, S.A. DE C.V.** ("Factor BI") que conforman su Plataforma, conforme se refieren en la Sección 1 del Anexo B del Contrato de Licencia de Entregables (DLA).

---

## ⚠️ Aviso sobre el carácter de este documento

Este documento es de **carácter descriptivo y referencial**. Su contenido refleja, en lenguaje natural, los criterios de identificación establecidos en la Sección 1 del Anexo B del DLA.

**En caso de cualquier discrepancia interpretativa entre este documento y el DLA, prevalecerá lo dispuesto en el DLA y sus Anexos firmados.**

La cobertura de la licencia se determina conforme a los criterios establecidos en el Anexo B; este documento es un instrumento de referencia auxiliar y no limitativo.

---

## Tipos de objetos cubiertos

Las Rutinas MySQL comprenden, para efectos del DLA, los objetos de base de datos MySQL de los siguientes tipos, desarrollados, desplegados o mantenidos por el Licenciante en el Servidor MySQL Designado:

- **PROCEDURE** (procedimiento almacenado)
- **FUNCTION** (función definida por el usuario)
- **VIEW** (vista)
- **EVENT** (evento programado)

---

## Criterios de identificación

Un objeto de base de datos MySQL presente en el Servidor MySQL Designado se considera **Rutina MySQL Licenciada** si cumple **al menos uno** de los siguientes criterios. Los criterios son **independientes y no acumulativos**: el cumplimiento de cualquiera de ellos es suficiente.

1. **Inclusión en este Catálogo Público** (criterio 1.A del Anexo B), por nombre exacto, en los archivos de inventario correspondientes a cada Sistema de Origen (`<sistema>-inventory.yaml`).

2. **Pertenencia a una familia funcional** (criterio 1.B del Anexo B), descrita en la siguiente sección de este documento.

3. **Marcadores embebidos** (criterio 1.C del Anexo B):
   - La cadena `Factor BI Licensed Component` en el atributo `COMMENT` del objeto (consultable vía `INFORMATION_SCHEMA.ROUTINES.ROUTINE_COMMENT` para `PROCEDURE` y `FUNCTION`, o vía `INFORMATION_SCHEMA.EVENTS.EVENT_COMMENT` para `EVENT`), o bien
   - Un comentario SQL inline dentro de la definición del objeto que incluya la leyenda:
     ```
     Factor BI Licensed Component | PANEL CRUNCH DATA ANALYTICS S.A. DE C.V. | DLA | https://github.com/factorbi/dla-catalog
     ```

4. **Reconocimiento como objeto preexistente** (criterio 1.D del Anexo B), mediante el inventario inicial capturado a la fecha de firma del Anexo A correspondiente.

---

## Familias funcionales

Las familias funcionales son **transversales a todos los Sistemas de Origen** soportados por la Plataforma. Cada objeto inventariado en los archivos `<sistema>-inventory.yaml` se clasifica en una de estas seis familias.

### FAM-01 — Utilitarios de Esquema

Procedimientos auxiliares para manipulación dinámica de la estructura del esquema de la base de datos, incluyendo:

- Creación, alteración y eliminación de tablas, columnas, índices y llaves primarias.
- Renombrado de tablas y columnas.
- Operaciones de adaptación multi-tenant.

Estos utilitarios son **transversales a cualquier Sistema de Origen** y no dependen de la lógica de negocio de ningún sistema en particular.

---

### FAM-02 — Dimensiones de Tiempo

Procedimientos y funciones de generación de calendarios y dimensiones de tiempo, así como cálculos de navegación temporal, incluyendo:

- Generación de tablas de calendario y dimensiones year-month.
- Cálculos de número de semana del año, día de la semana, primer y último día de la semana.
- Funciones de aging (antigüedad de saldos por fecha).
- Cálculos de fecha de servicio (service date) y year-to-date (YTD).
- Navegación temporal hacia adelante y hacia atrás (meses adelante, meses atrás).

Estos componentes son **transversales a cualquier Sistema de Origen**.

---

### FAM-03 — DWH (Data Warehouse)

Procedimientos, vistas, funciones y eventos asociados a la ingestión, transformación, carga, post-procesamiento, consolidación multi-empresa, tratamiento fiscal y cálculo de indicadores de negocio dentro del Almacén de Datos construido en MySQL, alimentado desde los Sistemas de Origen soportados.

Esta familia es **específica de cada Sistema de Origen**: los procedimientos y vistas de DWH para Microsip son distintos de los de Soft Restaurant, Aspel SAE, etc. La lista exacta de objetos DWH por sistema se encuentra en el archivo `<sistema>-inventory.yaml` correspondiente.

Los Sistemas de Origen actualmente soportados incluyen, de manera enunciativa y no limitativa: **Microsip, Soft Restaurant, Intelisis, Aspel SAE y POSitouch**.

---

### FAM-04 — Funciones Auxiliares

Funciones de utilidad de propósito general, aplicables a cualquier Sistema de Origen, incluyendo:

- Manipulación de cadenas (limpieza de acentos, eliminación de caracteres especiales, extracción de subcadenas).
- Manipulación de números (extracción de números desde cadenas).
- Extracción de campos JSON.
- Cálculos de tipo de cambio (por ejemplo, conversión a USD).

Estos componentes son **transversales a cualquier Sistema de Origen**.

---

### FAM-05 — Instalación y Eventos Programados

Procedimientos y eventos asociados a la instalación inicial del esquema y a tareas de mantenimiento programado en el Servidor MySQL Designado.

Incluye eventos MySQL nativos (`CREATE EVENT`) que ejecutan tareas periódicas, así como procedimientos de configuración inicial que se ejecutan una sola vez al desplegar la Plataforma.

---

### FAM-06 — Otros Utilitarios

Procedimientos de propósito general utilizados internamente por las demás familias, tales como:

- Control de flujo de ejecución (loops, esperas controladas).
- Depuración y registro de actividad.
- Utilidades de soporte que no encajan en ninguna otra familia.

---

## Verificación de marcadores embebidos

Sobre el Servidor MySQL Designado, las siguientes consultas SQL permiten verificar la presencia de marcadores embebidos:

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

Para inspeccionar el comentario SQL inline en el cuerpo de un objeto, puede emplearse:

```sql
SHOW CREATE PROCEDURE <schema>.<nombre>;
SHOW CREATE FUNCTION  <schema>.<nombre>;
SHOW CREATE EVENT     <schema>.<nombre>;
SHOW CREATE VIEW      <schema>.<nombre>;
```

**Nota sobre VIEWs.** MySQL no soporta el atributo `COMMENT` para objetos de tipo `VIEW`, ni preserva los comentarios SQL inline contenidos en el cuerpo de un `CREATE VIEW` una vez ejecutado en el servidor. Por esta razón, los marcadores embebidos en VIEWs únicamente subsisten en el código fuente del Licenciante (versionado en el presente repositorio), y no en el servidor desplegado. La identificación de VIEWs Licenciadas se apoya prioritariamente en los criterios 1.A (inclusión en este Catálogo por nombre exacto) y 1.B (pertenencia a una familia funcional), conforme al Anexo B del DLA.

La **ausencia o remoción del marcador no excluye** el carácter de Rutina MySQL Licenciada de un objeto, si éste se identifica conforme a los demás criterios (1.A, 1.B o 1.D).

---

## Inventarios por Sistema de Origen

Los nombres exactos de los objetos `PROCEDURE`, `FUNCTION`, `VIEW` y `EVENT` que conforman la Plataforma se enumeran en los siguientes archivos de inventario, uno por cada Sistema de Origen soportado:

- **Microsip** → `microsip-inventory.yaml`
- **Soft Restaurant** → *(pendiente de publicación)*
- **Intelisis** → *(pendiente de publicación)*
- **Aspel SAE** → *(pendiente de publicación)*
- **POSitouch** → *(pendiente de publicación)*

Cada archivo de inventario contiene la lista completa de objetos del Sistema de Origen correspondiente, con su tipo, nombre, archivo fuente, carpeta y familia funcional asignada.

### Archivos auxiliares de trazabilidad

Junto a cada archivo `<sistema>-inventory.yaml` puede existir un archivo `<sistema>-inventory-source.csv` con el mismo contenido en formato tabular plano. Estos archivos CSV son **snapshots informativos** derivados de la inspección del repositorio de desarrollo del Licenciante, conservados con fines de trazabilidad y para facilitar la consulta tabular del inventario (por ejemplo, en hojas de cálculo).

Los archivos CSV **no son canónicos**: su existencia y contenido son meramente auxiliares, y pueden estar ausentes para algunos Sistemas de Origen sin que ello afecte la validez del inventario correspondiente.

### Jerarquía documental

En caso de cualquier discrepancia interpretativa, prevalecerán los documentos en el siguiente orden de mayor a menor jerarquía:

1. **El DLA y sus Anexos firmados** — Documentos contractuales; prevalecen sobre cualquier otro contenido de este repositorio.
2. **Este `README.md`** — Documento descriptivo de referencia.
3. **`<sistema>-inventory.yaml`** — Documento canónico del inventario estructurado por Sistema de Origen.
4. **`<sistema>-inventory-source.csv`** — Snapshot informativo auxiliar, no canónico.

---

## Contacto

Para consultas o aclaraciones relacionadas con este Catálogo, dirigirse a `legal@factorbi.com`.

---

*Última actualización de este documento: ver historial de commits del repositorio.*
