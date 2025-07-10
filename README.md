# Archivero Digital Inteligente

## Objetivo:

Este proyecto tiene como finalidad desarrollar un sistema inteligente de archivo documental. A través del análisis de datos y procesamiento de texto, el sistema será capaz de identificar automáticamente el tipo de documento cargado por el usuario, clasificarlo y organizarlo dentro de su repositorio correspondiente.

El usuario simplemente subirá un documento, y la aplicación se encargará de:

1. Leer su contenido mediante OCR.

2. Procesarlo con técnicas de NLP.

3. Clasificarlo usando un modelo de machine learning.

4. Guardarlo en su ubicación lógica según el Cuadro de Clasificación Archivística.

---

# Cómo instalarlo

1. Clona el repositorio

```
git clone https://github.com/GuillermoSM33/Practique_FastApi.git
cd FASTAPI_PROYECTO

```

2. Instala las dependencias

```
pip install -r requirements.txt
```

---

# Entorno Virtual

Se recomienda usar el entorno virtual para aislar las dependencias del proyecto

```
# Crear entorno virtual
python -m venv .venv

# Activarlo en Windows
.\.venv\Scripts\activate

# Activarlo en Unix/Mac
source .venv/bin/activate
```

---
# Docker

También puedes ejecutar la aplicación usando Docker (basado en Ubuntu):

1. Construye la imagen Docker desde la raíz del proyecto:

   ```bash
   docker build -t practique_fastapi .  #el punto es importante se debe de copiar
   ```

2. Ejecuta el contenedor exponiendo el puerto 8000:
   ```bash
   docker run -p 8000:8000 practique_fastapi
   ```

Esto levantará el servidor FastAPI en `http://localhost:8000` dentro de un contenedor Ubuntu con todas las dependencias necesarias (incluyendo Tesseract para OCR).

Si necesitas montar archivos locales o usar variables de entorno, puedes agregar opciones a los comandos de Docker según tu caso de uso.

---

# Estructura del Proyecto

```
Archivero/
│
├── app/
│   ├── api/                         # Endpoints HTTP
│   │   └── v1/
│   │       ├── endpoints/
│   │       │   ├── documents.py     # Subida, clasificación y consulta de documentos
│   │       │   └── health.py        # Verificación del estado del sistema (health check)
│   │       └── router.py            # Enrutador principal de la API
│   │
│   ├── core/                        # Configuración central y utilidades base
│   │   ├── config.py                # Variables de entorno y parámetros globales
│   │   └── logger.py                # Configuración de logs del sistema
│   │
│   ├── models/                      # Modelos de base de datos (ORM)
│   │   └── document.py              # Representación del documento y sus metadatos
│   │
│   ├── schemas/                     # Esquemas Pydantic para validación de datos
│   │   └── document.py              # Esquemas de entrada/salida de documentos
│   │
│   ├── services/                    # Lógica de negocio
│   │   └── classifier_service.py    # Clasificación de documentos mediante IA
│   │
│   ├── utils/                       # Utilidades auxiliares
│   │   ├── ocr.py                   # Extracción de texto (Tesseract, Vision API, etc.)
│   │   ├── preprocess.py            # Limpieza y normalización del texto
│   │   └── vectorizer.py            # Vectorización del texto (TF-IDF, BERT, etc.)
│   │
│   ├── repository/                  # Acceso a la base de datos
│   │   └── document_repo.py         # Consultas y operaciones sobre documentos
│   │
│   ├── ml/                          # Modelos de machine learning entrenados
│   │   ├── model.pkl                # Modelo de clasificación
│   │   └── vectorizer.pkl           # Vectorizador usado en el entrenamiento
│   │
│   ├── main.py                      # Punto de entrada de la aplicación FastAPI
│   └── deps.py                      # Dependencias inyectables (DB, servicios, etc.)
│
├── tests/                           # Pruebas unitarias e integración
│   ├── test_documents.py
│   └── test_classifier.py
│
├── data/                            # Datos de entrenamiento y ejemplos
│   └── sample_docs/
│
├── notebooks/                       # Experimentos, prototipos y análisis exploratorio
│   └── classifier_experiment.ipynb
│
├── .env                             # Variables de entorno (local)
├── requirements.txt                 # Lista de dependencias del proyecto
├── README.md                        # Descripción general del proyecto
```
