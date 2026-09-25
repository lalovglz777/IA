# Reporte EDA — Operación Dino Crash

**Analista:** Eduardo Vargas González / 22121302

## 1. Problema y dataset (Misión 1)

### P1 — Muerte en el siguiente frame

- Y: La variable objetivo podría llamarse muere_siguiente_frame y sería de tipo binaria. Si el dinosaurio muere en el siguiente frame obtiene un valor de 1; si no muere, tendrá un valor de 0.

- X (mínimo 5 variables):

  1. distancia_obstaculo: sirve para conocer la distancia entre el dinosaurio y el obstáculo.
  2. velocidad: entre mayor sea la velocidad, el obstáculo recorre mayor distancia entre cada frame.
  3. tipo_obstaculo: permite saber si el obstáculo es un ave o un cactus.
  4. dino_altura: permite saber si el dinosaurio está suficientemente elevado para pasar el obstáculo.
  5. agachado: permite conocer si está agachado, ya que esto modifica su tamaño y puede ayudarlo a evitar las aves.

- Granularidad: Se requiere una fila por cada frame para relacionar lo que sucede en el actual con lo que sucede inmediatamente en el siguiente.

- Tamaño mínimo de dataset: Dos mil partidas completas registradas frame por frame. Cada partida debería terminar en una muerte y aportaría un ejemplo positivo. Además, muchas partidas pueden parecerse entre sí, por lo que habría que considerar jugadores con diferentes estilos de juego.

- Riesgo: Usar la muerte en el frame actual llevaría a resultados inadecuados, ya que el modelo aprendería a identificar si el dinosaurio ya murió y no a anticipar su muerte.

### P2 — Puntuación final de la partida

- Y: La variable objetivo podría llamarse marcador_final y sería de tipo numérica, ya que representa una medida en puntos del juego.

- X (mínimo 5 variables):

  1. promedio_general: permite conocer cómo se ha desempeñado el jugador en partidas anteriores.
  2. partidas_totales: permite conocer la experiencia del usuario en el juego.
  3. tiempo_reaccion: sirve para analizar si los jugadores con menor tiempo de reacción alcanzan mayores puntajes.
  4. metodo_entrada: jugar con teclado o pantalla táctil podría afectar la jugabilidad.
  5. dispositivo: permite comparar el desempeño entre móviles y computadoras.

- Granularidad: Se generaría una fila por partida, ya que los datos de entrada se registrarían antes de comenzar y el marcador final se conocería al terminar.

- Tamaño mínimo de dataset: Mil partidas completas de diferentes jugadores, dispositivos y métodos de entrada. También sería necesario tener puntuaciones bajas, medias y altas para no contar únicamente con un solo tipo de resultado.

- Riesgo: Agregar como entrada el tiempo total de la partida sería un error, ya que todavía no se conoce al comenzar. El modelo podría parecer muy preciso al entrenarse, pero esa información no estaría disponible en una partida nueva.

### P3 — Tipo del próximo obstáculo

- Y: La variable objetivo podría llamarse siguiente_obstaculo_tipo y sería categórica, ya que representa una clase de obstáculo.

- X (mínimo 5 variables):

  1. ancho_obstaculo: permite distinguir el tamaño del obstáculo.
  2. alto_obstaculo: ayuda a diferenciar cactus pequeños y grandes.
  3. posicion_y: permite distinguir si el obstáculo está apoyado en el suelo o se encuentra elevado.
  4. velocidad_obstaculo: permite saber si existen diferencias de velocidad entre los tipos de obstáculos.
  5. puntuacion: permite revisar si la frecuencia de ciertos obstáculos cambia conforme avanza la partida.

- Granularidad: Se debe registrar una fila cada vez que aparezca un nuevo obstáculo. Aunque sea igual al anterior, debe tener un identificador para saber que es un obstáculo diferente. Un mismo obstáculo no debe registrarse varias veces solamente porque aparezca durante varios frames.

- Tamaño mínimo de dataset: En algunos cientos de partidas se podría obtener el registro de miles de obstáculos. Sería necesario contar con suficientes ejemplos de cada tipo.

- Riesgo: Agregar el tipo de obstáculo como variable de entrada sería un error, ya que es precisamente lo que se busca predecir.

## 2. Diccionario y muestra (Misión 2)

- Patrón en died=1: En el frame 82 se observa que el dinosaurio está muy cerca de un cactus pequeño y no está saltando.

- ¿score es buena variable para P1?: Aporta poca información en comparación con saber si está saltando, lo cual es más importante. Además, la puntuación se relaciona con el tiempo de juego y en los frames 80, 81 y 82 sigue siendo 16, aunque el resultado cambia.

- ¿Falta alguna columna?: Sí. Faltaría saber si el dinosaurio está agachado, la altura del obstáculo y la altura actual del dinosaurio.

- ¿Sirve died tal como está?: Describe la muerte en el frame actual, pero necesitamos una variable que permita saber si morirá en el siguiente frame. El frame actual solo se descartaría cuando el dinosaurio ya esté muerto.

## 3. Checklist EDA (Misión 3)

### Tres preguntas elegidas

1. ¿Hay valores faltantes? Supongamos que falta la distancia del obstáculo cuando obstacle_type es none. Podría significar que no hay ningún obstáculo al cual medirle la distancia. No se debería sustituir por 0, ya que eso significaría que el obstáculo está al lado del dinosaurio.

2. ¿La clase objetivo está balanceada? No, porque de todos los frames que genera una partida solo uno anticiparía una muerte. Habría muchos más ceros que unos, por lo que durante el entrenamiento se podría dar mayor peso a las muertes.

3. ¿Hay sesgo de muestreo? Si todas las partidas fueran únicamente de expertos, el dataset estaría mal representado. Se deberían considerar jugadores de distintos niveles, dispositivos y formas de jugar.

### Pregunta 8: datos i.i.d.

Poner un frame en entrenamiento y el inmediato en prueba sería un error, ya que ambos podrían tener posiciones y velocidades muy similares. Sería mejor guardar un identificador de sesión para reservar partidas completas para entrenamiento y otras partidas completas para prueba.

### Ejemplo de data leakage

Un ejemplo sería usar el tiempo total de la partida menos el tiempo actual de juego. El problema es que durante una partida actual todavía no se conoce el tiempo total que durará, por lo que estaríamos usando información del futuro.

## 4. Interpretación de resúmenes (Misión 4)

1. Desbalance: Sí existe, porque hay muchos más ceros que unos. Existen 50 muertes en 12,000 frames:

   50 / 12000 × 100 = 0.42 %

   Aproximadamente el 0.42 % corresponde a muertes y el 99.58 % a frames sin muerte.

2. Métricas: Se consideraría el recall para saber, de todas las muertes, cuántas anticipó realmente. La precision permitiría saber, de todas las alertas de muerte, cuántas fueron correctas. F1 combina precision y recall para evaluar el equilibrio entre ambas. Accuracy por sí sola sería engañosa por el desbalance.

3. dist_obstacle: Sí parece aportar información, ya que las muertes suelen ocurrir con distancias pequeñas. También sería importante conocer la distancia en el frame inmediatamente anterior a la muerte y considerar velocidad, altura y movimiento.

4. Distribución de score: La media de 28 es mayor que la mediana de 18, lo que coincide con una cola larga hacia la derecha causada por algunas puntuaciones altas. Esto no significa automáticamente que se deba descartar la regresión simple. Primero habría que analizar las puntuaciones finales por partida y, si también tienen una cola muy marcada, se podría probar una transformación.

## 5. Elección de modelo (Misiones 5–6)

### Misión 5

| Escenario | Fila de la guía que aplica | Modelo propuesto | Dos condiciones del dataset |
| --- | --- | --- | --- |
| P1 | Y binaria, datos tabulares y clase muerte muy desbalanceada. | Árbol de clasificación de poca profundidad con pesos de clase. | Etiquetas alineadas con el siguiente frame y suficientes muertes de partidas distintas. |
| P2 | Y numérica: problema de regresión. | Regresión lineal como modelo inicial. | Entradas disponibles antes de comenzar y puntuaciones variadas. |
| P3 | Y categórica multiclase. | Árbol de clasificación pequeño. | No incluir el tipo de obstáculo entre las entradas y tener suficientes ejemplos de cada categoría. |

### Misión 6

1. Tenemos 12,000 frames y podrían parecer suficientes para entrenar un árbol profundo, pero provienen de solamente 50 partidas y contienen 50 muertes. El árbol podría memorizar situaciones particulares y fallar al encontrar una diferente. Esto sería sobreajuste. Una mejor opción sería usar un árbol pequeño y recopilar más partidas y muertes.

2. Una red neuronal tendría sentido si quisiéramos predecir la muerte usando secuencias recientes de imágenes recopiladas en miles de partidas diferentes. El EDA debería mostrar variedad, suficientes casos de muerte, orden temporal y partidas distintas para entrenamiento y prueba.

3. Se podría crear una regla como: si la distancia al obstáculo es menor que 20 y el dinosaurio no está saltando, entonces predecir una muerte en el siguiente frame. La ventaja es que sería fácil de entender y rápida. Su límite es que no considera velocidad, altura, movimiento ni el tipo de obstáculo. Un modelo aprendido podría combinar esas características, pero necesita datos adecuados y también podría aprender errores o sesgos.

## Síntesis (5 líneas)

Primero pediría datos por frame para P1, por partida para P2 y por obstáculo para P3.  
Revisaría que las variables y las etiquetas correspondan con lo que se quiere predecir.  
También revisaría datos faltantes, desbalance, sesgo y separación de partidas.  
Después del EDA usaría árboles pequeños para P1 y P3, y regresión lineal para P2.  
Solo usaría modelos más complejos si existe una cantidad suficiente de datos para justificarlos.
