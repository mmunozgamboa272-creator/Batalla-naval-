# Batalla-naval
## Descripción del Proyecto
Realizaremos un juego de Batalla Naval utilizando temas vistos en clase, tales como programación orientada a objetos. En caso de necesitarlo utilizaremos la IA como GitHub Copilot, entendiendo los conceptos y las dinámicas. En cuanto a programación orientada a objetos utilizaremos conceptos como: clases, encapsulación (conceptos vistos en clase) y otros como: métodos, reutilización y enums.

## Objetivos
-Aplicar lo visto en clase de Programación orientada a objetos
-Fortalecer habilidades blandas a la hora de trabajar en grupo
-Comprender los conceptos nuevos como: métodos, reutilización y enmus
-Aplicar conocimientos para crear un juego funcional

## Integrantes del Grupo

- Mariana Muñoz
- Juan Cocunubo
- Valeria Ascanio
- Alejandra Moyano

## Herramientas
-Lenguaje:Python
-Entorno:Computador
-IA:GitHub Copilot

## Procesos y Metodología

- Reuniones semanales: Para seguimiento del proyecto
- Control de versiones con Git
- Documentación continua

## Conceptos Programación orientada a objetos a Utilizar

- Clases: Estructuras para modelar entidades del juego
- Encapsulación: Concepto visto en clase utilizado para proteger datos, y definir si se puede acceder o no a ellos
- Métodos: Comportamientos de las clases
- Reutilización: Aprovechar código existente
- Enums: Para definir estados y valores constantes
- Estos últimos tres conceptos son nuevos para nosotras, guiados por una IA generativa

## Estructura del Proyecto

```
Batalla-naval---Proyecto-final/
├── README.md
├── src/
│   ├── juego.py
│   ├── tablero.py
│   └── jugador.py
└── docs/
    └── (documentación adicional)
```
Segunda entrega:
Funcionalidad tablero:
import random # importamos random para el juego aleatorios

class Tablero:
    # normas y reglas de juego.
    def __init__(self, filas, columnas):
        self.filas = filas
        self.columnas = columnas
        self.mar = "-"
        self.submarino = "S"
        self.disparo_fallado = "o"
        self.disparo_acertado = "*"
# creamos una matriz (tabla) de tamaño filas x columnas 
        self.tablero = [[self.mar for _ in range(columnas)] for _ in range(filas)]

    def mostrar(self):
        print("\nTablero:")
        for fila in self.tablero:
            print(" ".join(fila))

    def colocar_barco(self):
        x = random.randint(0, self.filas - 1)
        y = random.randint(0, self.columnas - 1)
        self.tablero[x][y] = self.submarino # cambia el valor de esa posicion por un barco S
 
    def disparar(self, x, y):
        if self.tablero[x][y] == self.submarino:
            print("impacto")
            self.tablero[x][y] = self.disparo_acertado
        else:
            print("agua")
            self.tablero[x][y] = self.disparo_fallado
