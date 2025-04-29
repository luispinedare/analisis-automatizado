# 🧠 Integración de OpenAI API en Jupyter Notebook

Este notebook demuestra cómo integrar la API de OpenAI con un entorno Jupyter para obtener respuestas inteligentes, generar explicaciones, y realizar tareas de asistencia técnica usando lenguaje natural. Está orientado a estudiantes, desarrolladores o analistas que buscan automatizar consultas y análisis dentro del propio notebook.

---

## 💡 ¿Qué hace este notebook?

- Inicializa un cliente de OpenAI en Python usando `openai`.
- Define una función que envía preguntas a la API y recupera respuestas generadas por un modelo de lenguaje.
- Usa `Markdown` para presentar las respuestas de forma limpia y legible.
- Muestra ejemplos de uso con consultas técnicas sobre Jupyter, Python y visualización de datos.

---

## 🗂️ Estructura del Notebook

### 1. ⚙️ Inicialización de cliente OpenAI
Se importa la biblioteca `openai` y se instancia un cliente.

```python
from openai import OpenAI
client = OpenAI()
```

---

### 2. 🔄 Función para consulta a la API
La función `obtener_respuesta_con_dataframe(pregunta)` permite enviar preguntas al modelo GPT-4o y devuelve respuestas en texto.

```python
def obtener_respuesta_con_dataframe(pregunta):
    completion = client.chat.completions.create(
        model="gpt-4o",
        messages=[
            {"role": "system", "content": "Eres un ayudante que es experto en Python, Pandas y Matplotlib"},
            {"role": "user", "content": pregunta}
        ]
    )
    return completion.choices[0].message.content
```

---

### 3. 🧪 Ejemplos de uso
Se muestran ejemplos prácticos para usar la función y mostrar las respuestas:

#### 📌 Pregunta: ¿Cómo integrar OpenAI con Jupyter?
```python
pregunta = "¿Cómo podrías ayudarme a integrar OpenAI y Jupyter?"
respuesta = obtener_respuesta_con_dataframe(pregunta)
display(Markdown(respuesta))
```

#### 📌 Pregunta: ¿Qué bibliotecas se recomiendan para visualización?
```python
nueva_pregunta = "¿Qué bibliotecas recomiendas para visualización de datos en Python?"
nueva_respuesta = obtener_respuesta_con_dataframe(nueva_pregunta)
display(Markdown(nueva_respuesta))
```

---

## 🔐 Requisitos previos

| Requisito | Descripción |
|-----------|-------------|
| OpenAI API Key | Una clave activa desde [OpenAI](https://platform.openai.com/). |
| Librerías | Asegúrate de tener: `openai`, `IPython`, `markdown`, `jupyter`, `python ≥ 3.8`. |

```bash
# Configurar variable de entorno
export OPENAI_API_KEY="sk-..."

# Instalar librerías necesarias
pip install openai IPython jupyter
```

---

## 💡 Sugerencias de extensión

- Agregar manejo de errores más robusto con logs o mensajes personalizados.
- Crear una interfaz interactiva con `ipywidgets` para enviar preguntas.
- Integrar el análisis con visualización automatizada en base a las respuestas.
- Extender a otros endpoints de OpenAI como imágenes o embeddings.

---

## 👤 Autor

**Luis Pineda**  
Ciberseguridad y ciencia de datos  
📍 Chile — 2025  
🎓 [Portafolio GitHub](https://github.com/tu_usuario)

> _"Always learning. Always adapting."_ 🚀
