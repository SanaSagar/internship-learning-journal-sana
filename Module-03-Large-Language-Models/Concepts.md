## Week 3 – Day 1

### Session Summary

This session introduced advanced Large Language Model (LLM) concepts and their role in building intelligent AI systems. The discussion covered how LLMs work internally, including transformers, tokens, self-attention, context limitations, and embeddings. The session also explored vector databases, Retrieval Augmented Generation (RAG), hybrid retrieval methods, multimodal processing (text, image, audio, video), and production-level application design using tools and agents.
Additionally, the session emphasized structured outputs using schemas, function calling, SQL integration, prompt engineering, evaluation strategies, regression testing, cost optimization, and commercial AI deployment practices.

### Concepts Covered

#### 🔹 Introduction & API Infrastructure
- Overview of Module 3 topics
- Specialized API interaction
- API key management
- Proxy usage for secure access
- Cost awareness in API usage

#### 🔹 How LLMs Work
- Transformers architecture
- Tokens and tokenization
- Self-attention mechanism
- Context window limitations
- Model behavior and scaling

#### 🔹 Embeddings & Semantic Understanding
- Text embeddings
- Multimodal embeddings
- Topic modeling
- Vector representations of text
- Similarity search concepts

#### 🔹 Vector Databases
- Purpose of vector databases
- ChromaDB
- LanceDB
- Typesense
- Storing and retrieving embeddings efficiently

#### 🔹 Retrieval Augmented Generation (RAG)
- RAG architecture
- Context injection
- Hybrid RAG
- Combining retrieval with generation

#### 🔹 Data Encoding & Media Processing
- Base64 (B64) encoding
- Image processing workflows
- Audio processing basics
- Vision models
- Video analysis using frames

#### 🔹 Prompt Engineering & Applications
- Prompt engineering techniques
- Sentiment analysis
- Text extraction
- Function calling
- Travel agent use-case example
- Structured outputs using schemas
- SQL database interaction through LLMs

#### 🔹 Agents & Tools
- Tool usage inside LLM systems
- Agent-based orchestration
- Multi-step reasoning systems

#### 🔹 Evaluation & Testing
- LLM evaluation (LLM eval)
- YAML-based test cases
- Assertions
- Regression testing
- Performance validation
- Cost-effectiveness strategies
- Commercial AI applications

## Week 3 – Day 2

### Session Summary

This session focused on embeddings, vector databases, hybrid RAG architecture, and implementing Project 1 using similarity search. The discussion covered cost-effective embedding models, sentence transformers, OpenAI embeddings, cosine similarity, and vector mathematics concepts. 

The session also explored multimodal embeddings, chunking strategies, environment variable management, asynchronous API calls using HTTPX, and building a question-answering system using embedding-based retrieval. The day concluded with implementing a top-5 similarity search pipeline using NumPy.

---

### Concepts Covered

#### 🔹 Embeddings & Similarity
- Text and image embeddings
- Sentence Transformers
- OpenAI embedding models
- Cost-effective embedding strategies
- Cosine similarity
- Dot product
- Vector norm
- Similarity scoring

#### 🔹 Multimodal Embeddings
- Nomic AI embeddings
- Text + Image similarity
- API key configuration
- JSON-based data exchange
- Python input/output handling

#### 🔹 Vector Databases & Storage
- Storing embeddings in structured format
- chunks.json structure:
  - ID
  - Source
  - Text
  - Embeddings
- Efficient retrieval workflows
- Hybrid RAG overview

#### 🔹 Chunking Strategy
- Why chunking is required
- Token limits and context handling
- Fixed-size vs semantic chunking
- Preparing chunks for embedding

#### 🔹 Environment & Configuration
- Environment variables
- .bashrc configuration
- Secure API key storage
- AI Pipe usage

#### 🔹 Project 1 Implementation
- Embedding-based retrieval system
- Query embedding generation
- Similarity comparison
- Retrieving most relevant chunks
- Cost-performance optimization
