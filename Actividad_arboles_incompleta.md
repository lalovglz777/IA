# Actividad — Árboles de decisión y redes neuronales multicapa

Responda cada pregunta de manera clara y justificada.

En las preguntas de análisis no basta con indicar qué algoritmo utilizaría; deberá explicar por qué considera que esa alternativa es adecuada para el problema planteado.

## Parte I. Conceptos y definiciones

### Pregunta 1

**¿Qué es un árbol de decisión y cuál es su objetivo principal dentro de un problema de clasificación?**

Es un diagrama donde nosotros podemos observar claramente lo que está sucediendo, también conocido como caja blanca. Es de gran utilidad ya que nos permite comprender mejor el flujo que adopta.

### Pregunta 2

**Explique con sus propias palabras los siguientes elementos de un árbol de decisión:**

- **Nodo raíz:** Es el primer elemento donde se origina el árbol, donde se parte o se plantea el problema.

- **Nodo interno:** Estos surgen a partir de otro nodo previo, en el cual se toman las decisiones de acuerdo a lo más adecuado para nuestro problema.

- **Rama:** Son básicamente las líneas que conectan los nodos entre sí. Hacen referencia a los caminos posibles que se pueden llegar a tomar.

- **Hoja:** Son las puntas inferiores, los finales. Muestran los resultados o consecuencias a partir de las decisiones tomadas en los nodos previos.

### Pregunta 3

**¿Qué es una red neuronal multicapa y qué función cumplen las siguientes capas?**

Es un modelo de inteligencia artificial el cual se basa en el funcionamiento real de las neuronas humanas. Se compone de capas de neuronas conectadas entre sí y trabajan en conjunto para aprender patrones que puedan resolver problemas complejos. Una característica clave de una red neuronal multicapa es que es capaz de resolver problemas no lineales.

- **Capa de entrada:** Es donde se reciben los datos iniciales para entrar a su procesamiento.

- **Capa oculta:** Es básicamente donde se procesa toda la información. Puede ser una o muchas.

- **Capa de salida:** Es donde se arrojan los resultados finales después de ser procesados.

### Pregunta 4

**¿Qué representan los pesos y los sesgos dentro de una red neuronal?**

Los pesos representan la prioridad que tienen los datos dentro de la red neuronal, mientras que el sesgo representa la facilidad para activar una neurona independientemente de los datos de entrada.

**Explique también por qué sus valores cambian durante el entrenamiento.**

Porque de ahí depende lo que aprende en sí la red neuronal, a partir de corregir los errores que haya tenido. Al principio del entrenamiento estos valores son completamente aleatorios.

### Pregunta 5

**¿Cuál es la principal diferencia entre la forma en que aprende un árbol de decisión y la forma en que aprende una red neuronal multicapa?**

El árbol de decisión aprende en una sola interacción, en la cual crea su árbol completo de acuerdo a su necesidad, mientras que una red neuronal aprende a partir de iteraciones.

**Explique qué elementos aprende cada modelo.**

Un árbol aprende variables importantes que sean las mejores para separar o clasificar el problema, como lo es la entropía, mientras que la red neuronal aprende pesos y sesgos.

## Parte II. Análisis y aplicación

### Pregunta 6

Una institución bancaria desea desarrollar un sistema que detecte posibles compras fraudulentas.

El sistema dispone de información como:

- Monto de la compra.
- Hora de la operación.
- Ciudad donde se realizó.
- Tipo de establecimiento.
- Número de compras realizadas durante el día.
- Historial de compras del cliente.

**Analice las ventajas y desventajas de utilizar un árbol de decisión y una red neuronal multicapa.**

**¿Cuál utilizaría y por qué?**

### Pregunta 7

Una escuela quiere detectar estudiantes que presentan riesgo de reprobar una materia.

Se conocen variables como:

- Asistencia.
- Calificaciones.
- Tareas entregadas.
- Participación.
- Número de materias reprobadas anteriormente.

Suponga que un árbol de decisión y una red neuronal obtienen prácticamente la misma precisión.

**¿Qué otros factores tomaría en cuenta para elegir uno de los dos modelos?**

**Justifique su respuesta.**

### Pregunta 8

Un hospital desarrolla un sistema para determinar qué pacientes necesitan atención prioritaria utilizando:

- Edad.
- Temperatura.
- Presión arterial.
- Frecuencia cardiaca.
- Síntomas.
- Antecedentes médicos.

Una red neuronal obtiene mejores resultados que un árbol de decisión, pero resulta más difícil explicar cómo obtuvo su respuesta.

**¿Considera que la mayor precisión es suficiente para elegir la red neuronal?**

**Analice las consecuencias que podría tener esta decisión.**

### Pregunta 9

Una empresa de reparto quiere predecir si un pedido llegará tarde considerando:

- Distancia.
- Tráfico.
- Clima.
- Hora del día.
- Cantidad de pedidos.
- Experiencia del repartidor.

Para determinado pedido, el árbol de decisión indica:

> Llegará a tiempo

Mientras que la red neuronal indica:

> Probablemente llegará tarde

**¿Cómo determinaría cuál de los dos modelos está realizando una mejor predicción?**

**Explique qué información adicional debería analizar.**

### Pregunta 10

Una empresa desarrolla dos sistemas para decidir si una persona puede recibir un crédito.

El primer sistema utiliza un árbol de decisión y permite explicar claramente por qué una solicitud fue rechazada.

El segundo utiliza una red neuronal multicapa y obtiene mejores resultados de predicción, pero es más difícil explicar sus decisiones.

Si usted fuera responsable del proyecto:

- **¿Cuál de los dos modelos utilizaría?**
- **¿Qué ventajas tendría su elección?**
- **¿Qué riesgos tendría?**
- **¿Consideraría posible utilizar ambos modelos dentro del mismo sistema?**
- **Justifique ampliamente su respuesta.**

## Conclusión

A partir de los ejercicios anteriores, explique brevemente la siguiente afirmación:

> No existe un algoritmo de Inteligencia Artificial que sea el mejor para todos los problemas.

Relacione su respuesta con los conceptos de:

- Precisión.
- Interpretabilidad.
- Cantidad de datos.
- Complejidad del problema.
- Consecuencias de una decisión incorrecta.
