# Clasificación de Tumores de Cáncer de Mama con Deep Learning e IA Explicable 🔬

Este repositorio contiene el flujo completo de trabajo para la clasificación automática e interpretable de los cuatro tipos de tumores malignos presentes en el dataset **BreakHis**. El proyecto integra técnicas de ingeniería de datos, aprendizaje por transferencia e interpretabilidad clínica.
Link a la base de datos BreakHis = https://drive.google.com/file/d/1ZY3l4rvmLtyxLsXVvl0NiiIxSTjlBvVi/view?usp=drive_link

## 📑 Resumen del Proyecto
El diagnóstico definitivo del cáncer de mama requiere un análisis histopatológico complejo y especializado. Este sistema busca servir como herramienta de apoyo, proporcionando no solo una clasificación precisa, sino también una explicación visual de las regiones del tejido que fundamentan la decisión del modelo              .

## 📊 El Dataset: BreakHis
Se utiliza la base de datos *Breast Cancer Histopathological Image Classification*              .
* **Alcance**: 5,429 imágenes microscópicas de tumores malignos              .
* **Clases**: 
  * Carcinoma Ductal (DC)               
  * Carcinoma Lobulillar (LC)               
  * Carcinoma Mucinoso (MC)               
  * Carcinoma Papilar (PC)               
* **Magnificaciones**: Imágenes capturadas a 40X, 100X, 200X y 400X.

## 🛠️ Pipeline del Proyecto

### 1. Ingeniería del Dato
*  **Limpieza y Estructuración**: Reorganización del dataset original para un flujo de trabajo optimizado en Google Colab.
*  **División de Datos**: Train (70%), Validation (15%) y Test (15%).
*  **Data Augmentation (Offline)**: Aplicación de rotaciones ($15^{\circ}$), desplazamientos, zoom y flips para balancear las clases minoritarias hasta ~2,000 imágenes cada una.
*  **Normalización**: Reescalado de píxeles al rango [0, 1] y redimensionamiento a $224 \times 224$.

### 2. Modelado (Transfer Learning)
 Se han evaluado y comparado arquitecturas pre-entrenadas en ImageNet:
*  **DenseNet121** 
*  **ResNet50** 
*  **EfficientNetB0** 

### 3. Explicabilidad (XAI)
 Uso de **Grad-CAM++** para generar mapas de calor sobre las muestras histológicas, permitiendo identificar las estructuras celulares y arquitecturas de tejido que el modelo considera relevantes para el diagnóstico.

## 💻 Tecnologías Utilizadas
* **Lenguaje**: Python 3.x
* **Frameworks**: TensorFlow, Keras
* **Bibliotecas**: Scikit-learn, Numpy, Matplotlib, Seaborn
* **Entorno**: Google Colab / Google Drive

## 📊 Estructura de Datos e Ingeniería

 Para optimizar el entrenamiento y asegurar la variabilidad morfológica, se transformó la jerarquía original del dataset en una estructura simplificada.  Se eliminó la separación por niveles de zoom para mezclar todos los factores de magnificación (40X, 100X, 200X y 400X) dentro de cada categoría tumoral.

### Árbol de Directorios
```text
dataset/
└── Malignos/                        # Carpeta raíz simplificada 
    ├── ductal_carcinoma/            # Imágenes DC (Ductal Carcinoma) 
    │   ├── SOB_M_DC-14-10926-100-001.png
    │   └── ...
    ├── lobular_carcinoma/           # Imágenes LC (Lobular Carcinoma)
    │   ├── SOB_M_LC-14-12204-100-015.png
    │   └── ...
    ├── mucinous_carcinoma/          # Imágenes MC (Mucinous Carcinoma) 
    │   ├── SOB_M_MC-14-10147-100-001.png
    │   └── ...
    └── papillary_carcinoma/         # Imágenes PC (Papillary Carcinoma) 
        ├── SOB_M_PC-14-12465-100-001.png
        └── ...
```
---
**Autor**: Felipe Galarza
**Institución**: Universidad Francisco de Vitoria (UFV Madrid)
**Curso**: 2025-2026
