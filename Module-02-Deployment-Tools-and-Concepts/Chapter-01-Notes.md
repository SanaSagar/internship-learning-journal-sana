
## Week 2 – Day 1

### Session Summary
This session introduced the concept of containerization and demonstrated how containers simplify application setup, portability, and deployment. Using Podman within WSL, the instructor walked through multiple hands-on projects, including running Jupyter Lab in a container, deploying a local LLM using Ollama, and connecting multiple containers through networking. The session concluded with building a simple Flask application that communicates with an LLM backend running in a container, along with troubleshooting common WSL networking issues.

### Concepts Covered
- Fundamentals of containerization and its advantages
- Installing and configuring Podman in WSL
- Pulling and running container images
- Managing running containers
- Port binding to access containerized services
- Persisting data using volume mounts
- Running local LLMs (Ollama) inside containers
- Interacting with services inside containers
- Container networking and inter-container communication
- Making API calls between containers
- Building a Flask web application backed by an LLM
- Debugging and resolving WSL networking issues

## Week 2 – Day 2

### Session Summary
This session continued the deep dive into containerization by focusing on practical, multi-container workflows using Podman. The instructor demonstrated how real applications can be split into separate containers and connected through networking. By containerizing Jupyter Lab and a local LLM (Ollama), the session showed how development, AI inference, and web services can run independently yet communicate seamlessly. The day concluded with building a Flask-based application that consumes LLM responses through internal API calls and addressing common WSL networking challenges.

### Concepts Covered
- Revisiting containerization principles through real projects
- Installing and validating Podman in WSL
- Pulling and running application images
- Managing container lifecycle (start, stop, inspect)
- Exposing services using port forwarding
- Persisting notebooks and data via volume mounts
- Running Ollama as a containerized local LLM
- Sending prompts and receiving responses from a containerized LLM
- Creating Podman networks for inter-container communication
- Making API calls between services running in different containers
- Building a Flask application with an LLM backend
- Diagnosing and resolving WSL networking issues


## Week 2 – Day 3

### Session Summary
This live session focused on understanding container technologies and modern deployment workflows. The discussion began with a comparison between containers and virtual machines, followed by differences between Podman and Docker. The session then shifted toward web deployment, covering GitHub Pages for static site hosting and FastAPI for building APIs. Finally, practical deployment strategies were demonstrated using Vercel and ngrok, along with explanations of environment variables, CORS, and deployment limitations.

### Concepts Covered
- Containers vs. Virtual Machines
- Podman vs. Docker comparison
- Hosting static websites using GitHub Pages
- Deploying projects via GitHub Pages
- Introduction to FastAPI framework
- HTTP methods: GET and POST
- API testing using FastAPI interactive docs
- Deploying backend applications with Vercel
- Understanding Vercel limitations (timeouts, constraints)
- Using Vercel CLI for deployment
- Exposing local servers using ngrok
- Managing secrets with environment variables
- Understanding CORS and cross-origin requests

## Week 2 – Day 4

### Session Summary
This session focused on understanding the TDS project workflow and building a production-ready FastAPI server. The instructor explained how to structure projects, handle different types of HTTP requests, validate data using Pydantic models, and implement file upload functionality. The session also covered automated testing using curl, managing secret keys securely, containerizing the application with a Dockerfile, and deploying the project to Hugging Face. The session concluded with best practices for live testing and deployment readiness.

### Concepts Covered
- Overview of TDS project workflow and submission expectations
- Setting up a FastAPI project
- Creating a basic GET endpoint
- Using path parameters and query parameters
- Data validation with Pydantic models
- Structuring response models
- Handling POST requests
- Uploading single and multiple files
- Automated API testing using curl
- Using GitHub Copilot for test case generation
- Managing secret keys securely
- Writing a Dockerfile for deployment
- Deploying FastAPI applications to Hugging Face
- Creating bash scripts for live endpoint testing

