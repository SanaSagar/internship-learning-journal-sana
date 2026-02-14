## Week 3 – Day 1

- Configured API keys securely for LLM access
- Explored proxy-based API routing
- Observed how token limits affect output quality
- Studied self-attention and context handling
- Generated embeddings and analyzed vector similarity
- Understood vector database workflow (ChromaDB, LanceDB)
- Analyzed RAG pipeline architecture
- Compared standard RAG vs Hybrid RAG
- Explored Base64 encoding use cases
- Observed outputs from vision models
- Reviewed video frame-based analysis
- Practiced prompt engineering improvements
- Designed structured schema-based outputs
- Explored function calling workflow
- Reviewed travel agent application example
- Studied agent-tool coordination
- Understood YAML-based LLM testing structure
- Observed regression and assertion-based validation
- Evaluated cost-performance trade-offs

## Week 3 – Day 2  
### Prompt Experiments – Embeddings & Retrieval

### 🔹 Experiment 1: Basic Text Embedding

**Objective:**  
Generate embeddings for sample text and observe vector output structure.

**Input Text:**
"Machine learning enables systems to learn from data."

**Observation:**
- Received high-dimensional numeric vector
- Embeddings represent semantic meaning in vector space
- Similar meaning sentences produce similar vectors

### 🔹 Experiment 2: Cosine Similarity vs Dot Product

**Objective:**  
Compare similarity scoring techniques.

**Steps:**
- Generated embeddings for two similar sentences
- Computed:
  - Cosine similarity
  - Dot product
  - Vector norm

**Observation:**
- Cosine similarity normalizes magnitude
- More stable for semantic comparison
- Dot product influenced by vector magnitude

### 🔹 Experiment 3: Chunking Strategy

**Objective:**  
Split large text into smaller chunks for embedding.

**Approach:**
- Fixed-size chunking
- Stored results in `chunks.json` with:
  - ID
  - Source
  - Text
  - Embedding vector

**Observation:**
- Smaller chunks improve retrieval precision
- Must respect token limits
- Overlapping chunks may improve context retention

### 🔹 Experiment 4: Top-5 Similarity Search

**Objective:**  
Build retrieval pipeline using `ask_question.py`.

**Process:**
1. Convert user query into embedding
2. Load stored chunk embeddings
3. Compute cosine similarity using NumPy
4. Rank results
5. Return top-5 matches

**Tools Used:**
- HTTPX (async API requests)
- NumPy (vector math)
- JSON-safe parsing

**Observation:**
- Top-ranked chunks are semantically related to query
- Async requests improve performance
- Timeout handling is important for reliability

### 🔹 Experiment 5: Multimodal Embeddings

**Objective:**  
Test text-image similarity using multimodal models.

**Tools:**
- Nomic AI embeddings
- API key via environment variables

**Observation:**
- Model can align image and text in same vector space
- Enables cross-modal search

### 🔹 Experiment 6: Cost Optimization

**Objective:**  
Evaluate cost-effective embedding strategies.

**Approach:**
- Compared sentence-transformers vs API-based embeddings
- Measured API usage patterns
- Reduced unnecessary calls


