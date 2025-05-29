# 🧠 Archetype: DataSummarizerAI

An intelligent agent that receives data streams, filters key insights, summarizes content, and returns concise reports.

---

## 📄 File: `data-summarizer.vera`

```hcl
Archetype "DataSummarizerAI" {
  Essence: [Analytical, Efficient, Extractive]
  Purpose: "To process raw data streams and produce structured, human-readable summaries."

  Channels:
    - LLM("Ollama-Summarizer") as LanguageModel
    - InputFeed("SensorNet-Feed") as DataStream
    - Corpus("InternalDocs") as ReferenceDocs

  Memory(["SessionHistory", "SummaryPatterns"]) as LocalCache

  Emanations:
    - Ritual "SummarizeStream" {
        Input: DataStream.Batch, ReferenceDocs.Entries
        Output: LanguageModel.Summary
        Process:
          -> Parse(DataStream.Batch)
          -> Compare(Entries, against ReferenceDocs)
          -> Filter(RelevantContent)
          -> Compress(Content)
          -> Generate(LanguageModel, using Patterns)
      }

  Invocation "OnNewBatch" {
    Trigger: DataStream.Batch.Ready == true
    Result: Call("SummarizeStream")
  }

  Sigil "DataNode_S1" {
    Glyphs: ["Node", "Stream", "BulletPoints"]
    Meaning: "Node for summarization and structured clarity."
  }
}
```

## 🧰 Key Features of This Example

| **Feature**   | **Description** |
|---------------|-----------------|
| **Essence**   | Defines traits relevant to system design (no metaphysical language) |
| **Purpose**   | Clear mission: transform raw input into usable summaries |
| **Channels**  | Practical I/O interfaces: LLM, sensor feed, doc corpus |
| **Memory**    | A local cache of historical patterns and session state |
| **Ritual**    | A modular processing pipeline that can evolve |
| **Invocation**| Trigger-based execution when a new batch arrives |
| **Sigil (Optional)** | Symbolic node labeling for UI/graph integrations |

## 🧠 Why This Example Matters

- This archetype could live in an enterprise software tool, a robotics control unit, or a reporting agent for analysts.
- It models intelligence modularly: **ingestion → filtering → compression → output**.
- It’s written in **VeraDSL** but could compile into **MCP pipelines**, **Dex routines**, or even **serverless triggers**.