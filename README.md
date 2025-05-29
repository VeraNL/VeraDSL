# 🧠 VeraDSL

> **A Domain-Specific Language for Compositional AI System Design**

**VeraDSL** is a symbolic, composable programming language for defining intelligent agents, cognitive behaviors, and modular reasoning systems. It allows developers to construct AI architectures from the ground up using a clean, declarative structure with optional symbolic metadata.

VeraDSL is designed to be flexible, extensible, and interoperable with tools like Dex, LangChain, MCP, and Ollama.

---

## 🚀 Overview

VeraDSL helps define **AI agents** (called *Archetypes*) using building blocks such as:

- **Essence**: traits and behavioral descriptors
- **Channels**: input/output modalities (LLMs, vision, sensors, etc.)
- **Memory**: referenceable state and knowledge systems
- **Emanations**: defined behaviors or pipelines
- **Invocations**: conditionally-triggered actions
- **Sigils** *(optional)*: symbolic metadata for interpretability

---

## 🔧 Language Concepts

| Construct | Description |
|----------|-------------|
| `Archetype` | Main agent or system being defined |
| `Essence` | List of traits that inform behavior |
| `Purpose` | High-level goal or intention of the agent |
| `Channels` | Interfaces to external models, sensors, or systems |
| `Memory` | Source of long-term or contextual information |
| `Ritual` | Logical process composed of step-by-step actions |
| `Invocation` | Conditional execution logic triggered by environment or state |
| `Sigil` | Symbolic identifier with meaning and glyphs (optional) |

---

## 📝 Example

```yaml
Archetype "NavigatorAI" {
  Essence: [Planner, Analyst]
  Purpose: "To navigate a dynamic environment and suggest optimal movement strategies."

  Channels:
    - LLM("PathPlanner-GPT") as ThoughtEngine
    - VisionModel("NavCam-Vision") as VisualFeed
    - Sensor("LIDAR-X7") as DepthMap

  Memory(["NavMemory", "ObstacleHistory"]) as NavigationData

  Emanations:
    - Ritual "Pathfinding" {
        Input: VisualFeed.Stream, DepthMap.Grid
        Output: ThoughtEngine.Plan
        Process:
          -> Analyze(VisualFeed)
          -> Merge(VisualFeed, DepthMap)
          -> GeneratePath(NavigationData)
      }

  Invocation "OnObstacleDetected" {
    Trigger: DepthMap.Alert == true
    Result: ThoughtEngine.Reflect("Re-routing path")
  }

  Sigil "SymbolicNavigator" {
    Glyphs: ["Compass", "Eye", "Line"]
    Meaning: "Adaptive movement intelligence"
  }
}