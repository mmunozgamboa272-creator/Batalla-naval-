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

# Funcionalidad tablero:
```
import random
import csv

class Tablero:
    def __init__(self, filas, columnas, intentos_max): 
        self.filas = filas 
        self.columnas = columnas 
        self.mar = "-" 
        self.submarino = "S" 
        self.disparo_fallado = "o" 
        self.disparo_acertado = "*" 
    
        # Nuevas variables pedidas por el ejercicio
        self.barcos_restantes = 0
        self.barcos_derribados = 0
        self.intentos_restantes = intentos_max
        
        self.tablero = [[self.mar for _ in range(columnas)] for _ in range(filas)]

    def mostrar(self):
        print(f"\n--- ESTADO DE LA PARTIDA ---")
        print(f"Barcos restantes: {self.barcos_restantes} | Derribados: {self.barcos_derribados} | Intentos: {self.intentos_restantes}")
        print("\nTablero Enemigo:")
        for fila in self.tablero:
            print(" ".join(fila))

    def colocar_barco(self):
        x = random.randint(0, self.filas - 1)
        y = random.randint(0, self.columnas - 1)
        if self.tablero[x][y] == self.mar:
            self.tablero[x][y] = self.submarino
            self.barcos_restantes += 1

    def disparar(self, x, y):
        if self.intentos_restantes <= 0:
            print("¡No te quedan más misiles!")
            return

        if self.tablero[x][y] == self.submarino:
            print("¡IMPACTO!")
            self.tablero[x][y] = self.disparo_acertado
            self.barcos_restantes -= 1
            self.barcos_derribados += 1
        else:
            print("AGUA...")
            self.tablero[x][y] = self.disparo_fallado
        
        self.intentos_restantes -= 1

    # CSV
    def cargar_desde_csv(self, nombre_archivo):
        with open(nombre_archivo, 'r') as archivo:
            lector = csv.reader(archivo)
            self.tablero = list(lector)
 
1. Creamos el tablero (filas, columnas, intentos)
T = Tablero(5, 5, 10) 
2. Ponemos un barco para probar
T.colocar_barco()
3. ¡Mostramos el tablero!
T.mostrar()
4. Probamos un disparo
T.disparar(0, 0) 
5. Mostramos cómo quedó
T.mostrar()
```
