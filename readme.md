# Archivero Digital Inteligente

## Objetivo:

Este proyecto tiene como finalidad desarrollar un sistema inteligente de archivo documental. A través del análisis de datos y procesamiento de texto, el sistema será capaz de identificar automáticamente el tipo de documento cargado por el usuario, clasificarlo y organizarlo dentro de su repositorio correspondiente.

El usuario simplemente subirá un documento, y la aplicación se encargará de:

1. Leer su contenido mediante OCR.

2. Procesarlo con técnicas de NLP.

3. Clasificarlo usando un modelo de machine learning.

4. Guardarlo en su ubicación lógica según el Cuadro de Clasificación Archivística.

---

# Estructura Del Proyecto

Archivero/
│
├── app/
│   ├── api/                         # Endpoints HTTP
│   │   └── v1/
│   │       ├── endpoints/
│   │       │   ├── documents.py     # Subida, Clasificación, Listar Documentos
│   │       │   └── health.py        # El proyecto está corriendo?
│   │       └── router.py            # Incluye todos los endpoints
│   │
│   ├── core/                        # Configuración central (settings, logger)
│   │   ├── config.py                # Variables de entorno y configuración
│   │   └── logger.py
│   │
│   ├── models/                      # Modelos de base de datos
│   │   └── document.py              # Documento, tipo, metadatos, etc.
│   │
│   ├── schemas/                     # Esquemas Pydantic (entrada/salida)
│   │   └── document.py
│   │
│   ├── services/                    # Lógica de negocio / servicios
│   │   └── classifier_service.py    # Clasificación por IA
│   │
│   ├── utils/                       # OCR, procesamiento de texto, etc.
│   │   ├── ocr.py                   # pytesseract o Google Vision
│   │   ├── preprocess.py            # Limpieza y normalización de texto
│   │   └── vectorizer.py            # TF-IDF o embeddings
│   │
│   ├── repository/                 # Acceso a datos (ORM o manual SQL)
│   │   └── document_repo.py
│   │
│   ├── ml/                          # Carpeta para modelos ML entrenados
│   │   ├── model.pkl                # Modelo de clasificación entrenado
│   │   └── vectorizer.pkl           # Vectorizador TF-IDF u otro
│   │
│   ├── main.py                      # Punto de entrada FastAPI
│   └── deps.py                      # Dependencias para inyección (DB, etc.)
│
├── tests/                           # Pruebas unitarias y de integración
│   ├── test_documents.py
│   └── test_classifier.py
│
├── data/                            # Documentos de ejemplo / entrenamiento
│   └── sample_docs/
│
├── notebooks/                       # Experimentos en Jupyter
│   └── classifier_experiment.ipynb
│
├── .env                             # Configuración de entorno
├── requirements.txt                 # Dependencias
├── README.md
