<div align="center">

# 🧭 Algoritmia y Complejidad · UAH

**Algorithms and Complexity (Algoritmia y Complejidad, 780021) · B.S. Computer Engineering · Universidad de Alcalá · 2025–2026**

[![build](https://github.com/MiguelHernandezz/Algoritmia-y-Complejidad/actions/workflows/build.yml/badge.svg)](https://github.com/MiguelHernandezz/Algoritmia-y-Complejidad/actions/workflows/build.yml)
![Python](https://img.shields.io/badge/Python_3.10+-3776AB?style=flat-square&logo=python&logoColor=white)
![pytest](https://img.shields.io/badge/pytest-13_tests-0A9EDC?style=flat-square&logo=pytest&logoColor=white)
![Team](https://img.shields.io/badge/team-3_people-00C853?style=flat-square)

</div>

**UAH-Route**: a delivery-planning system for the UAH campus that chains two NP-hard problems. First it picks the most valuable set of orders that fits in the van, then it finds the cheapest route to deliver them over the real campus graph.

> Done in a **team of 3**. My teammates' names have been removed from the report for privacy. **My part:** project structure, the scenario generator (`utils/generador_escenarios.py`) and the start of the dynamic-programming order selection (`dp_seleccion.py`).

Every push runs the unit tests and all six scenarios on Ubuntu with [GitHub Actions](.github/workflows/build.yml).

---

## 📁 Contents

| Folder | Practice | Report |
|---|---|---|
| [`PL4-5-optimizacion-logistica`](PL4-5-optimizacion-logistica) | Practice 4-5: dynamic programming and backtracking with branch and bound | [Informe_PL4-5.docx](PL4-5-optimizacion-logistica/Informe_PL4-5.docx) |

---

## How it works

| Phase | What happens | Technique |
|---|---|---|
| 1 | Load the vehicle (weight and volume capacity) and the orders | JSON scenarios |
| 2 | Choose the best subset of orders | **0/1 knapsack with two constraints** (weight + volume), 3-D **dynamic programming**; compared with a greedy heuristic; orders ranked with **Quicksort** |
| 3 | Plan the delivery route | **All-pairs shortest paths with Floyd-Warshall** (the campus graph isn't complete), then **TSP by backtracking with branch and bound**, timed with and without pruning; **Held-Karp** when there are more than 10 stops |
| 4 | Load the van in reverse delivery order | **LIFO** stack, ASCII route view |
| 5 | A road gets blocked | Distances recomputed and the route re-planned |

Extra modules: **binary search** for the minimum vehicle capacity that reaches a target % of value, and a **recursive** random-scenario generator over real campus buildings.

---

## ▶️ Run it

Requires Python 3.10+. The algorithms use only the standard library.

```bash
cd PL4-5-optimizacion-logistica/src
python main.py                 # interactive menu: 5 fixed scenarios + random generator
```

Tests and the optional graph drawing (`Grafo.py`) need a few packages:

```bash
cd PL4-5-optimizacion-logistica
pip install -r requirements.txt
python -m pytest -v src/tests
```

---

<div align="center">

Miguel Hernández López · [GitHub](https://github.com/MiguelHernandezz) · [LinkedIn](https://www.linkedin.com/in/miguel-hernandez-lopez/)

</div>
