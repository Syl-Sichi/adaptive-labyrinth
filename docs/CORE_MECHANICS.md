# Adaptive Labyrinth — Core Mechanics Spec

**Tagline:** A living maze for digital monsters.

This document defines the exact rules that make the Labyrinth function as a predatory defense system.

---

## 1. The Living Topology

The Labyrinth is modeled as a dynamic graph.

- **Nodes** represent security domains, processes, containers, network segments, or memory regions.
- **Edges** represent allowed transitions, communication channels, or execution paths.
- Both nodes and edges have mutable properties: strength, permeability, cost, visibility, and lifespan.

### Wall & Path Behaviors
Walls and paths can independently:

| Action              | Description                                                                 | Trigger Examples                          |
|---------------------|-----------------------------------------------------------------------------|-------------------------------------------|
| Slide               | Shift position while maintaining connectivity                               | Threat approaches a corridor              |
| Rotate              | Change orientation of a junction                                            | Multiple escape vectors detected          |
| Expand / Contract   | Increase or decrease the size of a region                                   | Need to create pressure or open a trap    |
| Seal                | Permanently or temporarily remove an edge                                   | Threat has passed; prevent backtracking   |
| Spawn               | Create new temporary walls or false paths                                   | Distract or over-constrain the Minotaur   |
| Dissolve            | Remove a wall to open a controlled path toward the Center                   | Herding phase                             |
| Harden              | Increase resistance / cost of traversal                                     | Repeated probing of the same wall         |

All movements are purposeful. Randomness is only used when it serves deception.

---

## 2. Detection & Threat Scoring

The Perception Layer continuously evaluates entities using:

- Behavioral signals (unusual process trees, lateral movement patterns, privilege escalation attempts)
- Network anomalies
- Memory and file system interactions
- Deviation from learned normal baselines

Each potential threat receives a **Minotaur Score** (0.0 – 1.0).

- Below threshold → ignored or lightly monitored
- Above threshold → becomes an active Minotaur and the hunt begins

Once active, the Labyrinth switches from passive observation to active herding.

---

## 3. Herding Logic

The primary goal of the Topology Engine is to reduce the Minotaur’s available options while increasing the gravitational pull toward the **Center** (Kill Zone).

### Herding Principles
1. **Never leave an open escape route** once the hunt has started.
2. **Always maintain at least one path** that leads deeper toward the Center (the “funnel”).
3. **Increase cost** of any path that leads away from the Center.
4. **Predict** short-term movement and pre-seal likely escape corridors.
5. **Apply pressure** — the Minotaur should feel the walls closing even when it is not yet trapped.

The system treats the Minotaur as an adversarial agent trying to maximize survival and reach. The Labyrinth is the opposing agent that continuously rewrites the graph to minimize the Minotaur’s utility.

---

## 4. The Kill Zone (Center)

When the Minotaur is forced into the designated Center node(s):

1. **Isolation** — All external edges are severed. No new connections can be formed.
2. **Containment Snapshot** — Forensic state is captured (memory, process tree, network context).
3. **Destruction Sequence**:
   - Process termination
   - Memory space cryptographic shredding
   - Behavioral signature extraction for future learning
   - Controlled restoration of any legitimate resources that were temporarily isolated
4. **Confirmation** — The system verifies the Minotaur no longer exists in any residual form.

Only after confirmation does the Labyrinth begin to relax the surrounding topology.

---

## 5. Rules of Adaptation (Evolution Loop)

After every engagement (successful or failed):

1. **Replay** the topology changes and Minotaur decisions.
2. **Score** each major decision the Labyrinth made:
   - Did it reduce escape options effectively?
   - Did it cause unnecessary disruption to legitimate activity?
   - How quickly was the Center reached?
3. **Reinforce** high-performing strategies.
4. **Penalize or discard** low-performing or overly disruptive strategies.
5. **Update** prediction models and default herding policies.

Over time the Labyrinth develops specialized responses for different classes of Minotaur (ransomware, APTs, fileless threats, etc.).

---

## 6. Hard Constraints

- Legitimate traffic and processes must never be permanently trapped or destroyed.
- The system must always retain a way to reverse temporary restrictions on trusted entities.
- Human operators must be able to observe, pause, or override the Labyrinth at any time.
- All destructive actions in the Kill Zone require high-confidence classification.

---

## Status

This is the foundational mechanics specification. It will be refined as we build simulations and prototypes.
