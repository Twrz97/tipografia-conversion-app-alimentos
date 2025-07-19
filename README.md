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
