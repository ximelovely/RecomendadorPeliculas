# ✦ CineVibeAI

<div align="center">

![Python](https://img.shields.io/badge/Python-3.10+-c9a96e?style=flat-square&logo=python&logoColor=white)
![Hugging Face](https://img.shields.io/badge/Hugging%20Face-Transformers-c9a96e?style=flat-square&logo=huggingface&logoColor=white)
![Gradio](https://img.shields.io/badge/Interfaz-Gradio-c9a96e?style=flat-square)
![Google Colab](https://img.shields.io/badge/Entorno-Google%20Colab-c9a96e?style=flat-square&logo=googlecolab&logoColor=white)

*Recomendador inteligente de películas basado en un modelo compacto de lenguaje*

**Proyecto Integrador de Aprendizaje — Sistemas Adaptativos**  
FIME, UANL · 2025

</div>

---

## 📖 Descripción

CineVibeAI es un modelo compacto de lenguaje especializado en recomendaciones cinematográficas. A partir de una descripción libre del usuario —como su estado de ánimo, género favorito o tipo de experiencia que busca— el modelo genera una recomendación personalizada con título, descripción y contexto de la película.

El proyecto fue desarrollado aplicando la técnica de **fine-tuning** sobre un modelo base preentrenado en español, usando un dataset construido manualmente con pares de consulta y recomendación.

---

## 🗂️ Estructura del repositorio

```
RecomendadorPeliculas/
│
├── Equipo_Newton_PIA_4.ipynb    # Notebook principal (entrenamiento + interfaz)
├── Películas base.xlsx          # Lista de películas base usadas para el dataset
├── prompts.jsonl                # Dataset de entrenamiento (pares prompt/completion)
└── README.md                    # Este archivo
```

---

## ⚙️ Tecnologías utilizadas

| Herramienta | Función |
|---|---|
| `transformers` (Hugging Face) | Fine-tuning y generación de texto |
| `datasets` (Hugging Face) | Carga y procesamiento del dataset |
| `datificate/gpt2-small-spanish` | Modelo base preentrenado en español |
| `Gradio` | Interfaz de usuario interactiva |
| Google Colab | Entorno de ejecución en la nube (GPU gratuita) |

---

## 🚀 Cómo ejecutar el proyecto

**1. Abre el notebook en Google Colab**

[![Abrir en Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/)

**2. Sube el archivo `prompts.jsonl`** cuando la celda correspondiente lo solicite.

**3. Ejecuta las celdas en orden:**

```
Celda 1 → Instalar librerías
Celda 2 → Subir dataset
Celda 3 → Cargar dataset
Celda 4 → Cargar modelo base
Celda 5 → Tokenizar datos
Celda 6 → Entrenar modelo
Celda 7 → Lanzar interfaz Gradio
```

**4.** Al correr la última celda, Gradio generará un enlace público `https://xxxx.gradio.live` — ábrelo en cualquier navegador para usar el recomendador.

---

## 🎬 Uso

Una vez activa la interfaz, escribe en lenguaje natural lo que buscas:

```
"Quiero algo de terror psicológico que no sea tan gore"
"Algo romántico pero no cursi"
"Una película para ver en familia"
"Ciencia ficción con buena historia"
```

El modelo generará una recomendación basada en los patrones aprendidos durante el entrenamiento.

---

## 📊 Dataset

El dataset (`prompts.jsonl`) fue construido manualmente en formato JSONL, con pares de entrada y salida que cubren ocho categorías de consulta:

- Terror psicológico
- Romance
- Comedia
- Acción y adrenalina
- Drama / Para llorar
- Ciencia ficción
- Familiar
- Suspenso

Cada entrada sigue el formato:
```json
{"prompt": "Quiero algo de terror psicológico", "completion": "Te recomiendo Hereditary..."}
```

---

## ⚠️ Errores encontrados

Durante el desarrollo se presentaron los siguientes obstáculos:

**Texto incoherente con palabras inventadas** — El modelo base inicial (`distilgpt2`) fue entrenado en inglés, generando salidas sin sentido en español. Se resolvió migrando a `datificate/gpt2-small-spanish`.

**Repetición excesiva de frases** — El modelo ciclaba sobre las mismas oraciones. Se mitigó con el parámetro `repetition_penalty=1.3`.

**Bloqueo CORS en el frontend local** — Al abrir el HTML desde el explorador de archivos (`file://`), el navegador bloqueaba las peticiones. Se resolvió migrando la interfaz directamente a Gradio dentro de Colab.

---

## 🔮 Mejoras futuras

- Ampliar el dataset a 200+ ejemplos para mejorar coherencia y variedad
- Migrar a un modelo base más robusto usando técnicas de fine-tuning eficiente (LoRA / PEFT)
- Agregar sistema de filtrado para evitar recomendaciones de películas inexistentes
- Incorporar imágenes de portadas e historial de recomendaciones en la interfaz
- Implementar retroalimentación del usuario para entrenamiento continuo y adaptativo

---

## 👩‍💻 Equipo

**Equipo Newton** · Grupo 002

| Nombre | GitHub |
|---|---|
| Ximena Cruz | [@ximelovely](https://github.com/ximelovely) |
| Juan Emmanuel Del Angel Arrieta | [@juanedaa05](https://github.com/juanedaa05) |
| Jordan Emanuel Ruedas Vazquez | [@jordyruedas-a](https://github.com/jordyruedas-a) |
| Greco Iván Gaytán Aldana | [@grecogaytan0-spec](https://github.com/grecogaytan0-spec) |

---

<div align="center">

*FIME · UANL · Sistemas Adaptativos · 202*

</div>