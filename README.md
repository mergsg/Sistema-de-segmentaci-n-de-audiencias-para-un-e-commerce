# Sistema de segmentación de audiencias para un e-commerce
Generación de segmentos estratégicos para el equipo de CRM & Email Marketing, listos para activación en Salesforce Marketing Cloud.
El dataset sintético utilizado proviene de la tabla transaccional AuroraRetail en BigQuery

##Objetivo del proyecto
Diseñar y documentar una serie de audiencias de clientes, cada una con criterios de negocio definidos por el equipo de Marketing.
El proyecto debe:
- Traducir requisitos comerciales en reglas SQL claras
- Construir queries limpias, estructuradas y eficientes
- Entregar resultados reproducibles mes a mes
- Generar un solo archivo _.sql_ con todos los segmentos

##Segmentos construidos
A partir de la conversación con el equipo de Marketing y los requisitos proporcionados, se implementaron los siguientes segmentos:

1. Dormant Clients
Clientes que compraron durante el último año, pero no han comprado en los últimos 6 meses.
Los pasos incluyen:
- Identificar compradores activos en la ventana principal
- Excluir clientes con compras recientes
- Excluir nuevos clientes cuya primera compra fue reciente
- Seleccionar un producto de referencia por cliente

2. Holiday High Spenders
Clientes con un gasto neto ≥ £500 durante la campaña de noviembre–diciembre.
Incluye:
- Cálculo del gasto total por cliente
- Selección de producto de referencia
- Priorizar últimos compradores

3. Bulk Buyers
Clientes que realizaron órdenes grandes (≥10 productos distintos o ≥100 unidades) en los últimos 12 meses.

4. One-Time Buyers
Clientes que realizaron exactamente una compra en el último año.

5. Cross-Border Clients
Clientes con al menos dos órdenes enviadas fuera de Reino Unido en el último año.

##Principales consultas SQL
El archivo _audiences.sql_ utiliza:
- CTEs (WITH) para estructurar cada paso
- Filtros temporales precisos
- Agrupaciones (COUNT DISTINCT, SUM)
- Joins entre CTEs
- Selección de producto de referencia
- Ordenación por fecha de última compra
La lógica está claramente segmentada con comentarios para cada audiencia.

##Tecnologías utilizadas
- ###Google BigQuery SQL
- Ventanas temporales definidas por negocio
- Transformación de datos exclusivamente en SQL
- Estructuración con CTEs para claridad y mantenibilidad
