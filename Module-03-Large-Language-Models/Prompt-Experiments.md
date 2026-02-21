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


## Week 3 – Day 3

- Diagnosed API key expiration errors
- Compared AI Pipe and AI Proxy request behavior
- Investigated Google Authentication key failures
- Debugged FastAPI deployment errors on Vercel
- Reviewed environment variable configurations
- Tested Week 3 Question 3 submission workflow
- Used Chrome DevTools for debugging
- Analyzed prompt improvements for GA3 Question 11
- Reviewed token usage differences in OpenAPI vs API Pipe
- Explored scraping approach for Discourse API
- Reviewed deployment checklist for Project 1
- Practiced system commands for troubleshooting
- Evaluated GitHub profile presentation


## Week 3 – Day 4

- Made OpenAI API calls using HTTPX
- Sent POST requests with JSON body and headers
- Tested endpoints using curl
- Configured API keys using environment variables
- Updated .bashrc for persistent key storage
- Built chatbot with conversation history
- Implemented system and user role handling
- Generated embeddings for text inputs
- Calculated cosine similarity using NumPy
- Retrieved most similar vectors
- Encoded images to base64 format
- Sent image data to multimodal endpoint
- Extracted product details from image
- Implemented function calling schema
- Defined tool structure and tool_choice
- Extracted manufacturing & expiry date in structured JSON
- Debugged API and schema errors


