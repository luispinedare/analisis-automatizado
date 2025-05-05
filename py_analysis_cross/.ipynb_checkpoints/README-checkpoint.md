# 🧠 Laboratorio Interactivo de Ciencia de Datos con Código Ejecutable

Este notebook permite realizar análisis estadísticos sobre archivos Excel utilizando modelos de lenguaje de OpenAI, **capaces de generar y ejecutar código Python automáticamente** dentro del entorno de Jupyter Notebook.

Está diseñado como una herramienta interactiva y extensible para quienes deseen integrar IA en sus flujos de trabajo analítico, con especial énfasis en análisis cruzado de múltiples DataFrames.

---

## 💡 ¿Qué hace este notebook?

- Carga uno o más archivos Excel `.xlsx` con múltiples hojas.
- Presenta muestras (`df_sample_1`, `df_sample_2`) para referencia visual del modelo.
- Formula preguntas en lenguaje natural que el modelo responde con **código Python ejecutable**.
- Permite editar y ejecutar el código generado directamente desde widgets en la interfaz.
- Exporta los resultados como archivos `.csv` si la consulta lo solicita.

---

## 🧰 ¿Qué tiene de especial este laboratorio?

- Integra un sistema de *prompts estructurados* que guía al modelo para generar solo código útil y directamente ejecutable.
- Trabaja con **dos DataFrames distintos** (`df_main_1`, `df_main_2`) cruzando información entre ellos.
- Crea un **widget interactivo** para editar y ejecutar el código sugerido, con visualización inmediata del resultado.

---

## 🗂️ Estructura del Notebook

### 1. 🧪 Dataset de prueba (opcional)
Incluye un dataset sintético de observación de aves, útil para pruebas. Este contiene:

- Especie, zona, comportamiento observado
- Temperatura, humedad, viento
- Interacción humana, presencia de predadores
- Fecha y observador

También incluye un segundo DataFrame con condiciones ecológicas por especie y zona.

```python
# df_main_1 → Observaciones de campo
# df_main_2 → Condiciones ecológicas cruzadas
```

---

### 2. 📂 Carga de datos personalizados
Puedes reemplazar los datos de prueba cargando tus propios archivos Excel. Para eso:

```python
load_file_1 = 'PATH/TO/archivo_1.xlsx'
load_file_2 = 'PATH/TO/archivo_2.xlsx'
```

> ⚠️ Algunas celdas de carga están en formato `Raw`. Cámbialas a tipo `Code` para que funcionen correctamente.

---

### 3. 🧠 Contexto del sistema
Definido en dos partes:

- `contexto_formato`: instrucciones sobre cómo presentar el código (formato JSON, uso de seaborn, etc.)
- `contexto_tema`: indica que el modelo debe centrarse en análisis de datos, sin generar nuevos datasets ni cargar archivos.

```python
contexto_sistema = contexto_formato + "\n" + contexto_tema
```

---

### 4. ❓ Pregunta en lenguaje natural
Ejemplo de consulta al modelo:

```python
pregunta = (
    "¿Puedes identificar qué especies de aves se observaron con mayor frecuencia en cada zona? "
    "Haz un conteo total de individuos por especie y zona usando `df_main_1`. "
    "Genera una visualización usando seaborn, y exporta los resultados como CSV."
)
```

---

### 5. 🧠 Generación y ejecución de código
El modelo devuelve código en formato JSON. Este se carga automáticamente en un `widget`, donde puedes:

- Revisar y editar el código generado
- Presionar "Ejecutar" para mostrar resultados directamente en el notebook

---

## ⚠️ Consideraciones técnicas

### ✅ Requisitos del entorno

Este notebook requiere las siguientes dependencias:

```bash
pip install numpy pandas matplotlib seaborn scipy openpyxl ipywidgets
```

### ⚠️ Para ejecutar los widgets:

Si usas Jupyter Notebook (no JupyterLab), asegúrate de habilitar `ipywidgets`:

```bash
jupyter nbextension enable --py widgetsnbextension --sys-prefix
```

Si usas **JupyterLab**, necesitas instalar la extensión:

```bash
pip install jupyterlab_widgets
```

> También puedes verificar si `ipywidgets` funciona correctamente ejecutando:
> `import ipywidgets as widgets; widgets.IntSlider()`

---

## 💡 Sugerencias de uso

- Personaliza el `contexto_tema` si necesitas aplicar el sistema a otras áreas: salud, ventas, educación, etc.
- Añade preguntas en lenguaje natural con necesidades específicas (filtrar, agrupar, visualizar, exportar).
- Usa esta plantilla como base para desarrollar asistentes analíticos en otros dominios.

---

## 👤 Autor

**Luis Pineda**  
Ciberseguridad y ciencia de datos  
📍 Chile — 2025  
🎓 [Portafolio GitHub](https://github.com/tu_usuario)

> _"Always learning. Always adapting."_ 🚀
