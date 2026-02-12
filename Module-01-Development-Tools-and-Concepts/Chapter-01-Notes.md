# Chapter 01 – Introduction to Development Tools & Internship Workflow

## Week 1 – Day 1

### Session Summary
This introductory session provided an overview of the Tools in Data Science (TDS) course. The session explained how the course is structured, how assignments will be submitted, and what skills are expected to be developed by the end of the program. It also emphasized the importance of hands-on projects, collaboration, and building job-ready skills. Towards the end, the session introduced the Windows Subsystem for Linux (WSL) and demonstrated the initial steps for setting it up.

### Concepts Covered
- Difference between Course Portal and Seek Portal
- Assignment submission and grading process
- Course prerequisites for students from different backgrounds
- Foundational tools and core technical concepts
- Importance of APIs in modern development
- Role of deployment and real-world skills
- Project-based learning and group collaboration
- Understanding course difficulty and expectations
- Student Q&A and common concerns
- Introduction to teaching assistants and support structure
- Overview of Windows Subsystem for Linux (WSL)
- Step-by-step guidance for starting WSL installation


## Week 1 – Day 2

### Session Summary
This session focused on setting up a Linux development environment using Windows Subsystem for Linux (WSL). A complete walkthrough of installing WSL and Ubuntu was demonstrated, along with common issues faced during setup and how to resolve them. The session also introduced Git and explained how version control fits into the overall development workflow.

### Concepts Covered
- Overview of terminals and command-line interfaces
- What WSL is and why it is used
- Comparison between WSL and VirtualBox
- Step-by-step WSL installation process
- Enabling Windows features required for WSL
- Installing Ubuntu on WSL
- Navigating files and folders inside WSL
- Handling common issues during setup
- Reinstalling Ubuntu after password issues
- Basics of Git and version control
- Understanding Git and GitHub workflow
- Introduction to repositories and commits
- Discussion on GitHub usage policies and learning roadmap


## Week 1 – Day 3

### Session Summary
This session introduced the use of WSL (Windows Subsystem for Linux) and focused on understanding how Linux works within a Windows environment. The session explained the Linux file system, basic navigation using command-line tools, and the differences between Linux and Windows file structures. It also covered setting up development tools that allow interaction with AI models directly from the terminal.

### Concepts Covered
- Overview of WSL and how Linux runs on Windows
- Basic understanding of system boot process
- Introduction to hypervisors and virtualization
- Navigating the Ubuntu file system using terminal
- Absolute paths vs relative paths in Linux
- Key Linux directories and their purpose
- Differences between Linux and Windows file systems
- Importance of learning command-line tools
- Integrating VS Code terminal with WSL
- Installing and configuring UV tool
- Installing and using LLM tools via UV
- Setting up API keys for AI model access
- Using terminal commands to interact with GPT and Gemini models


## Week 1 – Day 4

### Session Summary
This session focused on setting up a complete development environment for effective project work. It covered the installation and configuration of essential tools used in real-world development workflows, with emphasis on command-line usage and environment management. The session also demonstrated how different tools work together to streamline development and project setup.

### Concepts Covered
- Installing and configuring Visual Studio Code
- Using package managers for tool installation
- Setting up Git and GitHub from the terminal
- Managing Python versions for different projects
- Understanding project-specific environment configuration
- Introduction to command-line tools for AI and LLM usage

### Additional Notes
- Proper environment setup helps avoid dependency and version conflicts
- Command-line tools provide better control and automation
- Tool configuration is an important part of professional development workflow


## Week 1 – Day 5

### Session Summary
This session focused on setting up Git and GitHub properly for the course and understanding how version control will be used throughout the internship. The trainer explained how assignments can be managed, how repositories are created, and how GitHub helps in tracking progress. A major part of the session involved configuring SSH keys to securely connect the local system with GitHub and troubleshooting common issues faced while pushing code.

### Concepts Covered
- Understanding course workflow and assignment expectations
- Installing and configuring Git
- Creating repositories and files on GitHub
- Difference between HTTPS and SSH cloning
- Generating and adding SSH keys to GitHub
- Cloning repositories using SSH
- Adding files and committing changes locally
- Fixing permission and push-related errors
- Why Linux / WSL is preferred for development
- Brief overview of Python environments using UV
- Introduction to GitHub Copilot

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



