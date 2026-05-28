# Catálogo de Activos QuickSight Licenciados — Factor BI

Este documento describe las **familias funcionales de Activos QuickSight** desarrolladas por **PANEL CRUNCH DATA ANALYTICS, S.A. DE C.V.** ("Factor BI") que conforman su Plataforma, conforme se refieren en la Sección 2 del Anexo B del Contrato de Licencia de Entregables (DLA).

---

## ⚠️ Aviso sobre el carácter de este documento

Este documento es de **carácter descriptivo y referencial**. Su contenido refleja, en lenguaje natural, los criterios de identificación establecidos en la Sección 2 del Anexo B del DLA.

**En caso de cualquier discrepancia interpretativa entre este documento y el DLA, prevalecerá lo dispuesto en el DLA y sus Anexos firmados.**

La cobertura de la licencia se determina conforme a los criterios establecidos en el Anexo B; este documento es un instrumento de referencia auxiliar y no limitativo.

---

## Tipos de recursos cubiertos

Los Activos QuickSight comprenden, para efectos del DLA, los recursos de Amazon QuickSight de los siguientes tipos, desarrollados, desplegados o mantenidos por el Licenciante en la Cuenta AWS Designada:

- **Dataset** (Conjunto de Datos)
- **Analysis** (Análisis)
- **Dashboard** (Tablero)

Los recursos de tipo **Data Source** (Origen de Datos) **no se consideran Activos QuickSight Licenciados** y quedan fuera del alcance del DLA, por constituir meras conexiones de infraestructura.

---

## Criterios de identificación

Un recurso de Amazon QuickSight presente en la Cuenta AWS Designada se considera **Activo QuickSight Licenciado** si cumple **al menos uno** de los siguientes criterios. Los criterios son **independientes y no acumulativos**: el cumplimiento de cualquiera de ellos es suficiente.

1. **Inclusión en este Catálogo Público** (criterio 2.A del Anexo B), por correspondencia funcional y de diseño con los productos aquí descritos. Los recursos de QuickSight no se identifican por su nombre ni por su identificador, por ser éstos editables o variables entre cuentas e instancias.

2. **Pertenencia a una familia funcional** (criterio 2.B del Anexo B), descrita en la siguiente sección de este documento.

3. **Marcadores embebidos** (criterio 2.C del Anexo B): presencia de un parámetro nombrado `FactorBI` en la definición del recurso, cuyo valor estático por defecto contiene la leyenda:

   ```
   Factor BI Licensed Component | PANEL CRUNCH DATA ANALYTICS S.A. DE C.V. | DLA | https://github.com/factorbi/dla-catalog
   ```

4. **Reconocimiento como activo preexistente** (criterio 2.D del Anexo B), mediante el inventario inicial capturado a la fecha de firma del Anexo A correspondiente.

---

## Familias funcionales

### 1. Ventas

Tablero de análisis del ciclo de venta de mayoreo (cotizaciones, pedidos, remisiones, facturas y devoluciones).

**Dimensiones de análisis:** vendedor, grupos, líneas, artículos, clientes, tipos de clientes, zonas de clientes, almacenes, sucursales, condiciones de pago.

**Métricas de análisis:** importes de venta, devoluciones, descuentos, utilidad, % margen, ticket promedio y costos.

**Análisis de tiempo:** por fecha, día de la semana (lunes a domingo), número de la semana del año (1 a 52), mes y año.

**Pestañas estándar (una o más):**

- Ventas
- Ventas por Vendedor
- Acumulado del Año
- Devoluciones de Venta
- Pedidos Pendientes
- Cotizaciones Pendientes
- Remisiones Pendientes
- Comparativo Varios Años

---

### 2. Punto de Venta

Tablero de análisis de venta de punto de venta (tickets de mostrador, devoluciones de mostrador, facturación global y sus devoluciones).

**Dimensiones de análisis:** sucursal, caja, cajero, vendedor, cliente, almacenes, grupos, líneas, artículos.

**Métricas de análisis:** importes de tickets de venta, devolución, descuentos, utilidad, % margen, ticket promedio y costos.

**Análisis de tiempo:** por fecha, día de la semana (lunes a domingo), número de la semana del año (1 a 52), mes y año.

**Pestañas estándar (una o más):**

- Notas y Devoluciones
- Acumulado del Año
- Sucursales
- Cajas
- Cajeros
- Vendedores
- Facturas y Notas de Crédito
- Devoluciones de Venta

---

### 3. Consolidado Punto de Venta y Ventas

Tablero de análisis que consolida los módulos de Ventas y Punto de Venta en una vista integrada con comparativos, incluyendo las mismas dimensiones y métricas de los dos dashboards que consolida.

**Pestañas estándar (una o más):**

- Ventas
- Acumulado del Año
- Devoluciones de Venta
- Comparativo Varios Años

---

### 4. Inventarios y Compras

Tablero de análisis de existencias globales y por almacén, días de inventario (days at hand), inventario por proveedores, antigüedad de inventario, órdenes de compra, históricos de compra y estadísticas mensuales de: venta, devoluciones, compras, devoluciones de compra, costo promedio, último costo, valuación a costo promedio y último costo, inventario inicial y final, máximo, mínimo y punto de reorden.

**Pestañas estándar (una o más):**

- Inventario Global
- Inventario por Almacenes
- Días de Inventario
- Días de Inventario por Almacén
- Inventario por Proveedores
- Antigüedad del Inventario
- Antigüedad por Almacén
- Gráficas Estadísticas
- Órdenes de Compra
- Histórico de Compras
- Ventas y Compras por Semana

---

### 5. Estados Financieros

Tablero de análisis de estados de resultados y balance general en estilo de vista mes a mes (mensual), así como análisis gráficos de los rubros financieros relevantes para el negocio, vistas 80-20 (pareto).

**Dimensiones de análisis:** cuenta, centro de costo (departamento), póliza, folio, descripción.

**Pestañas estándar (una o más):**

- Estados de Resultados (gráficos)
- Estados de Resultados (analítico)
- Estado de Resultados (tablas)
- Balance General
- Clientes y Proveedores
- Auxiliar

---

### 6. Flujo de Efectivo

Tablero de análisis de cuentas por cobrar, cuentas por pagar, antigüedad de saldos (aging), cobranza, pagos, anticipos, y vista resumen de flujo de efectivo con sus respectivos detalles.

**Dimensiones de análisis:** cliente, concepto, tipo cliente, vendedor, almacén, plazo de antigüedad, moneda, condición de pago, proveedor, folio.

**Pestañas estándar (una o más):**

- Flujo de Efectivo
- Cuentas por Cobrar
- Cuentas por Pagar
- Cobranza
- Pagos
- Tendencia de Cartera

---

### 7. Restaurantes

Tablero de análisis para cadenas de restaurantes, con los tickets de venta, devoluciones, movimientos de caja, compras y gastos.

**Dimensiones de análisis:** tienda (establecimiento/sucursal), turno, área, mesero, categoría, platillo, tipo de descuento, caja, forma de pago.

**Métricas de análisis:** importes de venta, devoluciones, descuentos, costos, utilidad, % margen, ticket promedio, % mix alcohol (o café o un grupo de alimento importante), # invitados (comensales), # cheques (tickets).

**Pestañas estándar (una o más):**

- Venta Diaria
- Resumen por Semana
- Resumen Anual
- Comparativo de Tiendas
- Cajas
- Utilidad: Ventas, Compras, Gastos
- Desglose Venta Diaria
- Actualización de Tiendas

---

## Características de diseño distintivas

Los Activos QuickSight desarrollados por Factor BI presentan, según la naturaleza de cada tablero y de manera **enunciativa y no concurrente**, una o varias de las siguientes características de diseño que, en su selección, disposición y combinación, constituyen expresión original del Licenciante:

1. **Mecánica de doble rango de fechas:** uso de cuatro fechas (inicio y fin de un periodo actual, e inicio y fin de un periodo anterior) que permite establecer comparativos en línea con porcentajes de variación entre periodos.

2. **Flujo de análisis de lo general a lo particular:** organización que parte de indicadores clave (KPIs), continúa con representaciones gráficas de agrupación (tales como gráficas de dona por grupos, líneas, tipos de clientes y zonas) y concluye con tablas de detalle (tales como clientes, vendedores, grupos, líneas y artículos).

3. **Organización, secuencia y composición temática** de las hojas o pestañas (tabs) que conforman cada tablero.

---

## Verificación de marcadores embebidos

Sobre la Cuenta AWS Designada, usando AWS CLI con permisos de lectura sobre QuickSight:

```bash
# Inventario general de recursos
aws quicksight list-data-sets   --aws-account-id <ACCOUNT_ID>
aws quicksight list-analyses    --aws-account-id <ACCOUNT_ID>
aws quicksight list-dashboards  --aws-account-id <ACCOUNT_ID>

# Verificación del marcador embebido en una definición específica
aws quicksight describe-analysis-definition  --aws-account-id <ACCOUNT_ID> --analysis-id  <ID>
aws quicksight describe-dashboard-definition --aws-account-id <ACCOUNT_ID> --dashboard-id <ID>
aws quicksight describe-data-set             --aws-account-id <ACCOUNT_ID> --data-set-id  <ID>
```

El marcador embebido se identifica por:

- Para recursos de tipo **Analysis** y **Dashboard**: un parámetro en la sección `ParameterDeclarations` de la definición.
- Para recursos de tipo **Dataset**: un parámetro en la sección `DatasetParameters` de la definición.

En ambos casos, el parámetro está nombrado `FactorBI` y su valor estático por defecto contiene la leyenda referida en el criterio 2.C del Anexo B.

La **ausencia o remoción del marcador no excluye** el carácter de Activo QuickSight Licenciado del recurso, si éste se identifica conforme a los demás criterios (2.A, 2.B o 2.D).

---

## Contacto

Para consultas o aclaraciones relacionadas con este Catálogo, dirigirse a `legal@factorbi.com`.

---

*Última actualización de este documento: ver historial de commits del repositorio.*
