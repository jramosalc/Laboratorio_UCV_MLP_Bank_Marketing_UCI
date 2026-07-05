# Laboratorio_UCV_MLP_Bank_Marketing_UCI

# Laboratorio: Perceptrón Multicapa (MLP) - Bank Marketing

## 1. Respuestas a Preguntas de Análisis
*   **¿Qué diferencia existe entre un perceptrón simple y un perceptrón multicapa?**  
    El perceptrón simple solo puede resolver problemas linealmente separables (separados por una línea recta). El perceptrón multicapa (MLP) incluye capas ocultas y funciones de activación no lineales, lo que le permite aprender patrones complejos y fronteras de decisión no lineales.
*   **¿Qué función cumplen las capas ocultas?**  
    Actúan como extractores automáticos de características intermedias, combinando las variables de entrada para encontrar interacciones complejas antes de dar una predicción final.
*   **¿Por qué fue necesario convertir variables categóricas a variables numéricas?**  
    Las redes neuronales realizan operaciones matemáticas puras (multiplicaciones de matrices y sumas de pesos). No pueden procesar texto de forma directa.
*   **¿Por qué se estandarizan las variables numéricas antes de entrenar una red neuronal?**  
    Para asegurar que todas las variables tengan la misma escala (media 0 y varianza 1). Si no se hace, las variables con números más grandes (ej. el saldo bancario) dominarán los gradientes, ralentizando o impidiendo la convergencia del entrenamiento.
*   **¿Qué significa `hidden_layer_sizes=(16, 8)`?**  
    Significa que la red neuronal tiene dos capas ocultas: la primera capa tiene 16 neuronas artificiales y la segunda tiene 8 neuronas.
*   **¿Qué métrica considera más importante para este caso: accuracy, precision, recall o F1-score? Justifique.**  
    El **F1-score** o el **Recall de la clase 'yes'**. El dataset está fuertemente desbalanceado (la gran mayoría dice "no"). Un *Accuracy* alto sería engañoso. Al banco le interesa el *Recall* para minimizar los falsos negativos, es decir, evitar perder clientes que sí querían el depósito a plazo pero que el modelo clasificó erróneamente como no interesados.
*   **¿Qué riesgos existen si el banco usa este modelo para tomar decisiones comerciales reales?**  
    Existe el riesgo de sesgo en los datos históricos (por ejemplo, si el banco llamó antes a un solo tipo de perfil), hostigamiento a clientes debido a falsos positivos, o dejar de contactar a clientes potenciales rentables si el modelo falla.
*   **¿Por qué un modelo más grande no siempre es mejor?**  
    Porque un exceso de capas y neuronas provoca *overfitting* (sobreajuste), donde el modelo memoriza los datos de entrenamiento pero pierde su capacidad de generalizar con clientes nuevos en el mundo real.

## 2. Reto Experimental - Conclusión de Ingeniería
Si fuera el ingeniero responsable del banco, implementaría la arquitectura **(16, 8)**. Presenta el mejor balance en el **F1-score**, mantiene una alta estabilidad gracias al uso de *Early Stopping*, y cumple con el principio de parsimonia (simplicidad computacional), reduciendo el riesgo de sobreajuste en comparación con la estructura profunda de (32, 16, 8) sin comprometer la capacidad de priorizar de forma óptima las llamadas comerciales del banco.
