# 🧠 Multi-Service AI Assistant with LangChain

This project is a smart AI assistant that can answer **math** and **weather** queries by communicating with separate services (servers). It uses [LangChain](https://www.langchain.com/), [LangGraph](https://github.com/langchain-ai/langgraph), and [Groq](https://console.groq.com/) to build an agent that intelligently routes user queries to the correct tool (e.g., calculator or weather service).

---

## 📂 Project Structure

mcp_server/
├── client.py # Main file to run the AI assistant
├── mathserver.py # Local math computation service
├── weather.py # Weather server (runs HTTP API)
├── .env # Environment file for storing GROQ_API_KEY
├── requirements.txt # All required dependencies
├── pyproject.toml # Optional: Project metadata for poetry or pip
├── uv.lock # Optional: Exact dependency lock file
└── README.md # 📖 You're reading it now!


---

## 🚀 Features

- 🤖 Uses an LLM agent to route questions
- 🧮 Handles math questions via a local subprocess (mathserver)
- 🌦️ Handles weather queries via an HTTP service (weather server)
- ⚙️ Asynchronous, multi-tool compatible using `langchain_mcp_adapters`
- 🔑 Secure API access using `.env` for API keys (e.g., Groq)

---

## 📦 Requirements

- Python 3.9+
- `pip` or `poetry` (optional)
- Internet access (for LLM calls)

---

## 📥 Installation

### 1. Clone the Repository

```bash
git clone https://github.com/Anandhu-p-tec/mcp-multitool-agent.git
cd mcp_server

```
### 2. Create Virtual Environment
```
python -m venv mcp_server
source mcp_server/bin/activate  # Mac/Linux
mcp_server\Scripts\activate     # Windows
```
### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 🔐 Environment Variables
Create a .env file in the project root:

env
GROQ_API_KEY=your_actual_groq_api_key

You can get a free key from https://console.groq.com

### ▶️ How to Run the Project
Open three terminals: one for the math server, one for the weather server, and one for the AI client.

### 1. Start Weather Server
```bash
python weather.py
This will start a local HTTP API on:
http://127.0.0.1:8000/mcp
```

### 2. Start Math Server
```bash
python mathserver.py
This is a simple script that evaluates math expressions passed through standard input/output.
```

### 3. Run the AI Client
```bash

python client.py
```
Expected Output:


🧮 Math Response: The answer is 96
🌦️ Weather Response: It's currently sunny in California with 25°C

### 🧠 How It Works
client.py loads your environment, connects to both the weather and math services.

It uses langchain_mcp_adapters to connect tools as MultiServerMCPClient.

The create_react_agent function builds an AI agent that understands questions and routes them to:

mathserver.py if it's a math question.

weather.py if it's a weather question.




