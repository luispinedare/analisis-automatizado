# 🧠 Laboratorios de Análisis Automatizado con OpenAI API

Este conjunto de notebooks explora cómo usar modelos de lenguaje de OpenAI para realizar análisis exploratorio, visual y estadístico sobre conjuntos de datos, tanto reales como simulados. Algunos notebooks generan respuestas cualitativas estructuradas en Markdown, mientras que otros permiten generar y ejecutar directamente código Python sobre el dataset.

> Cada notebook está diseñado como una herramienta modular, adaptable a distintos dominios (ecología, censos, educación, etc.) y con énfasis en claridad, automatización y reproducibilidad.

---

## 📂 Notebooks incluidos

| Notebook | Tipo de análisis | Cruza DataFrames | Genera código ejecutable | Descripción |
|---------|------------------|------------------|---------------------------|-------------|
| `basic_prompt.ipynb` | Markdown + cualitativo | ❌ | ❌ | Notebook base de prueba con un prompt simple para generar respuestas en lenguaje natural. |
| `md_analysis_simple.ipynb` | Markdown estructurado | ❌ | ❌ | Genera informes cualitativos con estructura fija a partir de un solo DataFrame. |
| `md_analysis_cross.ipynb` | Markdown estructurado | ✅ | ❌ | Integra dos DataFrames cruzando variables clave (`Zona`, `Especie`). Ideal para análisis ecológico. |
| `py_analysis_simple.ipynb` | Código Python ejecutable | ❌ | ✅ | Permite generar, editar y ejecutar código Python generado automáticamente para un único DataFrame. |
| `py_analysis_cross.ipynb` | Código Python ejecutable | ✅ | ✅ | Integra dos DataFrames cruzados y permite ejecutar código directamente, con widgets interactivos. |

---

## 🔍 ¿Qué pueden hacer estos notebooks?

- Cargar uno o más archivos `.xlsx` con múltiples hojas.
- Previsualizar las primeras filas con estilos personalizados.
- Construir automáticamente prompts para análisis avanzados.
- Generar respuestas en formato Markdown (notebooks `md_*.ipynb`).
- Generar y ejecutar código en vivo con `ipywidgets` (notebooks `py_*.ipynb`).
- Exportar resultados (CSV, gráficas, análisis interpretativo).

---

## 📁 Estructura general

1. **Carga del archivo Excel**: desde uno o dos archivos `.xlsx`.
2. **Visualización de muestra (`df_sample`)**: tabla con estilo para referencia.
3. **Definición del contexto**: incluye estilo, lenguaje y tema del análisis.
4. **Redacción de la pregunta analítica**: guía la respuesta generada.
5. **Generación del prompt final**: combinación de muestra, contexto y pregunta.
6. **Llamado a la API de OpenAI**: usa `openai.ChatCompletion.create`.
7. **Visualización de la respuesta**:
   - Como informe estructurado (`Markdown`) o
   - Como código editable y ejecutable (con `ipywidgets`).

---

## 🧰 Requisitos técnicos

| Elemento | Detalles |
|---------|----------|
| **Lenguaje** | Python ≥ 3.8 |
| **Entorno recomendado** | Jupyter Notebook (Anaconda) |
| **API OpenAI** | Necesitas una clave activa |
| **Librerías** | `openai`, `pandas`, `numpy`, `matplotlib`, `seaborn`, `ipywidgets`, `openpyxl`, `scipy` |

```bash
# Instalación sugerida
pip install openai pandas numpy matplotlib seaborn ipywidgets openpyxl scipy

# Habilitar widgets (si usas Jupyter clásico)
jupyter nbextension enable --py widgetsnbextension --sys-prefix
```

---

## 🧪 Dataset de pruebas

Todos los notebooks incluyen un dataset ficticio sobre **observación de aves** en distintas zonas (urbana, rural, suburbana), incluyendo variables como:

- Especie, zona, comportamiento observado
- Temperatura, viento, humedad
- Interacción humana y predadores
- Condiciones ecológicas por especie y zona

> Este dataset puede ser reemplazado fácilmente por tus propios archivos `.xlsx`.

---

## 💬 Ejemplos de análisis

- ¿Qué especies se observan más en zonas urbanas?
- ¿Existen diferencias de comportamiento según temperatura o viento?
- ¿Cómo afecta la interacción humana a la cantidad de individuos?
- ¿Puedes graficar el comportamiento por especie con `seaborn`?
- ¿Puedes aplicar una prueba t de Student entre zonas?

---

## 💡 Ideas para expandir

- Adaptar el `contexto_tema` para distintos dominios (salud, transporte, clima).
- Usar notebooks `py_*.ipynb` como motor para dashboards Streamlit.
- Integrar validaciones estadísticas más robustas (`statsmodels`, `sklearn`).
- Agregar generación de reportes PDF o visualizaciones interactivas.

---

## 👤 Autor

**Luis Pineda**  
Ciberseguridad y ciencia de datos  
📍 Chile — 2025  
🎓 [Portafolio GitHub](https://github.com/tu_usuario)

> _"Always learning. Always adapting."_ 🚀