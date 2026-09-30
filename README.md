# 🤖 DevFlow ADK (Agent Development Kit)

[![Python Version](https://shields.io)](https://python.org)
[![AI Backend](https://shields.io)](https://google.dev)
[![License](https://shields.io)](https://opensource.org)

**DevFlow ADK** is a lightweight, local-first **Multi-Agent Development Kit** designed from scratch to completely automate the technical portfolio-building and interview preparation workflow. 

Instead of dealing with a fragmented loop—copy-pasting problems into chatbots, manually refactoring code in an IDE, tracking down similar algorithmic patterns, and running terminal Git commands—DevFlow ADK uses a **decoupled, event-driven sequential cascade architecture** to transform a raw coding question into a production-ready, version-controlled GitHub repository entry in **one click**.

---

## 🌟 Key Core Features & Value

* **Role-Isolated Architecture:** Eliminates context pollution. Each specialized agent (Explainer, Coder, Scout, DevOps) operates inside an isolated system boundary, ensuring clean, predictable outputs.
* **Autonomous Pipeline Cascade:** A centralized state machine passes mutable context variables from one agent turn to the next seamlessly behind the scenes.
* **Zero-Config Tool Registry:** Allows developers to convert standard Python functions into structural JSON execution schemas dynamically using simple decorators.
* **Native Ecosystem Integrations:** Interfaces directly with local environments and invokes the [PyGithub REST API](https://github.com) natively to verify, create, or update remote repository objects.
* **Visual Interface Dashboard:** Features a beautiful, interactive local web application framework built on [Streamlit](https://streamlit.io) to monitor execution latencies, token parameters, and agent handoffs in real-time.

---

## 🏗️ System Architecture & Data Flow

DevFlow ADK replaces bloated AI orchestrators with an explicit runtime engine that handles generation content requests, hooks parameter signatures, and manages asynchronous tool-calling states.

┌──────────────────────────────────────────┐
│        SharedDevelopmentContext          │
│  (Workspace State: Prompts, Code, Repos) │
└────────────────────┬─────────────────────┘
│
▼
┌───────────────┐      ┌──────────────────────────────┐      ┌──────────────┐
│   Developer   │ ───> │        ADKRunner             │ ───> │  Gemini API  │
│ CLI / Web UI  │      │ (Central Event/Reason Loop)  │ <─── │   Backend    │
└───────────────┘      └──────────────┬───────────────┘      └──────────────┘
│
┌──────────────────────┴──────────────────────┐
▼                      ▼                      ▼
┌──────────────────┐   ┌──────────────────┐   ┌──────────────────┐
│  Step 1 Agent    │   │  Step 2 Agent    │   │  Step 4 Agent    │
│(ConceptExplainer)│   │(SoftwareEngineer)│   │  (DevOpsAgent)   │
└──────────────────┘   └──────────────────┘   └──────────┬───────┘
│
▼
┌──────────────────┐
│   GitHub Tool    │
│ (External API)   │
└──────────────────┘


### The 4-Agent Pipeline
1. **`ConceptExplainer`**: Strips out chat filler to provide an institutional logic workflow, edge-case breakdown, and Big-O computational analysis.
2. **`SoftwareEngineer`**: Translates the logical blueprint into production-grade, syntax-highlighted, self-documenting Python source code.
3. **`ResearchScout`**: Identifies 1-2 conceptually matching data structure problems (e.g., LeetCode patterns) to solidify conceptual learning.
4. **`DevOpsAgent`**: Captures outputs, handles filesystem formatting, and calls repository integration tools to commit changes online.

---

## 🛠️ Tech Stack

* **Language & Runtime:** [Python v3.10+](https://python.org)
* **Reasoning AI Engine:** [Official Google GenAI SDK (`google-genai`)](https://pypi.org) + **Gemini 2.5 Flash**
* **Git & Versioning Automation:** [PyGithub Framework](https://pypi.org)
* **Developer Interfaces:** [Streamlit Dashboard Engine](https://streamlit.io) & [Rich Terminal Logger](https://pypi.org)
* **State Management:** Local system OS context + `python-dotenv`

---

## 🚀 Getting Started & Onboarding Flow

### 1. Installation
Clone the repository from GitHub and set up your system dependencies:
```bash
# Clone the repository
git clone https://github.com
cd devflow-adk

# Install dependencies in editable mode
pip install -e .
```

### 2. Configure Environment Keys
Create a local `.env` configuration file in your directory root (use `.env.example` as a template):
```env
GEMINI_API_KEY="AIzaSyYourGeminiStudioTokenHere"
GITHUB_TOKEN="ghp_YourPersonalGitHubAccessTokenHere"
```

### 3. Launch the Application Workflow
Fire up the local visual dashboard engine immediately using the built-in app server:
```bash
streamlit run app/ui.py
```
This automatically initiates a browser node at `http://localhost:8501`, giving you full visual control over the multi-agent workspace.

---

## 🤝 Contribution & Extension Guardrails
DevFlow ADK was designed to maximize extensibility. To register custom tool functionalities to the pipeline agents, use the native application decorator setup:

```python
from adk.core import CustomADK

app = CustomADK()

@app.tool()
def my_custom_local_verifier(file_path: str) -> str:
    """
    Automates standard checks on generated python code structures.
    """
    # Custom business logic goes here...
    return "Verification Successful"
```

---

## 📄 License
Distributed under the MIT License. See `LICENSE` for more details.