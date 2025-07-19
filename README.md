# 📊 Impacto de la tipografía en conversión de una app de productos alimenticios

Este proyecto analiza si el cambio de fuentes tipográficas en una aplicación móvil afecta el comportamiento del usuario dentro del embudo de ventas. Se empleó un diseño experimental A/A/B con limpieza de datos, segmentación por grupo y análisis estadístico riguroso.

---

## 🎯 Objetivo

Evaluar si el rediseño tipográfico de la interfaz mejora la tasa de conversión dentro de una app de ventas de productos alimenticios, considerando el avance del usuario a través del embudo: inicio → interacción → compra.

---

## 🔍 Contexto Empresarial

Una startup que vende alimentos por app móvil desea modernizar su diseño visual. El equipo de diseño propone una nueva tipografía; la gerencia solicita validación experimental. Se implementa un test A/A/B:

- **Grupo A1 y A2**: versiones con diseño antiguo
- **Grupo B**: versión con tipografía nueva

---

## ⚙️ Flujo de análisis

1. **Lectura de datos desde `logs_exp_us.csv`** con delimitador tab (`\t`)
2. **Estandarización de columnas**: `event`, `id`, `datetime`, `group`
3. **Limpieza y detección de outliers temporales**
4. **Identificación de ventana estable para análisis**
5. **Construcción del embudo de conversión por eventos**
6. **Comparaciones entre grupos** mediante pruebas estadísticas independientes
7. **Corrección por múltiples pruebas** (Bonferroni, alpha = 0.0025)
8. **Visualización de embudos y p-values**

---

## 📊 Resultados clave

- El evento de compra es la última etapa con mayor abandono.
- Grupos A1 y A2 fueron **estadísticamente equivalentes**, validando el diseño experimental.
- El grupo B **no mostró diferencias significativas** frente a los controles.
- Se realizaron **20 pruebas estadísticas independientes** → ningún resultado fue significativo bajo Bonferroni.

📘 Conclusión:  
> *El cambio de fuentes tipográficas no generó impacto estadísticamente significativo en el comportamiento del usuario. El experimento fue válido, reproducible y bien documentado.*

---

## 📁 Estructura del repositorio

```plaintext
├── README.md
├── notebooks/
│   └── analisis_embudo.ipynb          # Notebook con todo el flujo
├── visualizaciones/
│   ├── embudo_conversion.png          # Embudo por etapas
│   └── pvalues_comparacion.png        # P-values corregidos
├── datos/
│   └── logs_exp_us.csv                # Datos simulados del experimento
└── LICENSE

## ▶️ Ejecución del análisis

Puedes acceder al notebook del proyecto de dos maneras:

- 💻 **Descargar y ejecutar localmente**:  
  Abre `notebooks/analisis_embudo.ipynb` en Jupyter, VSCode o cualquier entorno compatible con `.ipynb`.  
  Requiere tener instaladas las siguientes librerías:
  `pandas`, `numpy`, `seaborn`, `matplotlib`, `scipy`, `statsmodels`

- ☁️ **Ejecutar directamente en Google Colab**:  
  [![Abrir en Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/13Pltwq5smixE8HIpspoy5N3SUPZbduFh?usp=sharing)

> El notebook incluye desde la lectura de datos y limpieza temporal hasta la construcción del embudo de ventas y el análisis estadístico con correcciones múltiples. Totalmente reproducible.

## 🧪 Resultados de pruebas estadísticas (Bonferroni alpha = 0.0025)

### Comparación A1 vs A2 (validación A/A)
| Evento           | % en A1  | % en A2  | p-value  | Resultado        |
|------------------|----------|----------|----------|------------------|
| compra_exitosa   | 48.29%   | 46.05%   | 0.11211  | ✅ No significativa |
| ver_carrito      | 50.99%   | 49.23%   | 0.21306  | ✅ No significativa |
| ver_ofertas      | 62.13%   | 60.63%   | 0.27435  | ✅ No significativa |
| inicio_app       | 98.67%   | 98.49%   | 0.58688  | ✅ No significativa |
| tutorial         | 11.19%   | 11.32%   | 0.87916  | ✅ No significativa |

### Comparación B vs A2 (tipografía nueva vs control)
| Evento           | % en B   | % en A2  | p-value  | Resultado        |
|------------------|----------|----------|----------|------------------|
| inicio_app       | 98.35%   | 98.49%   | 0.68196  | ✅ No significativa |
| ver_carrito      | 48.66%   | 49.23%   | 0.68838  | ✅ No significativa |
| compra_exitosa   | 46.57%   | 46.05%   | 0.70659  | ✅ No significativa |
| tutorial         | 11.10%   | 11.32%   | 0.80364  | ✅ No significativa |
| ver_ofertas      | 60.47%   | 60.63%   | 0.91005  | ✅ No significativa |

### Comparación B vs A1+A2 (agregados)
| Evento           | % en B   | % en Control | p-value  | Resultado        |
|------------------|----------|--------------|----------|------------------|
| ver_carrito      | 48.66%   | 50.10%       | 0.23764  | ✅ No significativa |
| inicio_app       | 98.35%   | 98.58%       | 0.42897  | ✅ No significativa |
| ver_ofertas      | 60.47%   | 61.38%       | 0.44718  | ✅ No significativa |
| compra_exitosa   | 46.57%   | 47.16%       | 0.62967  | ✅ No significativa |
| tutorial         | 11.10%   | 11.26%       | 0.84205  | ✅ No significativa |

