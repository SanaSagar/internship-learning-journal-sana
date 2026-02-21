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


## Week 3 – Day 3

### Session Summary

This session focused on troubleshooting real-world API and deployment issues while clarifying Project 1 requirements and evaluation criteria. Topics included API key expiration problems, AI Pipe vs AI Proxy differences, Google Authentication (GA2) errors, and FastAPI deployment challenges on Vercel. 

The instructor clarified Project 1 expectations (due June 14), including FastAPI implementation, web scraping, and Discourse API integration. The session also addressed evaluation structure (2x2 scoring system), Week 3 Question 3 submission, Chrome DevTools usage, prompt engineering improvements (GA3 Q11), token usage differences between OpenAPI and API Pipe, and common configuration issues.

Additional discussion included course structure, tool depth, coding background concerns, Linux/OS compatibility, resume building, and project showcase preparation.

### Concepts Covered

#### 🔹 API Troubleshooting
- API key expiration issues (OpenAPI)
- Token limits and usage
- AI Pipe vs AI Proxy comparison
- Handling authentication failures
- Debugging API configuration errors

#### 🔹 Google Authentication Issues (GA2)
- OAuth-related key errors
- Image compression issue in GA2
- Debugging login and authorization flows

#### 🔹 Deployment Issues
- FastAPI deployment challenges on Vercel
- Environment variable misconfiguration
- CORS and server configuration issues
- Debugging failed builds
- Linux/WSL compatibility concerns

#### 🔹 Project 1 Requirements
- Deadline: June 14
- Must include:
  - FastAPI backend
  - Web scraping
  - Discourse API integration
- Deployment requirements
- GitHub repository submission
- Evaluation structure (2x2 scoring system)
- Project prerequisites clarification

#### 🔹 Assignment & Question Clarifications
- Week 3 Question 3 submission guidance
- GA3 Question 11 (Prompt Engineering improvements)
- GA3 Question 7 debugging
- Chrome DevTools for debugging frontend issues
- Configuration issue in Question 6

#### 🔹 Token & API Usage
- Difference between OpenAPI direct usage vs API Pipe
- Token tracking and usage efficiency
- Cost awareness during development

#### 🔹 Course Structure & Career Guidance
- TDS course design philosophy
- Tool depth vs conceptual understanding
- Support for non-coding background students
- Using Discourse forum for queries
- Resume building guidance
- GitHub project showcase importance
- System commands and OS fundamentals
- New laptop setup and compatibility concerns

## Week 3 – Day 4

### Session Summary

This session focused on practical implementation of OpenAI API calls, embedding workflows, multimodal processing, vector similarity search, and function calling. The discussion covered HTTPX-based API requests, chat completion endpoints, base64 encoding, chatbot memory handling, vector database operations, and extracting structured data using function schemas.

The session also explained OpenAI API pricing considerations, usage of GPT-4.1 nano model, different API endpoints, and handling structured JSON outputs. Practical examples included building a chatbot with conversation history and extracting product details (manufacturing and expiry date) from an image using multimodal embeddings.

### Concepts Covered

#### 🔹 OpenAI API & HTTP Requests
- Making API calls using HTTPX
- POST requests with headers
- JSON payload structure
- Using curl commands for testing
- Understanding API URLs and endpoints
- Chat Completion API
- GPT-4.1 nano model usage
- OpenAI pricing awareness
- Different endpoints (chat, embeddings, etc.)

#### 🔹 Environment Setup
- API key configuration
- Using environment variables
- Updating .bashrc file
- Secure key management

#### 🔹 Chatbot Architecture
- System prompt
- User query
- Assistant message
- Roles (system, user, assistant)
- Maintaining conversation history
- LLM memory handling concept

#### 🔹 Word & Vector Embeddings
- Word embeddings and semantic meaning
- Generating embedding vectors
- Vector databases
- Cosine similarity
- Distance calculation
- Retrieving most similar text
- NumPy vector operations
- Ginga API usage overview

#### 🔹 Multimodal Embeddings
- Text + image embeddings
- Converting image to base64
- Sending image data in API request
- Extracting product details from image
- Using different multimodal models

#### 🔹 Base64 Encoding
- Image to Base64 conversion
- Encoding & decoding
- Why base64 is needed for API transmission

#### 🔹 Function Calling
- Function calling workflow
- Function schema definition
- Tools and tool_choice
- Extracting structured data
- Manufacturing date extraction
- Expiry date extraction
- JSON-safe outputs
- Code execution & debugging

#### 🔹 RAG & Vector Retrieval
- Embedding storage
- Similarity comparison
- Retrieving relevant chunks
- Integrating retrieval with chat completion
