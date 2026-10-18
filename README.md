<h1 align="center"> Análisis de Ventas en E-Commerce<br>Supermercado Online</h1> <p align="center"> Proyecto final del curso <b>Business Intelligence</b><br> Talento Tech · Buenos Aires Aprende · Agencia de Habilidades para el Futuro · 80 hs reloj </p> <p align="center"> <img src="https://img.shields.io/badge/estado-completado-5aa42d" alt="Estado"> <img src="https://img.shields.io/badge/herramientas-Google%20Sheets%20%7C%20Looker%20Studio-blue" alt="Herramientas"> <img src="https://img.shields.io/badge/curso-Business%20Intelligence-1f3864" alt="Curso"> </p>

---

##  Descripción

Proyecto de consultoría BI para un **supermercado online** ficticio. A partir de un modelo de datos de cinco tablas relacionadas, se realizó el ciclo completo de análisis: evaluación de calidad de datos, limpieza, integración, estadística descriptiva, visualización en un dashboard interactivo y recomendaciones de negocio.

**Pregunta central:** ¿dónde está concentrado el ingreso del negocio y qué riesgos implica?

---

## Objetivos

- Evaluar la calidad del dataset con un checklist de criterios.
- Limpiar y preparar los datos para el análisis.
- Integrar las tablas en una vista única (ventas por región, categoría, método de pago y período).
- Calcular estadística descriptiva sobre el ticket de compra.
- Construir un dashboard interactivo y comunicar conclusiones accionables.
- Incorporar el contexto **ético y legal** del manejo de datos.

---

## Modelo de datos

El archivo [`ecommerce.xlsx`](./ecommerce.xlsx) contiene las siguientes hojas:

| Hoja | Contenido | Registros |
|------|-----------|-----------|
| `Ventas_Original` | Dataset sin modificar (ID_Venta, Fecha, ID_Cliente, ID_Producto, Cantidad, Método_Pago, Estado) | 3.029 |
| `Ventas_Limpia` | Ventas sin duplicados, enriquecidas con cliente, región, producto, categoría, precio y total | 3.000 |
| `Clientes` | Nombre, apellido, email, fecha de registro y región | 325 |
| `Productos` | Producto, categoría, precio unitario y stock | 38 |
| `Métodos_Pago` | Métodos de pago disponibles | 5 |
| `Categorías` | Categorías de productos | 8 |
| `Análisis_Exploratorio` | Estadística descriptiva con fórmulas | — |

**Período analizado:** enero – diciembre de 2024 · **Regiones:** Buenos Aires, Centro, Patagonia, Cuyo, NEA y NOA.

---

## Calidad y limpieza de datos

Se aplicaron 6 criterios de calidad sobre los 5 datasets:

| Criterio | Resultado |
|----------|-----------|
| Completitud | ✅ OK |
| Unicidad de IDs | ✅ OK |
| Consistencia de formatos | ✅ OK |
| Integridad referencial | ✅ OK |
| Validación de email | ⏳ Pendiente (aplicar `REGEXMATCH`) |
| Duplicados en ventas | ⚠️ 29 filas exactamente duplicadas → eliminadas |

**Impacto:** sin la limpieza, la facturación aparecería inflada en aprox. **$1.000**.

**Técnicas utilizadas:** `TRIM`, `PROPER` / `UPPER`, validación de cálculos (`Cantidad × Precio_Unitario`), `COUNTIF` para unicidad, validación de rangos con `IF`, congelado de encabezados.

**Integración:** `VLOOKUP` / `XLOOKUP` para traer producto, categoría y región; `SUMIF` / `COUNTIF` para agregaciones.

---

## Resultados principales

### Estadística descriptiva (columna `Total`, 3.000 ventas)

| Métrica | Valor |
|---------|-------|
| Facturación total 2024 | **$103.103,19** |
| Media (ticket promedio) | $34,37 |
| Mediana | $26,16 |
| Moda | $32,70 |
| Desvío estándar | $27,41 |
| Mínimo / Máximo | $3,25 / $171,36 |

La media supera a la mediana: unas pocas compras de alto valor (Carnicería, Congelados) elevan el promedio.

### Ventas por categoría

| Categoría | % del total |
|-----------|------------|
| 🥩 Carnicería | 27,1 % |
| 🥛 Lácteos | 15,6 % |
| 🧊 Congelados | 14,5 % |
| 🍞 Panadería | 12,3 % |
| 🥤 Bebidas | 11,3 % |
| 🥬 Frutas y Verduras | 7,6 % |
| 🍪 Galletitas y Snacks | 6,9 % |
| 🥫 Conservas | 4,7 % |

### Ventas por método de pago

Mercado Pago (29,0 %) · Transferencia (26,3 %) · Efectivo (18,3 %) · Tarjeta de débito (17,8 %) · Tarjeta de crédito (8,6 %)

### Ventas por región

Buenos Aires lidera con ~$36.900 y 1.032 ventas, seguida por Centro, Patagonia y Cuyo. NOA es la región con menor participación (63 ventas).

---

## Dashboard interactivo

Dashboard construido en **Looker Studio** con filtros por fecha, categoría, región y estado, que incluye:

- KPIs: facturación total, nº de transacciones, ventas completas y ticket promedio.
- Ventas por categoría de producto.
- Ventas por región geográfica.
- Evolución de ventas mensuales 2024.

**[Ver dashboard](https://datastudio.google.com/s/tvCQ1XNYIMY)**

---

## Insight y recomendación

> **"Una sola categoría no puede ser el plan."**

Carnicería concentra el **27 %** de la facturación, lo que expone al negocio a riesgos de precio, abastecimiento y cambios en el consumo. Conservas y Galletitas tienen tickets promedio bajos (~$11 y ~$17), lo que indica volumen sin captura de valor.

**Acciones propuestas:**

1. Combos que vinculen Carnicería con Congelados y Bebidas.
2. Promociones específicas en categorías de bajo ticket.
3. Campañas estacionales para distribuir la demanda a lo largo del año.
4. **Meta 2025:** que ninguna categoría supere el 20 % de la facturación.

---

## Contexto ético y legal

Se analizó el caso **Facebook – Cambridge Analytica (2018)** y se aplicaron sus lecciones al proyecto:

| Principio | Aplicación |
|-----------|-----------|
| Consentimiento informado | Datos públicos o sintéticos |
| Minimización de datos | Solo los datos necesarios para el análisis |
| Transparencia | Procesos documentados en el informe y el checklist |
| Seguridad | Archivos compartidos con permisos controlados |
| No discriminación algorítmica | Análisis diseñados para decisiones justas |

---

## Investigación Fuentes Públicas de Datos

- [Kaggle – UCI E-Commerce Dataset](https://www.kaggle.com/)
- [Statista – E-Commerce Statistics](https://www.statista.com/)
- [INDEC – Comercio Electrónico](https://www.indec.gob.ar/)

---

## Tecnologías

- **Google Sheets / Excel:** limpieza, fórmulas e integración de datos
- **Looker Studio (Data Studio):** dashboard interactivo
- **Estadística descriptiva:** media, mediana, moda, desvío estándar, rangos

---

## Estructura del repositorio

```
├── README.md
├── ecommerce.xlsx                     # Dataset y análisis
├── Informe_Pre-Entrega_BI.pdf         # Informe del proyecto
└── Dashboard_Supermercado_Online.pdf  # Captura del dashboard
```

---

## Certificación

Curso de **Business Intelligence** · Talento Tech, Buenos Aires Aprende (Ministerio de Educación, Agencia de Habilidades para el Futuro) · 80 horas reloj · Julio 2026.

Certificado verificable en mi [perfil de LinkedIn](https://www.linkedin.com/in/matiaurelio/), sección "Licencias y certificaciones".

---

## Autor

**Matias Nicolas Aurelio**
Curso de Business Intelligence · Talento Tech 2026

[LinkedIn](https://www.linkedin.com/in/matiaurelio/)

---

⭐ Si te resultó útil este proyecto, ¡dejá una estrella al repositorio!
