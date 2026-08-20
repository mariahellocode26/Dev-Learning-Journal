# Dev-Learning-Journal

## Contents
- [LLM - RAG Pipeline](#llm---rag-pipeline)

---

### LLM - RAG Pipeline

#### 1. Data Retrieval

- 1. Data cleaning
- 2. Indexing:
  - Vector search
  - Word search
  - Hybrid search
- 3. Embeddings
  - Numerical representation of semantic meaning.
- 4. Reranking
  - Initial retrieval gets candidates.
  - A reranker reorders those candidates using a stronger relevance model.

#### 2. Building The Prompt

- Context + User input / query
- Prompt engineering:
  - System instructions
  - Grounding
  - Few-shot examples
  - Structured output
  - Context management
  - Prompt injection

#### 3. RAG Pipeline

**RAG = Retrieval → Context → Generation**

1. **Retrieval** — Find the most relevant information.
2. **Context** — Provide the retrieved information to the LLM.
3. **Generation** — The LLM generates an answer based on the available context.

#### 4. Hallucination

A hallucination occurs when:

> The model generates an answer that isn't supported by the available evidence.

In a RAG system, grounding the model in retrieved context helps reduce hallucinations.

#### 5. Evaluation

RAG evaluation can be divided into **retrieval evaluation** and **LLM answer evaluation**.

##### Retrieval Evaluation

Measures whether the retrieval system finds the right documents/chunks.

- **Hit@k**
  - Checks whether the relevant result appears within the top `k` retrieved results.
- **MRR (Mean Reciprocal Rank)**
  - Measures how highly the first relevant result is ranked.
  - Higher MRR means relevant results tend to appear earlier.

##### LLM Answer Evaluation

Measures the quality of the final generated answer.

- **Correctness** — Is the answer factually correct?
- **Groundedness** — Is the answer supported by the retrieved context?
- **Relevance** — Does the answer directly address the user's question?
- **Hallucination rate** — How often does the model generate unsupported information?

**Key distinction:**

> Retrieval evaluation asks: **"Did we find the right information?"**

> LLM answer evaluation asks: **"Did the model use that information to produce a good answer?"**

#### 6. Monitoring



