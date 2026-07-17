# plataforma-inteligencia-comercial
# Plataforma de Inteligencia Comercial

## Descripción

La Plataforma de Inteligencia Comercial es una solución empresarial desarrollada sobre el ecosistema Microsoft (Fabric y Power BI), diseñada para centralizar, transformar y visualizar información estratégica relacionada con ventas, compras y abastecimiento.

Su objetivo es habilitar una cultura organizacional orientada a la toma de decisiones basada en datos (Data-Driven), mediante la implementación de procesos analíticos, automatización de flujos de trabajo y capacidades preparadas para la integración futura de Inteligencia Artificial.

Este proyecto constituye una iniciativa de transformación digital enfocada en proporcionar visibilidad operativa y estratégica a las diferentes áreas de la organización.

---

## Objetivos del Proyecto

* Centralizar la información comercial y operativa.
* Optimizar la toma de decisiones mediante analítica avanzada.
* Implementar indicadores clave de desempeño (KPIs) en tiempo real.
* Automatizar procesos relacionados con la generación y consumo de información.
* Garantizar la calidad, consistencia y trazabilidad de los datos.
* Construir una arquitectura escalable y preparada para IA.

---

## Arquitectura General

```text
Fuentes de Datos
        │
        ▼
Procesos ETL
(Power Query / Python)
        │
        ▼
Microsoft Fabric
        │
        ▼
Modelo Semántico
(Power BI)
        │
        ▼
Dashboards
        │
        ▼
Usuarios Finales
(Ventas, Marketing, Gerencia)
```

---

## Módulos Implementados

### Dashboard Comercial

* Seguimiento de ventas.
* Cumplimiento de presupuesto.
* Análisis de clientes.
* * Análisis de productos
* Desempeño comercial.
* KPIs estratégicos.

### Dashboard de Compras y Abastecimiento

* Control de inventarios.
* Stock mínimo y máximo.
* Seguimiento de compras.
* Indicadores de abastecimiento.
* Análisis de rotación de productos.

---

## Tecnologías Utilizadas

| Tecnología       | Uso                                   |
| ---------------- | ------------------------------------- |
| Power BI         | Visualización y analítica             |
| Microsoft Fabric | Plataforma de datos                   |
| Python           | Automatización y procesamiento        |
| SQL              | Consulta y modelado de datos          |
| DAX              | Cálculos y KPIs                       |
| Power Query      | Transformación de datos               |
| Excel            | Integración y análisis complementario |
| Git & GitHub     | Versionamiento y documentación        |

---

## Modelo de Datos

La solución implementa un enfoque de modelado dimensional basado en esquema estrella (Star Schema), compuesto por tablas de hechos y dimensiones para garantizar escalabilidad, rendimiento y mantenibilidad.

Ejemplos:

* FactVentas
* FactCompras
* FactInventario
* DimFecha
* DimCliente
* DimProducto
* DimVendedor

---

## Seguridad

La plataforma está diseñada para operar bajo mecanismos de control de acceso administrados desde el ecosistema Microsoft, contemplando:

* Microsoft Entra ID.
* Administración de permisos por roles.
* Acceso centralizado mediante Power BI Service.

---

## Roadmap

### Fase 1

* Arquitectura de solución.
* Documentación técnica.
* Versionamiento.

### Fase 2

* Dashboards comerciales.
* Dashboard de compras y abastecimiento.

### Fase 3

* Seguridad y acceso.

### Fase 4

* Automatizaciones.
* Integración con Power Automate.

### Fase 5

* Inteligencia Artificial.
* Agentes inteligentes.
* IA Generativa.
* Copilot.

---

## Impacto Esperado

* Incrementar la velocidad de toma de decisiones.
* Mejorar la visibilidad de la operación.
* Optimizar la gestión comercial.
* Reducir tiempos de análisis manual.
* Fortalecer la cultura Data-Driven.
* Preparar la organización para la adopción de Inteligencia Artificial.

---

## Estado del Proyecto

> En desarrollo activo.

Actualmente, los módulos de Ventas y Compras/Abastecimiento se encuentran en producción, mientras se continúa trabajando en automatizaciones, documentación técnica e integración futura con capacidades de Inteligencia Artificial.

---

## Autor

**Juan David Restrepo Marulanda**

* Ingeniero de Sistemas
* Business Intelligence & Automation
* AI Engineer
* Especialista en Inteligencia Artificial y Automatización

---

## Licencia

Este proyecto es de carácter demostrativo y forma parte del portafolio profesional del autor.
