# Agent Knowledge and Applications

## 🤖 Table of Contents

- [Agentic AI Design Patterns & Architectures](#agentic-ai-design-patterns--architectures)
  - [1. Core Cognitive Patterns](#1-core-cognitive-patterns)
  - [2. Multi-Agent Coordination](#2-multi-agent-coordination)
  - [3. Levels of Autonomy](#3-levels-of-autonomy)
  - [4. Theoretical Archetypes](#4-theoretical-archetypes)
- [Agent Concepts](#agent-concepts)  
  - [1. Routing (Hand-off)](#1-routing-hand-off)  
  - [2. Guardrails](#2-guardrails)  
  - [3. Flow Agent](#3-flow-agent)  
  - [4. AI Gateway](#4-ai-gateway)  
  - [5. Tracing](#5-tracing)  
  - [6. Streaming](#6-streaming)  
  - [7. Parallelization](#7-parallelization)  
  - [8. Human-in-the-loop](#8-human-in-the-loop)
- [System Monitoring, Audit & Feedback](#system-monitoring-audit--feedback)
  - [1. Logging & Tracing](#1-logging--tracing)
  - [2. Alerting](#2-alerting)
  - [3. Evaluation / Red Team](#3-evaluation--red-team)
  - [4. Incident Response](#4-incident-response)
  - [5. Feedback Loop / Continuous Improvement](#5-feedback-loop--continuous-improvement)
- [Security in Agentic AI](#security-in-agentic-ai)
- [MCP (Model Context Protocol)](#mcp-model-context-protocol)
- [Agent2Agent (A2A) Protocol](#agent2agent-a2a-protocol)
- [ACP (Agent Communication Protocol)](#acp-agent-communication-protocol)
- [Retrieval-Augmented Generation (RAG)](#retrieval-augmented-generation-rag)  
  - [1. Create chunks](#1-create-chunks)  
  - [2. Generate embeddings](#2-generate-embeddings)  
  - [3. Store embeddings in a vector database](#3-store-embeddings-in-a-vector-database)  
  - [4. User input query](#4-user-input-query)  
  - [5. Embed the query](#5-embed-the-query)  
  - [6. Retrieve similar chunks](#6-retrieve-similar-chunks)  
  - [7. Re-rank the chunks](#7-re-rank-the-chunks)  
  - [8. Chunking Methods](#8-chunking-methods)  
  - [9. Retrieval Techniques](#9-retrieval-techniques)  
  - [10. Cross-encoder and Bi-encoder](#10-cross-encoder-and-bi-encoder)  
  - [11. Graph RAG](#11-graph-rag)

---

## Agentic AI Design Patterns & Architectures

Designing and categorizing AI Agents in real-world systems goes beyond a few standalone models. It expands across multiple dimensions: from internal cognitive processes and system coordination to levels of autonomy.

### 1. Core Cognitive Patterns
Defines how a single Agent thinks, makes decisions, and interacts with its environment.

* **ReAct (Reason and Act):** The core loop: *Thought -> Action -> Observation*. Enables the Agent to dynamically combine logical reasoning with real-world execution.
    <br><img src="images/react.png" width="40%" alt="ReAct Pattern">
* **Tool Use / Function Calling:** Recognizes context to automatically extract parameters and trigger external APIs, databases, or Sandbox environments.
    <br><img src="images/tool.png" width="40%" alt="Tool Use Pattern">
* **Reflection / Self-Correction:** The Agent acts as its own "critic," reviewing for errors and refining the output quality before responding to the user.
    <br><img src="images/reflection.png" width="40%" alt="Reflection Pattern">
* **Planning (Plan-and-Solve):** Deconstructs large, complex goals into manageable sub-tasks, creates a roadmap, and proactively adjusts the plan if errors occur.
    <br><img src="images/planning.png" width="40%" alt="Planning Pattern">
* **Memory-Augmented:** Integrates Short-term memory (Context window) and Long-term memory (Vector DB/Graph) to maintain consistency across extended sessions.

### 2. Multi-Agent Coordination
Dictates how multiple specialized Agents are organized, communicate, and delegate tasks.

<img src="images/multi-agent.png" width="40%" alt="Multi-Agent Pattern">

* **Router (Classifier):** The entry point. Receives the input stream and routes it to the most appropriate specialized Agent or pipeline.
* **Supervisor / Orchestrator:** A central Agent acting as a "manager." It receives the main task, delegates sub-tasks to Worker Agents, and synthesizes the final output.
* **Sequential Workflow:** A linear pipeline where data is automatically passed from one Agent to the next (e.g., *Researcher -> Writer -> Reviewer*).
* **Peer-to-Peer (Conversational):** Agents debate, critique, and collaborate as equals to find the optimal solution.
* **Hierarchical Teams:** A multi-layered tree structure where multiple Supervisors manage different sub-teams, designed for massive-scale systems.

### 3. Levels of Autonomy
Determines the extent of human control and intervention in the Agent's execution loop.

* **Human-in-the-Loop (HITL):** The Agent pauses at sensitive nodes (e.g., payments, deleting data, sending emails) to wait for human approval before proceeding.
* **Fully Autonomous:** Operates entirely independently. Receives the initial goal and runs the execution loop until completion (e.g., AutoGPT).
* **Human-on-the-Loop:** Humans only monitor the process (Observability) and have the authority to intervene or halt the system if necessary, without needing to approve every individual step.

### 4. Theoretical Archetypes
Based on classic AI literature regarding the cognitive capabilities of an Agent.

* **Reflex Agents:** Actions are based purely on rigid *If-Then* rules (Simple Reflex) or local state memory (Model-based Reflex).
* **Goal-Based Agents:** Select sequences of actions aimed at achieving a specific, predefined target state.
* **Utility-Based Agents:** Go beyond just achieving a goal by prioritizing actions that yield the highest "utility score" or efficiency.
* **Learning Agents:** Capable of self-updating and learning from past mistakes to optimize future decision-making processes.

---

## Agent Concepts

### 1. Routing (Hand-off)

Transferring tasks or control between agents to ensure seamless operation and fault tolerance.

<img src="images/router.png" width="60%" alt="model">

### 2. Guardrails

Rules and constraints to keep agents operating safely, ethically, and reliably.

<img src="images/guardrail.png" width="60%" alt="model">

### 3. Flow Agent

Manages the sequence and logic of tasks or conversations within an agent system.

<img src="images/flow.png" width="60%" alt="model">

### 4. AI Gateway

Interface connecting clients to multiple AI services, handling routing, security, and scaling.

<img src="images/gateway.png" width="60%" alt="model">

### 5. Tracing

Logging detailed agent activities for debugging and performance monitoring.

<img src="images/tracing.png" width="50%" alt="model">

### 6. Streaming

Real-time continuous data flow processing between agents or systems.

<img src="images/streaming.png" width="50%" alt="model">

### 7. Parallelization

Splitting tasks to run simultaneously across agents/processors for faster results.

<img src="images/paralle.png" width="60%" alt="model">

### 8. Human-in-the-loop

Involving humans in agent decisions or training for safety and accuracy.

<img src="images/human.png" width="50%" alt="model">

---

## System Monitoring, Audit & Feedback

A critical layer for large-scale, production-ready enterprise Agent systems to ensure reliability, security, and continuous enhancement over time.

### 1. Logging & Tracing
Recording granular system events, state changes, and specific LLM calls to debug complex multi-agent execution paths and monitor token usage.

### 2. Alerting
Automated notifications triggered by predefined thresholds (e.g., high latency, API failure rates, or budget limits) to proactively maintain system health.

### 3. Evaluation / Red Team
Continuous assessment of agent performance and security through adversarial testing (Red Teaming) to identify prompt injection vulnerabilities, hallucinations, and edge cases.

### 4. Incident Response
Standardized protocols, automated fallbacks, and circuit breakers designed to handle critical agent failures or unauthorized actions efficiently in production.

### 5. Feedback Loop / Continuous Improvement
Mechanisms to collect user feedback, human-in-the-loop corrections, and telemetry data to iteratively refine prompts, adjust guardrails, and update underlying models or logic.

---

## Security in Agentic AI

Security is paramount when deploying autonomous agents with access to external tools and data. For a comprehensive collection of vulnerabilities, defense mechanisms, and testing tools, refer to:

👉 **[AWESOME-AI-SECURITY](https://github.com/quaghien/AWESOME-AI-SECURITY)**

**Core Security Focus Areas:**
* **Input Validation:** Treating all external data (prompts, RAG chunks, web results) as untrusted to prevent indirect prompt injection.
* **Access Control:** Enforcing least privilege for tools and implementing strict Human-in-the-loop (HITL) policies for destructive actions.
* **Output Handling:** Sanitizing and escaping agent outputs to prevent downstream execution of malicious payloads (e.g., XSS).
* **Adversarial Testing:** Continuously evaluating the system against jailbreaks, obfuscation techniques, and excessive agency exploits.

## MCP (Model Context Protocol)

The USB-C port equivalent for agentic systems.

<img src="images/mcp.png" width="50%" alt="model">

<img src="images/mcp_contain.png" width="60%" alt="model">

<img src="images/json-rpc.png" width="50%" alt="model">

Transport Mechanisms:

stdio: Communication over standard input/output streams

- The client and server receive JSON messages via stdin and respond via stdout

- Simplifies local process integration and debugging

- Well-suited for local servers like File, Git server, etc.

<img src="images/stdio.png" width="60%" alt="model">

HTTP with Server-Sent Events (SSE):

- Establishes a bidirectional communication pattern over HTTP

- The server maintains an SSE connection for pushing messages to clients

- Clients send commands via standard HTTP POST requests

- Enables distributed architecture with multiple concurrent clients

- Better suited for hosted servers.

<img src="images/sse.png" width="60%" alt="model">

Further Reading on Model Context Protocol (MCP)

To deepen your understanding of the Model Context Protocol (MCP) and its applications, consider exploring the following resources:

- [What is Model Context Protocol (MCP): Explained](https://composio.dev/blog/what-is-model-context-protocol-mcp-explained/)

- [Building an MCP Server from Scratch](https://dshills.medium.com/building-an-mcp-server-from-scratch-432f600b5e68)

## Agent2Agent (A2A) Protocol

- MCP provides agents with access to tools.

- While A2A allows agents to connect with other agents and collaborate in teams.

<img src="images/a2a.png" width="60%" alt="model">

The A2A protocol is built upon established web standards, primarily using JSON-RPC 2.0 over HTTP(S) for request/response interactions and Server-Sent Events (SSE) for streaming.

- A2A-supporting Remote Agents must publish a "JSON Agent Card" detailing their capabilities and authentication.

- Clients use this to find and communicate with the best agent for a task.

<img src="images/a_card.png" width="50%" alt="model">

Example `JSON Agent Card` Structure:
```
{
  "name": "Image Generation Agent",
  "description": "Generates images based on text prompts.",
  "url": "https://api.example-image-agent.com/a2a",
  "version": "1.0.0",
  "capabilities": {
    "streaming": true,
    "pushNotifications": false,
    "stateTransitionHistory": true
  },
  "authentication": {
    "schemes": ["apiKey"]
  },
  "defaultInputModes": ["text"],
  "defaultOutputModes": ["image/png"],
  "skills": [
    {
      "id": "generate_image",
      "name": "Generate Image",
      "description": "Creates an image from a textual description.",
      "inputModes": ["text"],
      "outputModes": ["image/png"],
      "examples": ["Generate an image of a 'blue cat wearing a top hat'"]
    }
  ]
}
```


Further Reading on Agent2Agent (A2A) Protocol

To deepen your understanding of the Agent2Agent (A2A) protocol and its applications, consider exploring the following resources:

- [Building Multi-Agent AI App with Google's A2A Protocol, ADK, and MCP](https://medium.com/ai-cloud-lab/building-multi-agent-ai-app-with-googles-a2a-agent2agent-protocol-adk-and-mcp-a-deep-a94de2237200)

- [What is The Agent2Agent Protocol (A2A) and Why You Must Learn It Now](https://huggingface.co/blog/lynn-mikami/agent2agent)

## ACP (Agent Communication Protocol)

Agent Communication Protocol (ACP) is a more generalized framework for managing structured dialogue between agents. Think of it as the broad umbrella under which other protocols like A2A may reside.

<img src="images/acp.png" width="70%" alt="model">

Key Features of ACP:  

- Message Standardization: Uses speech-act theory (e.g., INFORM, QUERY, REQUEST) to standardize communication.
- Ontology Support: Agents share a common vocabulary, reducing ambiguity.
- Error Handling: Includes robust exception management and message validation.
- Agent Registry Services: Agents can register capabilities and discover others through directory facilitators.

ACP is widely used in environments with heterogeneous AI systems, often orchestrated by an AI agents development company to build scalable, distributed platforms where different agents (like recommendation engines, fraud detectors, and monitoring bots) coexist and collaborate.

MCP vs A2A vs ACP: A Comparative Breakdown

<img src="images/mcp_a2a_acp.png" width="70%" alt="model">

Protocols Compared Side-by-Side:

<img src="images/mcp_a2a_acp2.png" width="60%" alt="model">


Choosing the Right Protocol for Your AI Stack  
When building or scaling an AI agents communication architecture, your choice among MCP, A2A, and ACP depends on your specific needs:

- Choose MCP if your AI agents rely heavily on context, history, and personalized interactions. Ideal for recommendation systems, personalized assistants, or healthcare AI agents.
- Choose A2A for environments requiring distributed decision-making or multi-agent coordination. Best for supply chains, financial systems, or robotic swarms.
- Choose ACP when you need a common language and messaging standard across a wide range of agents, particularly in complex enterprise environments.

For example, a smart hospital system might use MCP for patient context sharing, A2A for real-time coordination between diagnostic bots, and ACP as the overarching communication framework.

Further Reading on Agent Communication Protocol (ACP)

To better understand the Agent Communication Protocol (ACP) and its role in multi-agent systems, explore the following resources:

- [MCP vs A2A vs ACP - Agent Communication Protocols](https://www.bluebash.co/blog/mcp-vs-a2a-vs-acp-agent-communication-protocols/)

- [What Every AI Engineer Should Know About A2A, MCP, and ACP](https://medium.com/@elisowski/what-every-ai-engineer-should-know-about-a2a-mcp-acp-8335a210a742)

# Retrieval-Augmented Generation (RAG)

## Workflow of a RAG System

<img src="images/rag1.png" width="60%" alt="model">

<img src="images/rag2.png" width="60%" alt="model">

### 1. Create chunks

<img src="images/chunk1.png" width="60%" alt="model">

<img src="images/chunk3.png" width="60%" alt="model">

### 2. Generate embeddings

<img src="images/embed1.png" width="60%" alt="model">

### 3. Store embeddings in a vector database

<img src="images/store.png" width="60%" alt="model">

### 4. User input query

<img src="images/input.png" width="60%" alt="model">


### 5. Embed the query

<img src="images/query.png" width="60%" alt="model">

### 6. Retrieve similar chunks

<img src="images/retrival.png" width="60%" alt="model">

<img src="images/retrival2.png" width="60%" alt="model">

### 7. Re-rank the chunks

<img src="images/rerank.png" width="60%" alt="model">

### 8. Chunking Methods

<img src="images/chunk2.png" width="60%" alt="model">

Further Reading on Chunking Strategies for RAG

- [5 Chunking Strategies for RAG](https://blog.dailydoseofds.com/p/5-chunking-strategies-for-rag?ref=dailydoseofds.com)

### 9. Retrieval Techniques

- Keyword Matching (Sparse Vector Search): Uses lexical matching with TF-IDF, BM25.

- Dense Vector Search: Employs transformer-based embeddings for semantic similarity via Approximate Nearest Neighbor (ANN) search in dense vector spaces.

- Hybrid Retrieval: Combines sparse (BM25) and dense (embedding) retrieval to balance precision and recall, enhancing relevance and robustness.

| Feature               | Sparse Vectors                                    | Dense Vectors                                      |
|-----------------------|--------------------------------------------------|---------------------------------------------------|
| Data Representation   | Majority of elements are zero                     | All elements are non-zero                          |
| Computational Efficiency | Generally higher, especially in operations involving zero elements | Lower, as operations are performed on all elements |
| Information Density   | Less dense, focuses on key features               | Highly dense, capturing nuanced relationships     |
| Example Applications  | Text search, Hybrid search                         | RAG, many general machine learning tasks          |

<img src="images/sparse1.png" width="60%" alt="model">

<img src="images/sparse2.png" width="60%" alt="model">

Mixing or fusion

You can mix the results from both dense and sparse vectors, based purely on their relative scores. This is a simple and effective approach, but it doesn’t take into account the semantic similarity between the results. Among the popular mixing methods are:

- Reciprocal Ranked Fusion (RRF)
- Relative Score Fusion (RSF)
- Distribution-Based Score Fusion (DBSF)

<img src="images/search.png" width="60%" alt="model">

Further Reading on Sparse Vectors

- [What is a Sparse Vector? How to Achieve Vector-based Hybrid Search](https://qdrant.tech/articles/sparse-vectors/)

### 10. Cross-encoder and Bi-encoder

Cross-Encoder is a deep learning model that jointly encodes both the query and document to directly assess their relevance by capturing fine-grained interactions between them.

It’s commonly used for re-ranking because:

- It provides higher accuracy by modeling detailed query-document interactions.

- It’s computationally expensive, so it’s applied to a small set of retrieved candidates.

- It improves final result quality by filtering out less relevant items.

<img src="images/cross.png" width="60%" alt="model">

Bi-Encoder independently encodes the query and document into separate embeddings, then measures relevance using similarity metrics like cosine similarity.

It’s often used for initial retrieval because:

- It enables efficient large-scale search by precomputing document embeddings.

- It allows fast approximate nearest neighbor (ANN) search.

- It’s less accurate than cross-encoder but much faster, suitable for filtering large collections before re-ranking.

<img src="images/bi.png" width="60%" alt="model">

### 11. Graph RAG

<img src="images/graph1.png" width="60%" alt="model">

<img src="images/graph2.png" width="60%" alt="model">

<img src="images/graph3.png" width="60%" alt="model">

<img src="images/graph4.png" width="60%" alt="model">
