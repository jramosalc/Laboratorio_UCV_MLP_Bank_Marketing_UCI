# Laboratorio: Perceptrón Multicapa (MLP) - Bank Marketing

## Desarrollo de Preguntas de Análisis

*   **¿Qué diferencia existe entre un perceptrón simple y un perceptrón multicapa?**
    El perceptrón simple solo posee una capa de entrada y una neurona de salida, por lo que únicamente puede resolver problemas linealmente separables (como una compuerta AND/OR). El Perceptrón Multicapa (MLP) incluye capas ocultas y funciones de activación no lineales, permitiéndole aproximar funciones y patrones complejos (como la compuerta XOR o el comportamiento de clientes bancarios).

*   **¿Qué función cumplen las capas ocultas?**
    Actúan como extractores de características abstractas. Transforman el espacio de entrada original en representaciones intermedias cada vez más complejas, permitiendo que la red aprenda relaciones no lineales entre las variables del cliente y su decisión final.

*   **¿Por qué fue necesario convertir variables categóricas a variables numéricas?**
    Los algoritmos de redes neuronales se basan puramente en operaciones matemáticas (multiplicaciones de matrices y optimización mediante cálculo/gradientes). Un modelo no puede procesar un texto como "admin." o "married"; necesita representaciones numéricas binarias (como las que provee el One-Hot Encoding).

*   **¿Por qué se estandarizan las variables numéricas antes de entrenar una red neuronal?**
    Porque el MLP es muy sensible a la escala de los datos. Si una variable mide la edad (de 18 a 80) y otra el balance bancario (de 0 a 100,000), los gradientes se desestabilizarán, haciendo que el algoritmo de optimización (Adam) tarde mucho en converger o se quede estancado. La estandarización asegura que todas las variables aporten equitativamente al inicio.

*   **¿Qué significa `hidden_layer_sizes=(16, 8)`?**
    Significa que la red neuronal tiene dos capas ocultas: la primera capa oculta tiene 16 neuronas y la segunda capa oculta tiene 8 neuronas. (Esto es independiente de la capa de entrada y de la capa de salida).

*   **¿Qué métrica considera más importante para este caso: accuracy, precision, recall o F1-score? Justifique.**
    En este caso de negocio, la métrica clave suele ser el Recall (o F1-score debido al desbalance). El banco busca clasificar correctamente a los clientes que sí aceptarán el depósito para optimizar el esfuerzo del equipo telefónico. Si el Recall es bajo, el banco estará perdiendo clientes potenciales valiosos (falsos negativos). Sin embargo, si el costo por llamada telefónica es extremadamente alto, priorizaríamos la Precision para no molestar a clientes que dirán que no. Por ende, el F1-score equilibra óptimamente ambos escenarios.

*   **¿Qué riesgos existen si el banco usa este modelo para tomar decisiones comerciales reales?**
    *   **Sesgo de datos:** Si el histórico telefónico discriminó previamente a un sector demográfico, el modelo replicará y automatizará ese sesgo.
    *   **Falsos Negativos:** Ignorar a clientes que sí habrían aceptado el producto si hubiesen sido contactados.
    *   **Cambio de concepto (Data Drift):** Que las condiciones económicas cambien (e.g., una crisis o baja de tasas) y el comportamiento histórico ya no refleje el presente.

*   **¿Por qué un modelo más grande no siempre es mejor?**
    Una arquitectura con demasiadas capas y neuronas memoriza los datos de entrenamiento en lugar de aprender el patrón general. Esto provoca sobreajuste (overfitting): el modelo tendrá un rendimiento excelente con datos conocidos, pero fallará drásticamente con clientes nuevos en producción. Además, consume más recursos computacionales de forma innecesaria.

## Reto Experimental - Conclusión de Ingeniería
Si fuera el ingeniero responsable del banco, implementaría la arquitectura **(16, 8)**. Presenta el mejor balance en el **F1-score**, mantiene una alta estabilidad gracias al uso de *Early Stopping*, y cumple con el principio de parsimonia (simplicidad computacional), reduciendo el riesgo de sobreajuste en comparación con la estructura profunda de (32, 16, 8) sin comprometer la capacidad de priorizar de forma óptima las llamadas comerciales del banco.
