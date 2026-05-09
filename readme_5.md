# Programming Assignment – AI Algorithms

---

ABHINAV SAI

SE24UCSE179

## Task 1 – Search Algorithms

### How to Run

```bash
python task1_search_algorithms/minimax.py
python task1_search_algorithms/alpha_beta.py
python task1_search_algorithms/heuristic_alpha_beta.py
python task1_search_algorithms/mcts.py
```

### What Each File Does

| File | Algorithm | Key Idea |
|---|---|---|
| `minimax.py` | Minimax | MAX player tries to maximise, MIN player tries to minimise. Searches the entire game tree. |
| `alpha_beta.py` | Alpha-Beta Pruning | Same as Minimax but skips branches that cannot change the result. Faster! |
| `heuristic_alpha_beta.py` | Heuristic Alpha-Beta | Adds a depth limit + heuristic function to estimate positions without full search. |
| `mcts.py` | Monte Carlo Tree Search | Runs hundreds of random game simulations to estimate the best move statistically. |

### Demo Game

All four algorithms use **Tic-Tac-Toe** as the demo game.  
The board positions are numbered 0–8:

```text
0 | 1 | 2
---------
3 | 4 | 5
---------
6 | 7 | 8
```

### Test Cases (Task 1)

Each file contains 3 test cases:

1. Evaluation of a sample game tree
2. Choosing a blocking move (AI must stop opponent from winning)
3. Choosing a winning move (AI must win immediately)

---

## Task 2 – AI-Based Travel Planner

### How to Run

```bash
python task2_travel_planner/travel_planner.py
```

### Knowledge Bases Used

| KB | Contents |
|---|---|
| `TOURIST_PLACES_KB` | Destinations, attractions, best season |
| `FOOD_KB` | Must-try local foods per city |
| `WINE_KB` | Wine / drink recommendations per region |
| `COST_KB` | Daily cost estimate per city (budget / mid / luxury) |
| `INTEREST_MATCH_KB` | Maps user interests → best destinations |

### How It Works

1. User inputs: name, interests, destination, days, budget level
2. System recommends destinations based on interests
3. Builds a day-by-day itinerary from attractions
4. Suggests local food and wine
5. Estimates total trip cost

### Test Cases (Task 2)

1. Art & wine lover planning 5 days in Tuscany (mid budget)
2. Beach & relaxation lover planning 4 days in Goa (budget)
3. Unknown destination falls back to best recommendation

---

## Task 3 – Knowledge Graphs

### How to Run

```bash
python task3_knowledge_graphs/knowledge_graph.py
```

### What is a Knowledge Graph?

A Knowledge Graph stores facts as **triples**:

```text
(subject)  --[predicate]-->  (object)
```

Example:

```text
(Eiffel Tower) --[locatedIn]--> (Paris)
(Paris)        --[locatedIn]--> (France)
(Chianti)      --[producedIn]--> (Italy)
```

### Features Implemented

* `add(subject, predicate, object)` – add a fact
* `query(subject, predicate, object)` – wildcard search
* `get_related(entity, predicate)` – get all objects for an entity + relationship
* `describe(entity)` – print everything known about an entity
* `get_all_predicates()` – list all relationship types

### Test Cases (Task 3)

1. Printing the full graph
2. Describing the entity "Paris"
3. Querying what is located in Paris
4. Getting what Paris is suitable for
5. Listing all predicates (relationship types)
6. Listing all entities

---

## Task 4 – Bayesian Networks

### How to Run

```bash
python task4_bayesian_networks/bayesian_network.py
```

### What is a Bayesian Network?

A Bayesian Network is a directed graph where:

* **Nodes** = random variables (e.g. Rain, Cloudy)
* **Edges** = causal relationships (Cloudy → Rain)
* Each node has a **Conditional Probability Table (CPT)**

### Example – Weather Network

```text
     Cloudy
    /      \
 Rain    Sprinkler
    \\      /
    WetGrass
```

CPT examples:

```text
P(Cloudy = True)               = 0.5
P(Rain = True | Cloudy = True) = 0.8
P(Rain = True | Cloudy= False) = 0.2
```

### Inference Methods Implemented

| Method | Type | Description |
|---|---|---|
| Prior Sampling | Approximate | Generate random samples from the joint distribution |
| Rejection Sampling | Approximate | Sample then reject samples inconsistent with evidence |
| Exact Enumeration | Exact | Sum over all hidden variables to get exact probabilities |

### Tools for Real Bayesian Networks

| Tool | Description |
|---|---|
| **pgmpy** | Python library for BNs |
| **PyMC** | Probabilistic programming |
| **Netica** | GUI tool for BNs |
| **GeNIe** | Free BN modelling software |
| **BayesiaLab** | Commercial BN software |

### Test Cases (Task 4)

1. Prior sampling sanity check
2. P(Rain=True | Cloudy=True) = 0.80 (exact)
3. P(Sprinkler=True | Cloudy=False) = 0.50 (exact)
4. P(Rain=True | WetGrass=True) ≈ 0.71 (rejection sampling)
5. P(WetGrass=True | Rain=False, Sprinkler=False) = 0.0 (exact)

---

## Running All Tests

To run all tests at once:

```bash
python task1_search_algorithms/minimax.py
python task1_search_algorithms/alpha_beta.py
python task1_search_algorithms/heuristic_alpha_beta.py
python task1_search_algorithms/mcts.py
python task2_travel_planner/travel_planner.py
python task3_knowledge_graphs/knowledge_graph.py
python task4_bayesian_networks/bayesian_network.py
```

All files print **PASS** for each test case and a final summary line.

---

