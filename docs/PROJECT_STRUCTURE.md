# Adaptive Labyrinth — Project Structure

**Tagline:** A living maze for digital monsters.

This document defines the current and planned folder structure of the repository.

---

## Current Structure

```
adaptive-labyrinth/
├── README.md
├── docs/
│   ├── IDENTITY.md
│   ├── CONCEPT.md
│   ├── ARCHITECTURE.md
│   ├── CORE_MECHANICS.md
│   ├── THREAT_MODEL.md
│   └── PROJECT_STRUCTURE.md
├── engine/                  # Core Labyrinth logic (future code)
│   ├── topology/              # Topology Engine
│   ├── perception/            # Detection & scoring
│   ├── herding/               # Herding policies & prediction
│   ├── killzone/              # Kill Zone protocols
│   └── evolution/             # Learning & adaptation loop
├── simulation/              # Visual and logical simulations
│   ├── maze/                  # Moving maze prototypes
│   ├── agents/                # Minotaur agent implementations
│   └── scenarios/             # Pre-defined hunt scenarios
├── research/                # Papers, notes, experiments, references
├── prototypes/              # Early experimental code & demos
├── ui/                      # Operator interface & visualization concepts
└── assets/                  # Images, diagrams, concept art
```

---

## Folder Purposes

### `/docs`
All design documents, specifications, and conceptual writing. This is the source of truth for how the Labyrinth is supposed to work.

### `/engine`
The future heart of the system. Will contain the actual implementation of:
- Topology Engine (living graph manipulation)
- Perception Layer
- Herding logic
- Kill Zone execution
- Evolution / learning loop

### `/simulation`
Safe, isolated environments for testing ideas:
- Visual moving-maze demos
- Minotaur agent behaviors
- Full hunt scenario replays

### `/research`
Notes, academic references, threat intelligence summaries, experiment logs, and open questions.

### `/prototypes`
Quick-and-dirty experimental code that may later be promoted into `/engine` or `/simulation`.

### `/ui`
Designs and eventual code for the operator-facing interface — how a human watches and controls the Labyrinth in real time.

### `/assets`
Visual materials: diagrams, concept art, icons, animations.

---

## Status

Structure created. Folders are ready to receive content as we continue building.
