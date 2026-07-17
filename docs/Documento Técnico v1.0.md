# Documento de Arquitectura y Especificación Técnica v1.0

**Proyecto**: Plataforma BI Comercial, Compras y Abastecimiento
**Origen de Datos**: ERP Siesa (SQL Server) & Excel Centralizado
**Entorno de Implementación**: Microsoft Fabric / Power BI Service

Introducción
Este repositorio contiene la arquitectura, el código y la especificación técnica de la solución analítica de inteligencia de negocios de Kooll Importaciones SAS, empresa dedicada a la importación y comercialización de equipos de piscinas y tratamiento de agua en Colombia.
La plataforma consolida la información transaccional proveniente del ERP Siesa junto con las metas presupuestales e inventarios, proporcionando visibilidad en tiempo real para la toma de decisiones críticas en las áreas comercial, compras y abastecimiento.

Objetivos
Centralizar la información comercial, operativa y logística en una única "fuente de la verdad".

* Monitorear el cumplimiento de presupuestos nacionales y regionales con unificación inteligente de metas.
* Optimizar las políticas de compras y abastecimiento mediante métricas de cobertura y control de stock mínimo y máximo.
* Garantizar la seguridad y confidencialidad de la información mediante exclusión de datos financieros sensibles a la fuerza de ventas.

Alcance
La solución abarca tres áreas críticas del negocio:

•	Comercial: Seguimiento de ventas netas, cumplimiento de presupuestos generales y de contado, margen de rentabilidad y evolución temporal por vendedor.
•	Compras: Análisis de órdenes de compra abiertas, cumplimiento de proveedores, tiempos de entrega e importaciones en tránsito.
•	Abastecimiento (Inventarios): Gestión de existencias, cálculo de meses de cobertura, y alertas de desabastecimiento basadas en políticas de stock mínimo/máximo configuradas en el sistema.

Arquitectura
El flujo de datos está diseñado bajo una arquitectura de BI híbrida para garantizar el rendimiento y la seguridad en la nube:

Fuentes de Datos
La solución se alimenta de dos orígenes principales:

ERP Siesa (SQL Server Local):

•	Fact_Ventas: Historial transaccional de facturación (vendedor, cliente, producto, zona, cantidades, montos netos).
•	Dim_Producto: Maestro de referencias de piscinas, filtros, bombas y tratamientos químicos.

Archivos de Control Interno (Excel en OneDrive):

•	Fact_Presupuestos: Cuotas mensuales por asesor y tipo de venta (Contado/Crédito).
•	Politica_Inventarios: Parámetros de stocks mínimos, máximos y lead times de importación.

Modelo de Datos
El diseño implementa un Esquema en Estrella clásico para maximizar el rendimiento de las medidas DAX y simplificar la experiencia de usuario.

Dashboards Desarrollados

Comercial
•	Pestañas Incluidas: 1. Comercial (Rentabilidad), 2. Ventas Generales, 3. Evolución Mensual.
•	Funcionalidades: Vista detallada de facturación vs presupuesto. Semáforo visual para cumplimiento de cuota general y meta de contado.
•	Seguridad: La pestaña "1. Comercial", que contiene márgenes de utilidad en pesos y rentabilidad porcentual, está estrictamente restringida para la fuerza de ventas.

Compras
•	Funcionalidades: Seguimiento a órdenes de compra nacionales e internacionales. Análisis de cumplimiento de fechas de entrega pactadas con proveedores de componentes de tratamiento de agua.

Abastecimiento
•	Funcionalidades: Monitoreo de niveles de stock actual en bodegas. Clasificación automática de SKUs en estado de Sobre-stock, Stock Óptimo, Bajo-stock y Quiebre de Inventario.

KPIs
Las métricas principales se calculan dinámicamente en memoria utilizando DAX:

1.	Ventas Netas ($)
2.	Cumplimiento de Presupuesto (%)
3.	Rentabilidad
4.	Meses de cobertura

Seguridad y Acceso
El acceso al reporte está gobernado bajo los siguientes parámetros de seguridad empresarial:

•	Autenticación Mandatoria: Solo usuarios activos del tenant de Microsoft 365 de la empresa pueden ingresar.
•	Licenciamiento: Cada visor requiere asignación activa de licencia Power BI Pro.
•	Seguridad a nivel de Interfaz (Audiencias): En lugar de restringir datos con RLS (lo cual limitaría la visualización de las ventas cruzadas), se implementó Seguridad de Páginas mediante Audiencias en Power BI App:

Workspace
Plataforma de Alojamiento: Espacio de trabajo corporativo en Microsoft Fabric.

•	Conectividad On-Premises: Configuración de Power BI Gateway (Standard Mode) en el servidor local de la compañía donde se aloja SQL Server para asegurar la conectividad directa con las bases de datos transaccionales de Siesa.
•	Esquema de Actualización: Programado 4 veces al día en horarios estratégicos del negocio (7:00, 12:00, 15:00 y 18:00).

Mejoras Futuras
•	Base de Datos para Presupuestos: Migración de los presupuestos comerciales actualmente registrados en archivos de Microsoft Excel hacia una tabla estructurada dentro de la base de datos de SQL Server para eliminar el riesgo de manipulación de archivos planos.
•	Automatización de Carga ERP: Integración de procesos automáticos en Power Automate Desktop para programar la extracción directa de Siesa ERP al almacenamiento compartido en OneDrive Corporativo.

Integración con IA
•	Pronóstico de Demanda Inteligente: Implementación futura de modelos predictivos en Azure Machine Learning integrados a Fabric, orientados a proyectar los requerimientos de inventario para la importación de productos “paretos” reduciendo el stock inmovilizado.
•	Copilot para Directores: Habilitación de narrativas inteligentes basadas en lenguaje natural dentro del reporte comercial para que la gerencia reciba explicaciones contextuales de las variaciones del margen mensual automáticamente.
