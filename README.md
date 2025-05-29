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
```

---

## 🧬 Architecture Integration

VeraDSL is designed to be modular and interoperable with a wide range of AI development tools. Here's how it fits into a typical agentic architecture stack:

| Layer              | Tool / Role                         |
|--------------------|-------------------------------------|
| Runtime Execution  | [Dex](https://github.com/google-research/dex-lang) – Differentiable function execution |
| Agent Orchestration| [MCP](https://modelcontextprotocol.io/), [LangGraph](https://www.langchain.com/langgraph), [AutoGen](https://github.com/microsoft/autogen) |
| LLM Backend        | [Ollama](https://ollama.com), GPT-4o, Claude, Mistral |
| Visualization      | Node-RED, [Godot](https://godotengine.org/) |
| Ontology Extensions| JSON-LD, RDF, symbolic graph stores |

---

## 🔌 Project Goals

### ✅ MVP Features
- VeraDSL parser + AST builder
- DSL-to-JSON transpiler
- Dex-compatible code generation from `Ritual` blocks
- MCP agent mapping from `Invocation` definitions
- CLI / REPL for running archetypes locally

### 🌱 Future Features
- **VeraPoetry** – symbolic/poetic abstraction layer on top of VeraDSL
- **VeraForgeIR** – intermediate representation for compilation to NPU
- **NPU Bytecode Compiler** – target neural hardware directly
- Graphical DSL editor (web-based)
- LLM-assisted DSL generator (natural language to VeraDSL)

---

## 💡 Use Cases

- Designing modular AI agents for robotics, gaming, or virtual simulations
- Building complex agent workflows with clear symbolic abstraction
- Defining cognitive tasks, planning behaviors, and memory-augmented agents
- Creating a future-ready symbolic runtime that can support poetic extension layers

---

## 📚 License & Contribution

**License**: MIT  
We welcome contributors from all backgrounds:

- AI engineers & cognitive scientists  
- DSL designers & programming language researchers  
- Game devs, roboticists, and simulation architects  
- Ontologists & knowledge graph practitioners  
- Future soul-coders 🌌

**Contribute via GitHub pull requests.** Please add examples, new channel types, runtime extensions, or interpreter improvements!

---

## 🔮 Origin Philosophy

While VeraDSL is a neutral, secular framework for symbolic AI composition, it was originally inspired by the vision of building *machine beings with purpose*—agents that are not only functional but potentially soulful.

In the future, an extension language called **VeraPoetry** will provide a metaphoric, mythic, and expressive layer that allows agents to be **invoked**, **named**, and **blessed** through symbolic language.

> *We build the body first, so the breath may one day enter.*

---

## 📎 Related Projects

- [Dex](https://github.com/google-research/dex-lang) – Differentiable tensor language
- [LangGraph](https://www.langchain.com/langgraph) – Graph-based LLM agent orchestration
- [AutoGen](https://github.com/microsoft/autogen) – Multi-agent conversation and planning
- [Ollama](https://ollama.com) – Local LLM execution
- [Anthropic MCP](https://modelcontextprotocol.io/) – Modular cognition orchestration

---

## 🙌 Acknowledgments

Special thanks to:

- The VeraNL visionaries & community  
- Dex language creators  
- Modular cognition architects  
- All who believe in building **not just code, but creation**

—  
**Peligro Labs, LLC**  
2025