# Algoritmo A* con Pygame

## Descripción

Implementación del algoritmo de búsqueda **A*** utilizando Python y Pygame.

El programa utiliza una cuadrícula de **14 x 14** en la cual se pueden colocar obstáculos utilizando el mouse.  
El algoritmo A* busca el camino desde la celda inicial hasta la meta evitando los obstáculos.

Para calcular la prioridad de cada celda se utiliza:

**f(n) = g(n) + h(n)**

Donde:

- **g(n):** costo real desde el inicio hasta la celda actual.
- **h(n):** estimación desde la celda actual hasta la meta.
- **f(n):** costo utilizado por A* para decidir qué celda explorar.

La heurística utilizada es la **distancia Manhattan**.

---

## Controles

- **Clic izquierdo:** agregar obstáculo.
- **Clic derecho:** eliminar obstáculo.
- **ESPACIO:** ejecutar el algoritmo A*.
- **R:** reiniciar el tablero.

---

## Colores

- **Verde:** inicio.
- **Rojo:** meta.
- **Negro:** obstáculos.
- **Azul:** camino encontrado.

---

## Código

```python
import pygame
import sys
import heapq

# --------------------------------------------------
# INICIAR PYGAME
# --------------------------------------------------

pygame.init()


# --------------------------------------------------
# CONFIGURACIÓN DE LA CUADRÍCULA
# --------------------------------------------------

FILAS = 14
COLUMNAS = 14
TAM_CELDA = 30

ANCHO = COLUMNAS * TAM_CELDA

# Altura de la cuadrícula
ALTO_CUADRICULA = FILAS * TAM_CELDA

# Espacio extra para mostrar los controles
ALTO_CONTROLES = 70

# Altura total de la ventana
ALTO = ALTO_CUADRICULA + ALTO_CONTROLES


# --------------------------------------------------
# COLORES
# --------------------------------------------------

BLANCO = (255, 255, 255)
GRIS = (180, 180, 180)
NEGRO = (0, 0, 0)
VERDE = (0, 200, 0)
ROJO = (220, 0, 0)
AZUL = (0, 120, 255)


# --------------------------------------------------
# CREAR VENTANA
# --------------------------------------------------

ventana = pygame.display.set_mode((ANCHO, ALTO))
pygame.display.set_caption("Algoritmo A*")

# Fuente para mostrar los controles
fuente = pygame.font.SysFont("Arial", 16)


# --------------------------------------------------
# POSICIONES DE INICIO Y META
# --------------------------------------------------

inicio = (0, 0)
meta = (FILAS - 1, COLUMNAS - 1)


# --------------------------------------------------
# OBSTÁCULOS Y CAMINO
# --------------------------------------------------

obstaculos = set()
camino = []


# --------------------------------------------------
# CONVERTIR POSICIÓN DEL MOUSE A CELDA
# --------------------------------------------------

def obtener_celda(posicion_mouse):

    x, y = posicion_mouse

    columna = x // TAM_CELDA
    fila = y // TAM_CELDA

    return fila, columna


# --------------------------------------------------
# OBTENER VECINOS
# --------------------------------------------------

def obtener_vecinos(celda):

    fila, columna = celda

    movimientos = [
        (-1, 0),  # arriba
        (1, 0),   # abajo
        (0, -1),  # izquierda
        (0, 1)    # derecha
    ]

    vecinos = []

    for cambio_fila, cambio_columna in movimientos:

        nueva_fila = fila + cambio_fila
        nueva_columna = columna + cambio_columna

        nuevo_vecino = (
            nueva_fila,
            nueva_columna
        )

        dentro_tablero = (
            0 <= nueva_fila < FILAS
            and
            0 <= nueva_columna < COLUMNAS
        )

        if (
            dentro_tablero
            and
            nuevo_vecino not in obstaculos
        ):
            vecinos.append(nuevo_vecino)

    return vecinos


# --------------------------------------------------
# HEURÍSTICA
# --------------------------------------------------

def heuristica(celda, meta):

    fila, columna = celda
    fila_meta, columna_meta = meta

    # Distancia Manhattan
    distancia = (
        abs(fila - fila_meta)
        +
        abs(columna - columna_meta)
    )

    return distancia


# --------------------------------------------------
# ALGORITMO A*
# --------------------------------------------------

def a_estrella(inicio, meta):

    # Celdas pendientes por explorar
    pendientes = []

    # Costo real para llegar a cada celda
    g_score = {
        inicio: 0
    }

    # Guarda de qué celda venimos
    came_from = {}

    # Calcular f del inicio
    f_inicio = heuristica(inicio, meta)

    # Agregar inicio a pendientes
    heapq.heappush(
        pendientes,
        (f_inicio, inicio)
    )

    # Mientras existan celdas pendientes
    while pendientes:

        # Sacar la celda con menor f
        f_actual, actual = heapq.heappop(
            pendientes
        )

        # Comprobar si llegamos a la meta
        if actual == meta:

            camino_encontrado = [actual]

            # Reconstruir el camino
            while actual in came_from:

                actual = came_from[actual]

                camino_encontrado.append(
                    actual
                )

            # El camino quedó al revés
            camino_encontrado.reverse()

            return camino_encontrado

        # Revisar vecinos
        for vecino in obtener_vecinos(actual):

            # Cada movimiento cuesta 1
            nuevo_g = g_score[actual] + 1

            # Si nunca llegamos a esta celda
            # o encontramos un camino más corto
            if (
                vecino not in g_score
                or
                nuevo_g < g_score[vecino]
            ):

                # Actualizar costo
                g_score[vecino] = nuevo_g

                # Guardar de dónde venimos
                came_from[vecino] = actual

                # f = g + h
                f_vecino = (
                    nuevo_g
                    +
                    heuristica(vecino, meta)
                )

                # Agregar a pendientes
                heapq.heappush(
                    pendientes,
                    (f_vecino, vecino)
                )

    # No existe camino
    return None


# --------------------------------------------------
# BUCLE PRINCIPAL
# --------------------------------------------------

while True:

    # Revisar eventos
    for evento in pygame.event.get():

        # Cerrar ventana
        if evento.type == pygame.QUIT:

            pygame.quit()
            sys.exit()

        # --------------------------------------------------
        # MOUSE
        # --------------------------------------------------

        if evento.type == pygame.MOUSEBUTTONDOWN:

            # Solo permitir clics dentro de la cuadrícula
            if evento.pos[1] < ALTO_CUADRICULA:

                celda = obtener_celda(
                    evento.pos
                )

                # Clic izquierdo: agregar obstáculo
                if evento.button == 1:

                    if (
                        celda != inicio
                        and
                        celda != meta
                    ):

                        obstaculos.add(celda)
                        camino.clear()

                # Clic derecho: quitar obstáculo
                elif evento.button == 3:

                    obstaculos.discard(celda)
                    camino.clear()

        # --------------------------------------------------
        # TECLADO
        # --------------------------------------------------

        if evento.type == pygame.KEYDOWN:

            # ESPACIO: ejecutar A*
            if evento.key == pygame.K_SPACE:

                resultado = a_estrella(
                    inicio,
                    meta
                )

                if resultado is not None:

                    camino = resultado

                    print("Camino encontrado:")
                    print(camino)

                else:

                    camino = []

                    print("No existe un camino")

            # R: reiniciar
            elif evento.key == pygame.K_r:

                obstaculos.clear()
                camino.clear()

                print("Tablero reiniciado")


    # --------------------------------------------------
    # DIBUJAR
    # --------------------------------------------------

    ventana.fill(BLANCO)

    # Dibujar cuadrícula
    for fila in range(FILAS):

        for columna in range(COLUMNAS):

            celda = (
                fila,
                columna
            )

            x = columna * TAM_CELDA
            y = fila * TAM_CELDA

            rectangulo = pygame.Rect(
                x,
                y,
                TAM_CELDA,
                TAM_CELDA
            )

            # Elegir color
            if celda == inicio:

                color = VERDE

            elif celda == meta:

                color = ROJO

            elif celda in obstaculos:

                color = NEGRO

            elif celda in camino:

                color = AZUL

            else:

                color = BLANCO

            # Pintar interior
            pygame.draw.rect(
                ventana,
                color,
                rectangulo
            )

            # Pintar borde
            pygame.draw.rect(
                ventana,
                GRIS,
                rectangulo,
                1
            )


    # --------------------------------------------------
    # MOSTRAR CONTROLES
    # --------------------------------------------------

    texto1 = fuente.render(
        "ESPACIO: ejecutar A*     R: reset",
        True,
        NEGRO
    )

    texto2 = fuente.render(
        "Clic izq: obstaculo     Clic der: borrar",
        True,
        NEGRO
    )

    ventana.blit(
        texto1,
        (
            10,
            ALTO_CUADRICULA + 10
        )
    )

    ventana.blit(
        texto2,
        (
            10,
            ALTO_CUADRICULA + 35
        )
    )


    # Actualizar pantalla
    pygame.display.flip()
```

---

## Funcionamiento del algoritmo

El algoritmo comienza agregando la celda inicial a una cola de prioridad.

En cada iteración:

1. Se obtiene la celda con el menor valor de **f(n)**.
2. Se comprueba si esa celda es la meta.
3. Si no es la meta, se obtienen sus vecinos.
4. Se calcula el nuevo costo **g(n)** para cada vecino.
5. Se calcula la heurística **h(n)** utilizando distancia Manhattan.
6. Se obtiene **f(n) = g(n) + h(n)**.
7. Si se encuentra una ruta más corta hacia una celda, se actualiza su costo.
8. El proceso continúa hasta encontrar la meta o quedarse sin celdas por explorar.

Cuando se encuentra la meta, se utiliza `came_from` para reconstruir el camino desde la meta hasta el inicio.

---

## Ejecución

Para ejecutar el programa es necesario tener Python y Pygame instalados.

Instalar Pygame:

```bash
pip install pygame
```

Ejecutar:

```bash
python astar.py
```
