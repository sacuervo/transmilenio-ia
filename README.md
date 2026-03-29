# Sistema Inteligente de Rutas — TransMilenio Bogotá

**Curso:** Inteligencia Artificial / Análisis de Datos
**Universidad:** Ibero — Facultad de Ingeniería
**Actividad:** 2

---

## Descripción del proyecto

Sistema inteligente que, a partir de una **base de conocimiento** escrita en reglas lógicas sobre la red de TransMilenio, encuentra la **mejor ruta** entre dos estaciones usando algoritmos de búsqueda informada e informada.

### Algoritmos implementados

| Algoritmo | Criterio de optimización | Tipo |
|-----------|--------------------------|------|
| BFS       | Menor número de paradas  | No informado |
| A\*       | Menor tiempo de viaje    | Informado (heurística de distancia Manhattan) |

---

## Estructura del proyecto

```
transmilenio_ia/
├── knowledge_base.py   # Base de conocimiento: estaciones y reglas de conexión
├── search_engine.py    # Motor de inferencia: BFS y A*
├── main.py             # Interfaz de usuario (menú interactivo)
└── README.md           # Este archivo
```

---

## Requisitos

- Python 3.8 o superior
- No requiere librerías externas (solo módulos de la biblioteca estándar)

---

## Instrucciones de ejecución

### 1. Clonar el repositorio

```bash
git clone <url-del-repositorio>
cd transmilenio_ia
```

### 2. Ejecutar el sistema interactivo

```bash
python main.py
```

El programa mostrará la lista de estaciones disponibles y pedirá origen y destino.

### 3. Ejecutar pruebas de los algoritmos directamente

```bash
python search_engine.py
```

Esto corre tres rutas de prueba predefinidas y muestra la comparación entre BFS y A*.

### 4. Explorar la base de conocimiento

```bash
python knowledge_base.py
```

Muestra todas las estaciones y conexiones registradas en el sistema.

---

## Ejemplo de uso

```
╔══════════════════════════════════════════════════════╗
║     SISTEMA INTELIGENTE DE RUTAS — TransMilenio      ║
╚══════════════════════════════════════════════════════╝

  Estaciones disponibles:
     1. Av. Jiménez
     2. Banderas
     3. Biblioteca Tintal
     ...

  Estación de ORIGEN: Portal Norte
  Estación de DESTINO: Portal Sur

  ══════════════════════════════════════════════════════
    RUTA: Portal Norte  →  Portal Sur
  ══════════════════════════════════════════════════════

    Algoritmo : BFS — Menos paradas
    Paradas   : 9
    Transbord.: 0
    Tiempo est: 38 min

    🟢 INICIO  → Portal Norte  [Caracas]
    ⬜ Paso  1 → Toberín       [Caracas]
    ...
    🔴 LLEGADA → Portal Sur    [Caracas]
```

---

## Base de conocimiento

Las estaciones y conexiones se definen como **hechos** y **reglas** en `knowledge_base.py`:

```python
# HECHO: estación con su troncal y coordenadas
"Portal Norte": {"troncal": "Caracas", "x": 4, "y": 10}

# REGLA: conexión bidireccional con tiempo y flag de transbordo
("Portal Norte", "Toberín", 4, False)
```

La función `heuristica()` estima el tiempo restante usando distancia Manhattan entre coordenadas, lo que guía al algoritmo A* hacia el destino de forma eficiente.

---

## Referencia académica

- Hurbans, R. (2020). *Grokking Artificial Intelligence Algorithms*. Manning Publications. Capítulos 3 y 4.
