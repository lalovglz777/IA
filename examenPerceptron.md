           ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
            EXAMEN TEÓRICO — PERCEPTRÓN, MLP Y CNN (GRUPO A)

                            Eduardo Alcaraz
           ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━


1 Datos del alumno
══════════════════

  ━━━━━━━━━━━
   Nombre  Eduardo Vargas Gonzalez
   Grupo   A 
   Fecha   03 de noviembre
  ━━━━━━━━━━━


2 Pregunta 1 — Idea del perceptrón
══════════════════════════════════

  1. Explica qué recibe un perceptrón, qué hace con los pesos y el bias,
     y qué produce.
  2. ¿Qué quiere decir que dos clases sean *linealmente separables*?
  3. Señala *una* limitación fuerte del perceptrón de una sola capa.


2.0.1 Respuesta
╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌

  ┌────
1. el perceptron es una neurona artificial que recibe entradas con valores, los persos y el bias lo utiliza para decidir que salida es la que va a generar, los pesos determinan la importancia de cada entrada, y el bias se usa para ajustar es resultado ede la decision 
2. quiere decir que es posible separar dos clases de datos mediante una linea recta, es decir no se mezclan los dato
3. no puede resolver problemas que no sean linealmente separables
  └────


3 Pregunta 2 — Por qué aparece el MLP
═════════════════════════════════════

  1. ¿En qué sentido un MLP es “más de una capa de neuronas”?
  2. ¿Para qué sirve la capa oculta ?
  3. Si quitas todas las activaciones no lineales, ¿qué tipo de
     comportamiento te queda y por qué importa?


3.0.1 Respuesta
╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌

  ┌────
1. tiene mas de una capa de neuronas cuando tiene una capa de entrada ademas de una o mas capas ocultas que se encargan de procesar la informacion y la capa de salida
2. se encarga de procesatr la informacion, ya sea encontrar caracteristicas, patrones, relaciones, etc para asi poder aprender y generar una respuesta
3. pierde la capacidad de resolver problemas no lineales, entonces la red se comporta como una sola lineal
  └────


4 Pregunta 3 — XOR como lección histórica
═════════════════════════════════════════

  1. ¿Qué enseña el ejemplo XOR sobre el perceptrón simple?
  2. ¿Qué cambia al pasar a una red con capas ocultas y no linealidad?
  3. ¿Eso significa que el perceptrón nunca sirve en problemas reales?
     Argumenta.


4.0.1 Respuesta
╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌

  ┌────
1. que un perceptron simple no puede resolver todo con respect a clasificacion, enfocado a los que no son linealmente separables
2. se pueden cominar diferentes operaciones para aprender patrones complejos y resolver problemas
3. no precisamente hay problemas de la vida real que si son linealmente separables, ademas es una base importante para el funcionamiento de las redes neuronales
  └────


5 Pregunta 4 — Cómo “aprende” la red
════════════════════════════════════

  1. Describe con palabras el ciclo: predicción → medir error → ajustar
     pesos.
  2. ¿Qué controla el *learning rate* (tasa de aprendizaje) a nivel
     conceptual?
  3. Diferencia *subajuste* y *sobreajuste* con un ejemplo escolar
     breve.


5.0.1 Respuesta
╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌

  ┌────
1. lo que hace basicamente es recibir todos los datos para asi poder realizer una prediccion, eso quiere decir que realizer una comparacion del resultado obtenido con la respuesta correcta para asi calcular el error para poder realizer el ajuste de sus pesos mediante su proceso de aprendizaje para redcuir el error
2. hace referencia a que tan facil o complicado es para que la red aprenda, esto es base a los pesos, si son demasiado grande puede no encontrar una solucion precisa, si son muy pequenos podria tardar demasiado en aprender
3. el subajuste se podria interpretar a  cuando un alumno no estudia y por ende no parende los temas mientras que el sobreasjuste ocurre cuando apende demasiado de memoria ejemplo de practica pero no sabe como resolver preguntas nuevas que no habia visto
  └────


6 Pregunta 5 — Salidas: sigmoide y softmax
══════════════════════════════════════════

  1. ¿Cuándo usarías sigmoide y cuándo softmax?
  2. ¿Qué significa el vector que sale de un softmax en un problema de
     varias clases?
  3. Pon un ejemplo del curso (juego, riesgo, imágenes, etc.) y di qué
     salida encajaría.


6.0.1 Respuesta
╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌

  ┌────
1. si el problema tiene dos posibles resultados usaria sigmoide por ejemplo determiner si cierto objeto se encuentra en una imagen mientras que SoftMax es para cuando temenos varias clases posibles y se debe elegir solo una como identificar determinado objetos en una iimagen
2. demuestra la probabilidad estimada de pertenecer a una clase en si, cada probabilidad suma 1 y por ende la clase con valor mas alto representa la prediccion
3. por ejemplo la clasificacion de los deportes, se usa SoftMax porque hay varias posiblidades y debe identificar a cual pertenece de acuerdo a las probabilidades que genere, el que tenga valor mas alto es el que determina como correcto
  └────


7 Pregunta 6 — Motivación de la CNN
═══════════════════════════════════

  1. ¿Qué inconveniente conceptual tiene aplastar una imagen y meterla a
     un MLP denso?
  2. ¿Qué aporta la idea de *filtro local* y *pesos compartidos*?
  3. Menciona *dos* dominios (además de fotos cotidianas) donde una CNN
     tiene sentido.


7.0.1 Respuesta
╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌

  ┌────

  └────


8 Pregunta 7 — Piezas de una CNN
════════════════════════════════

  Explica el *para qué* de:
  1. Convolución
  2. Pooling
  3. Flatten + Dense al final
  4. Dropout durante el entrenamiento


8.0.1 Respuesta
╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌

  ┌────

  └────


9 Pregunta 8 — Capas bajas vs capas altas
═════════════════════════════════════════

  1. ¿Qué suelen captar las primeras capas de una CNN frente a las más
     profundas?
  2. Usa una analogía (lupas, detectores, “de simple a complejo”).
  3. ¿Por qué “poner más capas” no garantiza mejor modelo?


9.0.1 Respuesta
╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌

  ┌────

  └────


10 Pregunta 9 — Análisis: elige arquitectura
════════════════════════════════════════════

  Elige *Perceptrón (o lineal simple)* / *MLP* / *CNN* y justifica en
  *una* frase:

  1. Tabla de alumnos: promedio, faltas, horas de estudio → ¿aprueba?
  2. Clasificar el color de un semáforo en una fotografía.
  3. Clases en el plano que *no* se separan con una recta.
  4. ¿Usarías CNN para autocompletar código o una secuencia larga de
     texto? ¿Sí/no y qué alternativa del curso mencionarías?


10.0.1 Respuesta
╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌

  ┌────

  └────


11 Pregunta 10 — Análisis: mirada de proyecto
═════════════════════════════════════════════

  1. Train accuracy altísima y validation baja: ¿qué sospechas? ¿Qué dos
     preguntas le harías al equipo en la defensa?
  2. ¿Por qué más neuronas o más capas no sustituyen un buen
     planteamiento del problema y buenos datos?
  3. Escribe *tres* preguntas orales (tuyas) para verificar que
     distinguen perceptrón, MLP y CNN.


11.0.1 Respuesta
╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌

  ┌────

  └────
