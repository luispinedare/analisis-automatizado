# 🧠 Asistente de Análisis de Datos con OpenAI API — Versión Multitabla

Este notebook permite automatizar análisis exploratorios cruzando **dos conjuntos de datos complementarios**, típicamente almacenados en hojas separadas de archivos Excel (`.xlsx`). Usa la API de OpenAI para generar explicaciones, visualizaciones y código Python en formato Markdown.  
Es ideal para análisis ecológicos, censales o cualquier escenario donde se desee integrar datos por múltiples dimensiones (ej. especie, zona, tiempo).

---

## 💡 ¿Qué hace este notebook?

- Carga dos archivos `.xlsx` con múltiples hojas.
- Permite seleccionar dinámicamente las hojas a analizar.
- Presenta una muestra (`df_sample_1`, `df_sample_2`) para referencia visual del modelo.
- Genera análisis cruzados usando `df_main_1` y `df_main_2`, enlazados por columnas comunes (`Zona`, `Especie`, etc.).
- Formula preguntas estructuradas que incluyen instrucciones específicas para generar una respuesta enriquecida.
- Responde en formato Markdown con visualizaciones estilizadas y código explicativo.

---

## 🗂️ Estructura del Notebook

### 1. 📂 Carga de datos (`# Configuración DataFrame`)

```python
load_file_1 = 'PATH_TO/FILE_A.xlsx'
load_file_2 = 'PATH_TO/FILE_B.xlsx'
```

> ⚠️ Estas celdas vienen como `Raw` por defecto en Jupyter.  
> Para que funcionen, **debes convertirlas a tipo `Code`**.  
> Puedes reemplazar los archivos por los tuyos para realizar análisis personalizados.

---

### 2. 🧠 Contexto del sistema

Separado en dos partes:

- `contexto_formato`: Define el formato de salida (Markdown, estilo Seaborn, uso de bloques de código, etc.).
- `contexto_tema`: Explica el dominio del análisis (ecología, urbanismo, salud, etc.).

Ambos se combinan en `contexto_sistema`, que guía el comportamiento del modelo.

---

### 3. 🧾 Modelo de respuesta

El modelo sigue una plantilla como:

```markdown
### Análisis Ecológico de Observaciones de Aves

#### 1. Patrones de comportamiento según especie y zona
...

#### 2. Factores ambientales asociados (temperatura, viento, predadores)
...

#### 3. Cruce con condiciones ecológicas por zona y especie
...

#### 4. Interacción humana y su impacto
...

#### 5. Visualizaciones relevantes
...

#### 6. Observaciones adicionales
...
```

> Puedes modificar el `modelo_respuesta` para adaptarlo a otras estructuras de entrega: informes técnicos, artículos divulgativos, diagnósticos sectoriales, etc.

---

### 4. 🔧 Construcción del Prompt

El `prompt` combina:

- Fragmentos visibles de los DataFrames (`df_sample_1`, `df_sample_2`)
- Instrucciones sobre cómo generar la respuesta
- La pregunta planteada por el usuario

Esto garantiza que el modelo genere respuestas coherentes, contextualizadas y con estructura homogénea.

---

### 5. 📬 Consulta al modelo

La pregunta es ingresada manualmente o generada automáticamente. Se lanza una petición a la API de OpenAI y la respuesta es desplegada en Markdown.

---

## 🔐 Requisitos previos

| Requisito        | Descripción                                                                 |
|------------------|-----------------------------------------------------------------------------|
| OpenAI API Key   | Debes tener una clave válida de [OpenAI](https://platform.openai.com/)     |
| Dependencias     | Python ≥ 3.8 con: `openai`, `pandas`, `openpyxl`, `numpy`, `seaborn`, `matplotlib` |

```bash
# Exportar clave API
export OPENAI_API_KEY="sk-..."

# Instalar librerías necesarias
pip install -r requirements.txt
```

---

## 🧪 Dataset de prueba incluido

El notebook contiene un entorno simulado de análisis ecológico:

- `df_main_1`: Observaciones individuales de aves (zona, especie, comportamiento, temperatura, predadores, etc.)
- `df_main_2`: Condiciones ecológicas por especie y zona (cobertura vegetal, ruido, densidad humana, etc.)

> Puedes reemplazar los datasets por otros con columnas comunes (`merge`) para adaptar el análisis a tu dominio.

---

## 💡 Posibles adaptaciones

- Análisis censales: personas, viviendas, infraestructura.
- Estudios de biodiversidad, clima, cambio ambiental.
- Datos de salud pública o educación por comuna y año.
- Reportes de auditoría entre inventario vs terreno.
- Evaluaciones cualitativas asistidas por IA.

---

## 👤 Autor

**Luis Pineda**  
Ciberseguridad y ciencia de datos  
📍 Chile — 2025  
🎓 [Portafolio GitHub](https://github.com/tu_usuario)

> _"Always learning. Always adapting."_ 🚀
