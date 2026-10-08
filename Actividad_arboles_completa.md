# Actividad — Árboles de decisión y redes neuronales multicapa

Responda cada pregunta de manera clara y justificada.

En las preguntas de análisis no basta con indicar qué algoritmo utilizaría; deberá explicar por qué considera que esa alternativa es adecuada para el problema planteado.

## Parte I. Conceptos y definiciones

### Pregunta 1

**¿Qué es un árbol de decisión y cuál es su objetivo principal dentro de un problema de clasificación?**

Es un diagrama donde nosotros podemos observar claramente lo que está sucediendo, también conocido cómo caja blanca, es de gran utilidad ya que nos permite poder comprender mejor el flujo que adopta

### Pregunta 2

**Explique con sus propias palabras los siguientes elementos de un árbol de decisión:**

**Nodo raíz.** Es el primer elemento donde se origina el árbol, donde se parte o se plantea el problema

**Nodo interno.** Estos surgen a partir de otro nodo previo a este en el cual se toman las decisiones de acuerdo a lo más adecuado para nuestro problema

**Rama.** Son básicamente la línea que conecta lo nodos entre si, hacen referencia a los caminos posibles que se pueden llegar a tomar

**Hoja.** Son las puntas inferiores débil, los finales, muestra los resultados consecuencias a partir de las decisiones tomadas en los nodos previos

### Pregunta 3

**¿Qué es una red neuronal multicapa y qué función cumplen las siguientes capas?**

Es un modelo de inteligencia artificial el cual se basa en el funcionamiento real de las neuronas humanas, se compone de capas de neuronas conectadas entre si y trabajan en conjunto para aprender patrones, que puedan resolver problemas complejos, una característica clave de una neurona multicapa es que es capaz de resolver problemas no lineales

**Capa de entrada.**

Es donde se reciben los datos iniciales,para entrar a su procesamiento

**Capa oculta.**

Es básicamente donde se procesa toda la información, puede ser una o muchas

**Capa de salida.**

Es donde se arrojan los resultados finales después de ser procesado

### Pregunta 4

**¿Qué representan los pesos y los sesgos dentro de una red neuronal?**

Los pesos representan la prioridad en si que tienen los datos dentro dela red neuronal mientras que el sesg representa la facilidad para activar una neurona independientemente de los datos de entrada

**Explique también por qué sus valores cambian durante el entrenamiento.**

Porque de ahí depende lo que aprende en si la red neuronal, a partir de corregir los errores que haya tenido, al principio del entrenamiento estos valores son completamente aleatorios

### Pregunta 5

**¿Cuál es la principal diferencia entre la forma en que aprende un árbol de decisión y la forma en que aprende una red neuronal multicapa?**

El árbol de decisión aprende en una sola interacción en la cual crea su árbol completo de acuerdo a su necesidad, mientras que una red neuronal aprende a partir de iteraciones

**Explique qué elementos aprende cada modelo.**

Un árbol aprende variables importantes que sean las ejores para separar o clasificar el problema como lo es la entropia, mientras que la red neuronal aprende pesos y sesgos

## Parte II. Análisis y aplicación

### Pregunta 6

Una institución bancaria desea desarrollar un sistema que detecte posibles compras fraudulentas.

El sistema dispone de información como:

* Monto de la compra.
* Hora de la operación.
* Ciudad donde se realizó.
* Tipo de establecimiento.
* Número de compras realizadas durante el día.
* Historial de compras del cliente.

**Analice las ventajas y desventajas de utilizar un árbol de decisión y una red neuronal multicapa.**

**¿Cuál utilizaría y por qué?**

Utilizaría una red neuronal ya que se partiría principalmente de historial previo que se tenga del usuario y apartir de ahí analizar los montos, las ciudades donde se realizan, además de interpretar patrones relacionados a fraudes, se requiere una gran precisión ya que son temas muy importantes como los son los económicos

### Pregunta 7

Una escuela quiere detectar estudiantes que presentan riesgo de reprobar una materia.

Se conocen variables como:

* Asistencia.
* Calificaciones.
* Tareas entregadas.
* Participación.
* Número de materias reprobadas anteriormente.

Suponga que un árbol de decisión y una red neuronal obtienen prácticamente la misma precisión.

**¿Qué otros factores tomaría en cuenta para elegir uno de los dos modelos?**

Un aspecto que podría ser clave es la interpretabilidad de los resultados, si se tiene un historial corto es mejor el árbol, ya que las redes neuronales se comportan mejor a partir de muchos datos, utilizaria un árbol para tener una mejor comprensión de los resultados obtenidos

### Pregunta 8

Un hospital desarrolla un sistema para determinar qué pacientes necesitan atención prioritaria utilizando:

* Edad.
* Temperatura.
* Presión arterial.
* Frecuencia cardiaca.
* Síntomas.
* Antecedentes médicos.

Una red neuronal obtiene mejores resultados que un árbol de decisión, pero resulta más difícil explicar cómo obtuvo su respuesta.

**¿Considera que la mayor precisión es suficiente para elegir la red neuronal?**

En este caso considero que lo más adecuado es efectivamente la red neuronal ya que a final de cuentas los resultados deberán ser interpretados por un doctor, no son para que el paciente los interprete o entienda yen temas tan críticos como estos, se necesita una gran precisión de acuerdo a los patrones que se dan a partir de los síntomas que se presentan

Si no se toman las decisiones más precisas podría resultar en complicaciones para paciente que requerían atención antes que otros

### Pregunta 9

Una empresa de reparto quiere predecir si un pedido llegará tarde considerando:

* Distancia.
* Tráfico.
* Clima.
* Hora del día.
* Cantidad de pedidos.
* Experiencia del repartidor.

Para determinado pedido, el árbol de decisión indica:

**Llegará a tiempo**

mientras que la red neuronal indica:

**Probablemente llegará tarde**

**¿Cómo determinaría cuál de los dos modelos está realizando una mejor predicción?**

Probablemente la red neuronal está tomando más en cuenta aspectos por ejemplo la experiencia del repartidor en situaciones parecidas a la actual a partir de patrones que ha aprendido

**Explique qué información adicional debería analizar.**

Algo que se podría considerar es el vehículo que usar el repartidor o los métodos de pago también

### Pregunta 10

Una empresa desarrolla dos sistemas para decidir si una persona puede recibir un crédito.

El primer sistema utiliza un árbol de decisión y permite explicar claramente por qué una solicitud fue rechazada.

El segundo utiliza una red neuronal multicapa y obtiene mejores resultados de predicción, pero es más difícil explicar sus decisiones.

**Si usted fuera responsable del proyecto:**

**¿Cuál de los dos modelos utilizaría?**

Yo decidiría usar un árbol de decisión ya que al final el giro de la empresa de dar la facilidad a sus clientes por lo que debe ser importante dejarles claro lo que necesitan como requisito para ser parte de quien puede obtener el crédito

**¿Qué ventajas tendría su elección?**

Gran facilidad para general le confianza a los clientes y atraerlos a obtener su credito

**¿Qué riesgos tendría?**

Llegar a tener inconsistencias o falta de precisión a la hora de elegir a los mejores candidatos para recibir el crédito

**¿Consideraría posible utilizar ambos modelos dentro del mismo sistema?**

**Justifique ampliamente su respuesta.**

Para mí si es posible utilizar ambos ya que con la red neurona la empresa puede asegurar completamente analizar a quien poder hacer el préstamos y a quien no con datos fríos económicamente, mientras que el árbol nos ayuda para realizar el informe a los usuarios de quienes podrían ser candidatos y quien no

### A partir de los ejercicios anteriores, explique brevemente la siguiente afirmación:

**No existe un algoritmo de Inteligencia Artificial que sea el mejor para todos los problemas.**

Estoy de acuerdo con la afirmación ya que cada método se adapta a diferentes contextos o enfoques en el que se vaya a realizar, puede que se requiera una gran precisión pero si los resultados no se pueden interpretar entonces de debería considera si se podrían sacrificar algunos conceptos compensando con los que importan en el contexto en el que se aplique, si hay gran cantidad de información se podría indicar hacia alguna opción,por la complejidad entre otros

