# Adaptive Labyrinth — Threat Model & Behavioral Primitives

**Tagline:** A living maze for digital monsters.

This document defines the Minotaur — the abstract adversarial entity the Labyrinth is designed to hunt — and maps real-world threats onto its behavioral primitives.

---

## 1. The Minotaur (Core Abstraction)

The **Minotaur** is not a single piece of malware. It is any entity that:

- Acts with intent to persist, escalate, move laterally, exfiltrate, disrupt, or destroy
- Deviates from established normal behavior in ways that indicate malice or high risk
- Attempts to evade, adapt to, or overcome defensive controls

Once the Perception Layer assigns a sufficiently high Minotaur Score, the entity becomes an **Active Minotaur** and the hunt begins.

### Primary Goals of a Minotaur
1. Survive
2. Expand influence / access
3. Achieve its payload objective (theft, encryption, destruction, persistence, etc.)
4. Evade or disable defenses

The Labyrinth’s opposing goals are to deny all four.

---

## 2. Behavioral Primitives

These are the atomic actions and tendencies the Labyrinth observes and responds to. Every real-world threat is composed of combinations of these primitives.

### Movement & Navigation
- **Lateral Step**: Moves from one node/domain to another
- **Probe**: Tests a wall or edge for weakness / permissiveness
- **Backtrack**: Returns to a previously visited node
- **Spray**: Attempts many paths in parallel or rapid succession
- **Tunnel**: Creates or uses a hidden/covert channel
- **Hide**: Reduces visibility (sleep, inject, fileless, living-off-the-land)

### Persistence & Survival
- **Anchor**: Establishes persistence mechanism
- **Replicate**: Creates copies of itself
- **Mutate**: Changes appearance, signature, or behavior
- **Elevate**: Attempts privilege escalation
- **Disable**: Tries to turn off or impair security controls

### Exploitation & Impact
- **Exploit**: Triggers a vulnerability or misuse of legitimate function
- **Harvest**: Collects credentials, data, or system information
- **Exfiltrate**: Moves data out of the environment
- **Encrypt / Destroy**: Ransomware or wiper behavior
- **Command**: Receives or executes external instructions (C2)

### Social & Deceptive
- **Impersonate**: Mimics legitimate processes or users
- **Distract**: Generates noise or false signals
- **Wait**: Delays activity to avoid temporal detection

---

## 3. Minotaur Classes

The Labyrinth classifies Active Minotaurs into behavioral archetypes. A single campaign may shift between classes.

| Class              | Description                                      | Dominant Primitives                          | Typical Real-World Examples                     |
|--------------------|--------------------------------------------------|----------------------------------------------|-------------------------------------------------|
| **Stalker**        | Slow, stealthy, long-term presence               | Hide, Wait, Probe, Harvest, Tunnel           | APTs, nation-state actors, advanced espionage   |
| **Sprinter**       | Fast, noisy, high-impact                         | Spray, Exploit, Encrypt/Destroy, Replicate   | Ransomware, wipers, opportunistic malware       |
| **Shapeshifter**   | Continuously mutates to evade                    | Mutate, Impersonate, Hide, Elevate           | Polymorphic / metamorphic malware, fileless     |
| **Burrower**       | Deep persistence and living-off-the-land         | Anchor, Hide, Elevate, Command               | Rootkits, firmware threats, LOTL techniques     |
| **Swarm**          | Many coordinated instances                       | Replicate, Spray, Lateral Step, Command      | Botnets, wormable threats, distributed campaigns|
| **Ghost**          | Extremely low visibility, minimal footprint      | Hide, Tunnel, Wait, Harvest                  | Advanced fileless, memory-only, supply-chain    |
| **Berserker**      | Aggressive, destructive, little concern for stealth | Exploit, Destroy, Disable, Spray           | Destructive malware, rogue insiders, sabotage   |

---

## 4. Mapping Real-World Threats

| Real-World Threat Type          | Primary Minotaur Class(es)     | Key Behavioral Primitives Used                          | Labyrinth Response Focus                     |
|---------------------------------|--------------------------------|---------------------------------------------------------|----------------------------------------------|
| Ransomware                      | Sprinter, Shapeshifter         | Spray, Encrypt, Replicate, Disable                      | Rapid funnel + early Kill Zone               |
| APT / Espionage                 | Stalker, Ghost, Burrower       | Hide, Wait, Tunnel, Harvest, Elevate                    | Long-game pressure, deny quiet paths         |
| Wormable Malware                | Swarm, Sprinter                | Replicate, Lateral Step, Spray, Exploit                 | Contain spread, collapse lateral edges       |
| Fileless / LOTL                 | Ghost, Shapeshifter, Burrower  | Hide, Impersonate, Elevate, Command                     | Behavior-first detection, memory focus       |
| Supply Chain Compromise         | Stalker, Ghost                 | Hide, Anchor, Command, Harvest                          | Trust graph analysis, slow herding           |
| Insider Threat (Malicious)      | Stalker, Berserker             | Harvest, Exfiltrate, Disable, Wait                      | Contextual behavior + privilege monitoring   |
| Cryptominer                     | Burrower, Sprinter             | Hide, Anchor, Replicate                                 | Resource anomaly + persistence removal       |
| Wiper / Destructive             | Berserker, Sprinter            | Destroy, Disable, Spray                                 | Emergency isolation + Kill Zone priority     |
| Botnet Agent                    | Swarm                          | Command, Lateral Step, Replicate                        | C2 disruption + swarm collapse               |
| Zero-Day Exploit                | Any (depends on payload)       | Exploit + follow-on primitives                          | Anomaly + rapid topology lockdown            |

---

## 5. Minotaur Lifecycle Inside the Labyrinth

1. **Emergence** — Score crosses threshold → Active Minotaur declared
2. **Awareness** — Labyrinth begins topology pressure
3. **Resistance** — Minotaur attempts to probe, backtrack, mutate, or disable
4. **Compression** — Available paths decrease; funnel toward Center strengthens
5. **Entrapment** — Minotaur enters Kill Zone
6. **Annihilation** — Isolation + destruction sequence
7. **Absorption** — Behavioral lessons integrated into future strategies

---

## 6. Design Implications for the Labyrinth

- Detection must be behavior- primtive-based, not purely signature-based.
- Herding strategies should be class-aware (a Stalker is handled differently from a Sprinter).
- The system must handle class transitions mid-hunt.
- False positives are expensive; high-confidence classification is required before aggressive herding or Kill Zone activation.
- The Labyrinth should become progressively harder for previously seen primitive combinations.

---

## Status

This threat model is living. New primitives and classes will be added as real-world threats evolve and as simulation data provides insight.
