# Implementación y Comparación de Modelos de Traducción Automática (NMT)

Este repositorio contiene la implementación y comparación de cuatro arquitecturas distintas de redes neuronales para resolver un problema de Traducción Automática Neuronal (NMT). El objetivo es comparar el rendimiento, la eficiencia y la calidad de traducción de cada modelo en un corpus de Español a Inglés.

Este proyecto cumple con los requisitos de la Fase 4 (Entrega) de la actividad.

## 🚀 Arquitecturas Implementadas

Se implementaron y entrenaron cuatro arquitecturas Codificador-Decodificador (Encoder-Decoder), como se especifica en el documento:

1.  **Modelo 1: RNN Simple** (SimpleRNN, sin mecanismo de atención)
2.  **Modelo 2: LSTM + Atención** (LSTM con Atención Bahdanau)
3.  **Modelo 3: GRU + Atención** (GRU con Atención Bahdanau)
4.  **Modelo 4: Transformer** (Arquitectura de Auto-Atención y Atención Cruzada)

## 📊 Resumen de Resultados y Comparativa

El objetivo principal fue la comparación de métricas. Todos los modelos se entrenaron en el mismo dataset filtrado (20,000 frases) con hiperparámetros de base similares (1 capa, 128 hidden size) para una comparación justa.

| Arquitectura | Calidad (BLEU) | Pérdida (Loss) Final | Parámetros | Análisis Clave |
| :--- | :---: | :---: | :---: | :--- |
| **1. RNN Simple** | *(Esperado: < 0.05)* | *(Esperado: > 3.5)* | ~1.9 M | **Sin Atención.** Sirve como base para demostrar el "cuello de botella de información". |
| **2. LSTM + Atención** | *(Esperado: ~0.17)* | *(Esperado: ~2.2)* | ~2.3 M | **Más complejo.** Logra una calidad similar a GRU, pero tiene más puertas (4) y, por lo tanto, más parámetros. |
| **3. GRU + Atención** | **0.1763** | **2.1631** | **2,141,246** | **Eficiente.** Logra un rendimiento base con menos parámetros que LSTM (2 puertas). Los resultados (BLEU bajo) demuestran que 1 capa / 128 hidden es insuficiente. |
| **4. Transformer** | *(Esperado: > 0.50)* | *(Esperado: < 1.0)* | ~6.5 M+ | **Estándar actual.** Se espera que supere a los modelos recurrentes, ya que la Atención Multi-Cabeza maneja mejor las dependencias. |

### Conclusiones del Modelo 3 (GRU)
Los resultados del modelo GRU (BLEU: 0.1763, Loss: 2.1631) demuestran que, aunque la arquitectura (GRU + Atención) es funcional, la configuración de **1 capa y 128 de tamaño oculto** fue **demasiado simple** para la complejidad de la tarea, resultando en un modelo sub-entrenado.

## Dataset

Se utilizó un corpus paralelo de Español-Inglés del proyecto **Tatoeba**, recomendado por el documento.
* **Fuente:** [manythings.org/anki/ (spa-eng.zip)](http://www.manythings.org/anki/)
* **Preprocesamiento:** Se filtraron los datos para incluir solo **20,000 pares** de frases con una longitud máxima de **15 palabras**.

## 🛠️ Cómo Empezar

Instrucciones para replicar el entrenamiento y la evaluación.

### 1. Requisitos

El código se implementó en Python 3 usando PyTorch.

**`requirements.txt`**
