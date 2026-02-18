# 🎙️ Speaker Recognition: Biometric Voice Classification

![Python Version](https://img.shields.io/badge/Python-3.8%2B-blue)
![Librosa](https://img.shields.io/badge/Librosa-Audio_Analysis-orange)
![Status](https://img.shields.io/badge/Status-Development-yellow)

Este repositorio contiene la implementación de modelos de clasificación supervisada para el **Reconocimiento de Locutores (Speaker Recognition)**. El sistema analiza señales de audio para extraer huellas biométricas de voz y determinar la identidad de la persona que habla.


## 📖 Descripción del Proyecto

El objetivo principal es autenticar o identificar usuarios basándose únicamente en su voz. A diferencia del reconocimiento de voz (que busca entender *qué* se dice), este proyecto se enfoca en *quién* lo dice.

El sistema procesa archivos de audio raw, transforma las ondas sonoras en representaciones matemáticas complejas y entrena un clasificador para distinguir entre distintos individuos etiquetados.

## ⚙️ Metodología y Pipeline

El flujo de trabajo del proyecto se divide en las siguientes etapas:

1.  **Ingesta de Audio:** Carga de archivos `.wav` (o `.mp3`).
2.  **Preprocesamiento:** Limpieza de ruido, normalización de volumen y eliminación de silencios.
3.  **Extracción de Características:** Conversión del audio en coeficientes numéricos.
4.  **Generación del DataFrame:** Creación de una estructura tabular donde cada fila es una muestra de audio y las columnas son sus features + la etiqueta del individuo.
5.  **Entrenamiento:** Uso de algoritmos de clasificación [SVM / Random Forest / MLP / GMM].

## 📊 Ingeniería de Características

Para capturar la "huella" vocal única de cada individuo, utilizamos principalmente **MFCCs (Mel-Frequency Cepstral Coefficients)**.


Se extraen las siguientes características del dominio de la frecuencia y el tiempo:
* **MFCCs:** (Ej. 13-40 coeficientes) que representan la forma del tracto vocal.
* **Delta & Delta-Delta:** Para capturar la dinámica temporal del cambio en la voz.
* **[Opcional: Chroma, Zero Crossing Rate, Spectral Roll-off]**.

Estos datos se consolidan en un **Pandas DataFrame** final listo para el entrenamiento.

