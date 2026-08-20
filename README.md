# Dev-Learning-Journal

## Contents
- [LLM - RAG Pipeline](#llm---rag-pipeline)
- [ML - Churn Prediction](#ml---churn-prediction)

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

---

### ML - Churn Prediction

#### 1. Get the Data

- Dataset: Telco Customer Churn

#### 2. Data Preparation

- Download the data and read it with Pandas.
- Look at the data.
- Make column names and values consistent and uniform.
- Check that all columns were read correctly.
- Check whether the `churn` variable needs any preparation.

#### 3. Setting Up the Validation Framework

- Perform the train/validation/test split using Scikit-Learn.
- Keep the validation framework consistent so models can be compared fairly.

#### 4. Exploratory Data Analysis (EDA)

- Check for missing values.
- Look at the target variable (`churn`).
- Examine numerical variables.
- Examine categorical variables.
- Understand the distribution and characteristics of the data before modeling.

#### 5. Feature Importance: Churn Rate & Risk Ratio

Feature importance analysis is part of EDA. It helps identify which features are associated with the target variable.

- **Churn rate**
  - Percentage of customers who churn.
  - Can be calculated for different groups/categories.
- **Risk ratio**
  - Compares the churn rate of a group with the overall churn rate.
  - Helps identify groups with higher or lower churn risk.
- **Mutual information**
  - Covered later.

#### 6. Feature Importance: Mutual Information

**Mutual information** is a concept from information theory.

It tells us how much we can learn about one variable if we know the value of another variable.

- Measures the relationship between a feature and the target.
- Can be used to identify categorical variables that contain useful information about churn.
- Higher mutual information generally indicates a stronger dependency between the variables.

#### 7. Feature Importance: Correlation

- Measure the correlation between numerical features and the target variable.
- Understand whether variables have a positive or negative relationship with churn.
- Use correlation to identify potentially useful features and relationships between numerical variables.


