# TC2008B_Proyecto_Multiagentes
Repositorio para el trabajo realizado en equipo del proyecto de multiagentes

## Plano provisional de paredes

Cada casilla se identifica como `(fila, columna)`, con índices desde 1. Las filas avanzan hacia −Z y las columnas hacia +X. `(1, 1)` es `GameBoard/Row1/Cell1`, en la esquina noroeste. Su centro en Unity es `(−14, 0, 10)`. La cuadrícula mide 32 × 24 y cada casilla mide 4 × 4 unidades.

~~~text
       1 2 3 4 5 6 7 8
Fila 1 A A A C C D D D
Fila 2 A A A C C D D D
Fila 3 B B C C C C E E
Fila 4 B B C C C C E E
Fila 5 B B B F F E E E
Fila 6 B B B F F E E E
~~~

A es Comunicaciones, B es Ingeniería, C es el Atrio, D es el Laboratorio, E es Enfermería y F es Almacén. Las letras indican sectores del plano.

`H(k, c)` es el borde paralelo a X entre las filas `k` y `k + 1`, en la columna `c`. `H(0, c)` y `H(6, c)` son los lados norte y sur. `V(r, k)` es el borde paralelo a Z entre las columnas `k` y `k + 1`, en la fila `r`. `V(r, 0)` y `V(r, 8)` son los lados oeste y este. Los centros indicados son los centros nominales de cada borde. El ajuste visual de las uniones se aplica solo a los extremos de algunas paredes.

Para Python, cada pared bloquea el paso entre las dos casillas del borde. Los bordes interiores de esta lista de vanos se reservan para compuertas. Los demás bordes interiores que no figuran en ninguna tabla quedan abiertos. El convenio de coordenadas está pendiente de contrastar con el archivo oficial.

### Vanos para compuertas

| Tipo | Borde | Casillas | Sectores | Centro XZ |
| --- | --- | --- | --- | --- | --- |
| Interior | `V(1, 3)` | (1, 3) ↔ (1, 4) | A ↔ C | `(-4, 10)` |
| Interior | `V(3, 2)` | (3, 2) ↔ (3, 3) | B ↔ C | `(-8, 2)` |
| Interior | `V(1, 5)` | (1, 5) ↔ (1, 6) | C ↔ D | `(4, 10)` |
| Interior | `V(3, 6)` | (3, 6) ↔ (3, 7) | C ↔ E | `(8, 2)` |
| Interior | `H(4, 4)` | (4, 4) ↔ (5, 4) | C ↔ F | `(-2, -4)` |
| Interior | `H(2, 1)` | (2, 1) ↔ (3, 1) | A ↔ B | `(-14, 4)` |
| Interior | `H(2, 8)` | (2, 8) ↔ (3, 8) | D ↔ E | `(14, 4)` |
| Interior | `V(6, 3)` | (6, 3) ↔ (6, 4) | B ↔ F | `(-4, -10)` |
| Norte | `H(0, 4)` | Exterior ↔ (1, 4) | Exterior ↔ C | `(-2, 12)` |
| Este | `V(4, 8)` | (4, 8) ↔ Exterior | E ↔ Exterior | `(16, -2)` |
| Sur | `H(6, 5)` | (6, 5) ↔ Exterior | F ↔ Exterior | `(2, -12)` |
| Oeste | `V(3, 0)` | Exterior ↔ (3, 1) | Exterior ↔ B | `(-16, 2)` |

### Paredes

| Objeto | Borde | Casillas | Centro XZ |
| --- | --- | --- | --- |
| Wall1 | `H(0, 1)` | Exterior ↔ (1, 1) | `(-14, 12)` |
| Wall2 | `H(0, 2)` | Exterior ↔ (1, 2) | `(-10, 12)` |
| Wall3 | `H(0, 3)` | Exterior ↔ (1, 3) | `(-6, 12)` |
| Wall4 | `H(0, 5)` | Exterior ↔ (1, 5) | `(2, 12)` |
| Wall5 | `H(0, 6)` | Exterior ↔ (1, 6) | `(6, 12)` |
| Wall6 | `H(0, 7)` | Exterior ↔ (1, 7) | `(10, 12)` |
| Wall7 | `H(0, 8)` | Exterior ↔ (1, 8) | `(14, 12)` |
| Wall8 | `H(2, 2)` | (2, 2) ↔ (3, 2) | `(-10, 4)` |
| Wall9 | `H(2, 3)` | (2, 3) ↔ (3, 3) | `(-6, 4)` |
| Wall10 | `H(2, 6)` | (2, 6) ↔ (3, 6) | `(6, 4)` |
| Wall11 | `H(2, 7)` | (2, 7) ↔ (3, 7) | `(10, 4)` |
| Wall12 | `H(4, 3)` | (4, 3) ↔ (5, 3) | `(-6, -4)` |
| Wall13 | `H(4, 5)` | (4, 5) ↔ (5, 5) | `(2, -4)` |
| Wall14 | `H(4, 6)` | (4, 6) ↔ (5, 6) | `(6, -4)` |
| Wall15 | `H(6, 1)` | (6, 1) ↔ Exterior | `(-14, -12)` |
| Wall16 | `H(6, 2)` | (6, 2) ↔ Exterior | `(-10, -12)` |
| Wall17 | `H(6, 3)` | (6, 3) ↔ Exterior | `(-6, -12)` |
| Wall18 | `H(6, 4)` | (6, 4) ↔ Exterior | `(-2, -12)` |
| Wall19 | `H(6, 6)` | (6, 6) ↔ Exterior | `(6, -12)` |
| Wall20 | `H(6, 7)` | (6, 7) ↔ Exterior | `(10, -12)` |
| Wall21 | `H(6, 8)` | (6, 8) ↔ Exterior | `(14, -12)` |
| Wall22 | `V(1, 0)` | Exterior ↔ (1, 1) | `(-16, 10)` |
| Wall23 | `V(1, 8)` | (1, 8) ↔ Exterior | `(16, 10)` |
| Wall24 | `V(2, 0)` | Exterior ↔ (2, 1) | `(-16, 6)` |
| Wall25 | `V(2, 3)` | (2, 3) ↔ (2, 4) | `(-4, 6)` |
| Wall26 | `V(2, 5)` | (2, 5) ↔ (2, 6) | `(4, 6)` |
| Wall27 | `V(2, 8)` | (2, 8) ↔ Exterior | `(16, 6)` |
| Wall28 | `V(3, 8)` | (3, 8) ↔ Exterior | `(16, 2)` |
| Wall29 | `V(4, 0)` | Exterior ↔ (4, 1) | `(-16, -2)` |
| Wall30 | `V(4, 2)` | (4, 2) ↔ (4, 3) | `(-8, -2)` |
| Wall31 | `V(4, 6)` | (4, 6) ↔ (4, 7) | `(8, -2)` |
| Wall32 | `V(5, 0)` | Exterior ↔ (5, 1) | `(-16, -6)` |
| Wall33 | `V(5, 3)` | (5, 3) ↔ (5, 4) | `(-4, -6)` |
| Wall34 | `V(5, 5)` | (5, 5) ↔ (5, 6) | `(4, -6)` |
| Wall35 | `V(5, 8)` | (5, 8) ↔ Exterior | `(16, -6)` |
| Wall36 | `V(6, 0)` | Exterior ↔ (6, 1) | `(-16, -10)` |
| Wall37 | `V(6, 5)` | (6, 5) ↔ (6, 6) | `(4, -10)` |
| Wall38 | `V(6, 8)` | (6, 8) ↔ Exterior | `(16, -10)` |

## Naves de evacuación

El modelo [Spaceship](https://poly.pizza/m/xNbtFQwirO) fue creado por Quaternius y se distribuye bajo la licencia [CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/). Se importó en formato OBJ para usarlo con el importador de Unity, conservando los dos materiales del modelo original.

En `SampleScene`, `EvacuationZones` agrupa las zonas `North`, `East`, `South` y `West`, frente a `Door9`, `Door10`, `Door11` y `Door12`, respectivamente. Cada zona tiene una instancia de `Spaceship` orientada hacia su compuerta y situada sobre `ExteriorFloor`, el perímetro visual de 4.5 unidades hecho con el piso de Kenney. El perímetro queda fuera de las 48 casillas de simulación.

## Astronauta

[Astronaut](https://poly.pizza/m/erlAEWfFKH3) fue creado por PW Wu y se distribuye bajo la licencia [Creative Commons Attribution 3.0 (CC BY 3.0)](https://creativecommons.org/licenses/by/3.0/). El proyecto conserva la geometría y los ocho colores del OBJ y su archivo de materiales original. Se agruparon las piezas para la importación y se ajustó la escala del prefab a 1.65 unidades de altura.

En `SampleScene`, `Agents/Astronaut` es la instancia de prueba situada en la casilla `(3, 4)`.
