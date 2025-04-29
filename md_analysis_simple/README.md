# 🧠 Asistente de Análisis de Datos con OpenAI API

Este notebook permite automatizar análisis exploratorios y visuales a partir de un conjunto de datos en formato Excel (`.xlsx`), utilizando modelos de lenguaje de OpenAI para generar respuestas en lenguaje natural y código Python. Está diseñado como parte de un portafolio personal orientado a ciencia de datos aplicada y análisis asistido por IA.

---

## 💡 ¿Qué hace este notebook?

- Carga automáticamente archivos Excel con múltiples hojas.
- Consolida los datos en un único `DataFrame` para análisis completo.
- Muestra una muestra (`df_sample`) para referencia visual del modelo.
- Formula preguntas analíticas complejas a través de un prompt estructurado.
- Genera respuestas en formato Markdown con código Python explicativo.
- Utiliza visualizaciones estilizadas con `seaborn`.

---

## 🗂️ Estructura del Notebook

### 1. 🔄 Carga de datos (`#Dataset de producción`)
Este bloque permite importar datos reales desde un archivo `.xlsx`.

```python
load_file = 'PATH_TO/FILE.xlsx'
excel_sheet = None
```

> ⚠️ **Importante:** Esta celda puede aparecer como tipo `Raw` en Jupyter.  
> Para que funcione correctamente, **debes cambiarla a tipo `Code`**.  
> Además, si estás trabajando con tus propios datos, comenta o elimina el bloque `# Dataset de pruebas`.

---

### 2. 🧠 Contexto del sistema

Se define de forma modular:

- `contexto_formato`: instrucciones sobre estilo de respuesta (Markdown, código Python, etc.).
- `contexto_tema`: enfoque del análisis (por ejemplo, ecología urbana, censo, etc.).
- Se combinan ambos en `contexto_sistema`.

---

### 3. 🧾 Pregunta al modelo

La pregunta se redacta como un conjunto de pasos específicos para que el modelo entregue una respuesta útil:

```python
pregunta = (
    "1. ¿Cuál es la distribución de los comportamientos observados según la zona (urbana o rural)?\n"
    "2. ¿Qué especies son más comunes en zonas urbanas y cuáles en zonas rurales?\n"
    ...
)
```

---

### 4. 🗣️ Construcción del prompt

El `prompt` integra el contexto, la muestra del `DataFrame`, y la pregunta:

```python
prompt = (
    f"Se muestra una porción de un DataFrame como referencia:\n\n{df_sample}\n\n"
    "Esta muestra es solo ilustrativa. El análisis debe realizarse sobre el DataFrame completo `df_main`.\n\n"
    f"Pregunta del usuario:\n{pregunta}\n\n"
    "Entrega tu respuesta en formato Markdown, incluyendo bloques de código Python cuando sea necesario.\n"
)
```

---

## 🔐 Requisitos previos

| Requisito | Descripción |
|-----------|-------------|
| OpenAI API Key | Debes tener una clave válida de [OpenAI](https://platform.openai.com/). |
| Dependencias | Python ≥ 3.8 con las siguientes librerías: `openai`, `pandas`, `ipywidgets`, `openpyxl`, `seaborn`. |

```bash
# Configurar tu API Key (Linux/macOS)
export OPENAI_API_KEY="sk-..."

# Instalar dependencias
pip install -r requirements.txt
```

---

## 🧪 Dataset de prueba

Se incluye un dataset ficticio de observación de aves en zonas urbanas y rurales. Este contiene variables como:

- Especie
- Zona
- Comportamiento observado
- Temperatura y viento
- Interacción humana
- Observador y hora del día

> Puedes usarlo como entorno de pruebas para verificar el funcionamiento del notebook antes de usar tus propios datos.

---

## 💡 Sugerencias de extensión

- Adaptar el `contexto_tema` a dominios distintos como salud, educación o marketing.
- Agregar nuevos prompts o plantillas para tareas específicas.
- Integrar el sistema en dashboards visuales (`Streamlit`, `Voila`, etc.).
- Incluir validación estadística o uso de bibliotecas como `statsmodels` o `scikit-learn`.

---

## 👤 Autor

**Luis Pineda**  
Ciberseguridad y ciencia de datos
📍 Chile — 2025  
🎓 [Portafolio GitHub](https://github.com/tu_usuario)

> _"Always learning. Always adapting."_ 🚀

