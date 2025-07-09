# Archivero Digital Inteligente

## Objetivo:
Este proyecto tiene como finalidad desarrollar un sistema inteligente de archivo documental. A través del análisis de datos y procesamiento de texto, el sistema será capaz de identificar automáticamente el tipo de documento cargado por el usuario, clasificarlo y organizarlo dentro de su repositorio correspondiente.

El usuario simplemente subirá un documento, y la aplicación se encargará de:

1. Leer su contenido mediante OCR.

2. Procesarlo con técnicas de NLP.

3. Clasificarlo usando un modelo de machine learning.

4. Guardarlo en su ubicación lógica según el Cuadro de Clasificación Archivística.

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
