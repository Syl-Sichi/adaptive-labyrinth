# Adaptive Labyrinth — Architecture Outline

*(This document will evolve rapidly.)*

## Layers

1. **Telemetry & Sensing**
2. **Threat Modeling & Intent Inference**
3. **Topology State Manager**
4. **Herding Policy Engine**
5. **Kill Zone Executor**
6. **Learning & Strategy Store**
7. **Operator Interface / Visualization**

## Core Abstraction: The Living Graph

The protected environment is modeled as a directed graph whose edges and nodes can be:
- Strengthened
- Weakened
- Redirected
- Temporarily removed
- Created on demand

Cost functions on edges are dynamic and threat-aware. The Minotaur is treated as an agent trying to maximize its own survival and lateral reach. The Labyrinth is the opposing agent that continuously rewrites the graph to minimize the Minotaur’s options and drive it to a designated sink node (the Center).

## Open Questions

- How do we represent and manipulate topology at different scales (process, container, host, network, cloud)?
- What is the right balance between aggressive herding and operational disruption?
- How do we prove (or strongly assure) that legitimate traffic is never permanently trapped?
