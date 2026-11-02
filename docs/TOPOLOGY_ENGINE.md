# Adaptive Labyrinth — Topology Engine Design

**Tagline:** A living maze for digital monsters.

The Topology Engine is the core subsystem that makes the Labyrinth *alive*. It owns the living graph and continuously rewrites it to herd Active Minotaurs toward the Kill Zone.

---

## 1. Purpose

Transform a static or semi-static digital environment into a dynamic, adversarial maze whose geometry actively works against the Minotaur.

---

## 2. Core Abstraction: The Living Graph

```
Graph G = (N, E)
```

- **N (Nodes)**: Security domains, processes, containers, hosts, network segments, memory regions, identity contexts, etc.
- **E (Edges)**: Allowed transitions, communication channels, execution rights, trust relationships, data flows.

Every node and edge carries dynamic attributes:

| Attribute       | Description                                      | Mutable by Engine |
|-----------------|--------------------------------------------------|-------------------|
| Cost            | Difficulty / risk for Minotaur to traverse       | Yes               |
| Permeability    | How easily traffic/processes can cross           | Yes               |
| Visibility      | How observable the element is to the Minotaur    | Yes               |
| Strength        | Resistance to probing or attack                  | Yes               |
| Lifespan        | Temporary vs persistent                          | Yes               |
| Affinity        | Pull toward or away from the Kill Zone           | Yes               |
| Trust Level     | How trusted the node/edge currently is           | Yes               |

---

## 3. Primary Responsibilities

1. **Maintain an accurate, real-time model** of the protected environment as a graph.
2. **Accept directives** from the Herding Policy Engine (e.g., “increase pressure on this region”, “seal all paths leading outward”).
3. **Execute topology mutations** safely and efficiently:
   - Slide / rotate / expand / contract walls
   - Seal or dissolve edges
   - Spawn deceptive paths
   - Harden critical boundaries
4. **Enforce the Three-Wall Communication Severance rule** automatically.
5. **Guarantee reversibility** for legitimate entities (temporary restrictions must be undoable).
6. **Expose state** to the Operator UI and logging systems.

---

## 4. Key Algorithms & Mechanisms

### 4.1 Funnel Construction
Continuously maintain at least one decreasing-cost path from the Minotaur’s current position toward the Kill Zone while raising the cost of all other directions.

### 4.2 Escape Route Collapse
Identify and seal high-utility escape edges (especially those leading to external communication or high-value lateral movement).

### 4.3 Predictive Pre-sealing
Using short-horizon prediction of Minotaur movement, seal corridors *before* the Minotaur reaches them.

### 4.4 Deception Layer
Spawn temporary false paths and attractive dead-ends that waste the Minotaur’s time and reveal its decision-making.

### 4.5 Three-Wall Counter
Track the number of significant defensive layers each Active Minotaur has crossed. At count = 3, trigger full external communication severance for that entity.

---

## 5. Interaction with Other Subsystems

| Subsystem          | Interaction with Topology Engine                              |
|--------------------|---------------------------------------------------------------|
| Perception         | Provides Minotaur locations, scores, and behavioral primitives |
| Herding Policy     | Issues high-level goals (“compress this region”, “open funnel”) |
| Kill Zone          | Signals when a Minotaur has entered the Center                |
| Evolution          | Receives post-hunt topology decision logs for learning        |
| Operator UI        | Streams live graph state and accepts manual overrides         |

---

## 6. Safety & Constraints

- Every mutation must be logged with reason and expected effect.
- Mutations that would permanently strand trusted entities are forbidden unless explicitly overridden.
- The Engine must support instantaneous global pause / freeze by an operator.
- Performance target: topology updates should complete fast enough to react to real-time movement (sub-second for most environments).

---

## 7. Open Design Questions

- What is the optimal granularity of nodes at different scales (process vs container vs host vs network)?
- How do we represent and manipulate cloud IAM, serverless, and ephemeral resources cleanly?
- What formal guarantees can we offer that legitimate business flows remain possible during a hunt?
- How aggressive should predictive pre-sealing be before it risks false positives?

---

## Status

This is the detailed design foundation for the Topology Engine. Implementation will begin in `/engine/topology/` once simulation prototypes validate the core ideas.
