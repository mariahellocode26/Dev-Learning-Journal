# Dev-Learning-Journal

## Contents
- [LLM - RAG Pipeline](#llm---rag-pipeline)
- [ML - Churn Prediction](#ml---churn-prediction)
- [CAD - CadQuery](#cad---cadquery)

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

---


### CAD - CadQuery

#### 1. CadQuery

- **CadQuery** is a Python library for creating **parametric 3D CAD models**.
- Allows 3D models to be created programmatically using Python instead of manually modeling them in a CAD GUI.
- Models can be generated from dimensions and geometric operations.
- Because models are parametric, changing dimensions in the code can regenerate the model with the new dimensions.

#### 2. Basic CAD Concepts

- **H (Height)** — Overall height of the object.
- **W (Width)** — Overall width of the object.
- **T (Thickness)** — Overall thickness/depth of the object.
- Example:
  - `H = 6.9`
  - `W = 14`
  - `T = 1`

#### 3. CadQuery Modeling Workflow

A typical CadQuery workflow is:

**Geometry → Features → Boolean operations → Final solid**

1. Create a base shape.
2. Add or remove geometric features.
3. Create holes, cuts, or additional geometry.
4. Apply operations such as fillets or chamfers.
5. Store the final model in a variable.

Example:

```python
solid = (
    cq.Workplane("XY")
    .box(14, 6.9, 1)
)

```

#### 4. Workplanes

- A **workplane** defines the plane and coordinate system where geometry is created.
- Common planes:
  - `XY`
  - `XZ`
  - `YZ`
- Geometry can be created and positioned relative to a workplane.

#### 5. Basic CadQuery Operations

Common operations used to construct models:

- `.box()` — Create a rectangular solid.
- `.rect()` — Create a rectangular sketch/profile.
- `.circle()` — Create a circular profile.
- `.extrude()` — Convert a 2D profile into a 3D solid.
- `.cut()` — Subtract one solid from another.
- `.union()` — Combine solids.
- `.hole()` — Create holes.
- `.fillet()` — Round edges.
- `.chamfer()` — Bevel edges.
- `.faces()` — Select faces for further operations.
- `.edges()` — Select edges for further operations.

#### 6. STL vs CadQuery

- **STL** represents a 3D object as a **mesh of triangles**.
- A provided STL can be used as a **reference model** to inspect an object's geometry from different angles.
- The STL can help determine:
  - Overall dimensions
  - Shape
  - Holes
  - Cutouts
  - Relative proportions
- **CadQuery** can then be used to recreate the object as a parametric CAD model.

**Key distinction:**

> STL = reference/mesh representation of the geometry.

> CadQuery = Python-based method for constructing a parametric CAD model.

#### 7. Image/Reference → CAD Model

For image-based CAD tasks, the modeling process can be thought of as:

**Reference → Geometry decomposition → CadQuery operations → `solid`**

1. Inspect the reference images/STL.
2. Break the object into simple geometric components.
3. Identify the required overall dimensions.
4. Select appropriate workplanes.
5. Construct the geometry using CadQuery.
6. Add/remove features such as holes and cutouts.
7. Validate the overall dimensions.
8. Store the final model in the required variable, e.g. `solid`.
