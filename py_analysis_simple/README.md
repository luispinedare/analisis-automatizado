# 📊 Asistente de Análisis Automatizado con OpenAI

Este notebook permite realizar análisis exploratorios, estadísticas descriptivas y visualizaciones directamente desde un archivo Excel con un solo DataFrame. Utiliza la API de OpenAI para generar respuestas en lenguaje natural junto con código Python ejecutable que puedes revisar, modificar y correr con widgets interactivos.

Está pensado como una herramienta educativa y profesional para científicos de datos, investigadores o estudiantes que quieran acelerar sus análisis con ayuda de modelos de lenguaje.

---

## 💡 ¿Qué hace este notebook?

- Carga un archivo Excel (`.xlsx`) con una hoja de datos.
- Muestra una porción inicial del DataFrame (`df_sample`) como referencia visual.
- Construye un **prompt estructurado** para enviar preguntas a OpenAI.
- Genera código Python ejecutable que puedes editar antes de correrlo.
- Utiliza `seaborn` para visualizaciones limpias y estandarizadas.
- Permite exportar resultados, como gráficos o CSVs, desde el análisis generado.

---

## 🗂️ Estructura del Notebook

### 1. 📁 Carga del archivo Excel

```python
load_file = 'PATH_TO/your_dataset.xlsx'
sheet_name = 'Nombre_de_la_hoja'
```

> ⚠️ **IMPORTANTE:** esta celda puede estar marcada como `Raw` en Jupyter.  
> Para que funcione, **debes cambiarla a tipo `Code`** manualmente.

---

### 2. 🔍 Visualización del DataFrame

Se genera automáticamente una muestra (`df_sample`) para mostrar cómo luce el dataset, sin cargarlo completo en memoria en el prompt. El DataFrame completo está disponible en la variable global `df_main`.

---

### 3. 🧠 Contexto del sistema

El análisis sigue una estructura modular:

- `contexto_formato`: instrucciones sobre estilo (Markdown, Python, seaborn, etc.).
- `contexto_tema`: define que el asistente es un analista de datos que opera sobre un solo DataFrame (`df_main`).
- El modelo recibe estas instrucciones al construir el prompt.

---

### 4. 💬 Formulación de la pregunta

Ejemplo de pregunta:

```python
pregunta = (
    "Puedes realizar un análisis estadístico de la variable 'Duración_observación_min' agrupada por 'Zona'? "
    "Incluye media, desviación estándar y un test de comparación si es posible. "
    "¿Puedes graficar la distribución de estas duraciones por zona con seaborn? "
    "Finalmente, exporta la tabla resumen como CSV."
)
```

---

### 5. ⚙️ Generación de código y widgets

El código generado por OpenAI se muestra automáticamente en un área de texto editable con botón de ejecución.

```python
codigo_python = obtener_respuesta_con_dataframe(pregunta)

if codigo_python:
    widget_codigo, boton_ejecutar, output_resultado = crear_widgets(codigo_python)
    display(widget_codigo, boton_ejecutar, output_resultado)
```

Puedes modificar el código antes de ejecutarlo.

---

## 🧪 Dataset de prueba

El notebook incluye una base de datos ficticia de observaciones de aves como entorno de pruebas. Variables incluidas:

- Especie
- Zona (Urbana, Rural, Suburbana)
- Temperatura, humedad, viento
- Comportamiento
- Interacción humana y presencia de predadores
- Fecha, hora y observador

---

## 🔐 Requisitos previos

| Requisito       | Descripción                                                                 |
|------------------|-----------------------------------------------------------------------------|
| OpenAI API Key   | Necesitas una clave válida de [OpenAI](https://platform.openai.com/account/api-keys). |
| Python ≥ 3.8     | Idealmente en un entorno Anaconda o virtualenv.                            |
| Librerías        | `openai`, `pandas`, `ipywidgets`, `seaborn`, `matplotlib`, `numpy`, `scipy`, `openpyxl` |

```bash
# Configura tu clave de API
export OPENAI_API_KEY="sk-..."

# Instala dependencias
pip install openai pandas ipywidgets seaborn matplotlib numpy scipy openpyxl
```

> ⚠️ No olvides ejecutar:
> 
> ```bash
> jupyter nbextension enable --py widgetsnbextension --sys-prefix
> ```

---

## 🎨 Sugerencias de extensión

- Agregar más plantillas de preguntas.
- Incluir más funciones estadísticas (ANOVA, correlaciones, etc.).
- Adaptar el análisis a temas como salud pública, educación o economía.
- Integrarlo a dashboards con Streamlit o Gradio.

---

## 👤 Autor

**Luis Pineda**  
Ciberseguridad y ciencia de datos  
📍 Chile — 2025  
🎓 [Portafolio GitHub](https://github.com/tu_usuario)

> _"Always learning. Always adapting."_ 🚀