**Multi-Capable Processing (MCP) Smart Agent**
It is a modular and extensible AI-driven agentic server system that connects specialized agents through a central REST API. These agents can analyze code repositories, fetch external data (like weather), generate text summaries, and remember past interactions using a persistent memory manager.

---

## 🚀 Key Features

- **Multi-Agent Architecture:** Modular design with specialized agents for code analysis, data lookup, and summarization.
- **Tool-Integrated Agents:** Each agent uses tools like GitHub API, weather services, or basic NLP techniques.
- **Memory System:** Keeps a persistent memory of prior tasks for contextual recall.
- **RESTful Server:** Easily integrate with frontends, CLI tools, or workflows via HTTP.
- **Pythonic Structure:** Fully testable and extensible project layout.
- **Ready for Scaling:** You can plug in OpenAI, LangGraph, Vector Databases, and more.

---

## 🗂️ Project Structure

```
mcp-smart-agent/
│
├── agents/                  # AI agents for specific task domains
│   ├── code_agent.py        # Analyzes GitHub repositories
│   ├── data_agent.py        # Fetches weather data
│   └── summary_agent.py     # Summarizes input text
│
├── tools/                   # External service integrations
│   ├── github_tool.py       # Simulates GitHub API access
│   └── weather_tool.py      # Simulates weather data fetch
│
├── memory/
│   └── memory_manager.py    # In-memory key-value storage (can be extended)
│
├── server/
│   └── mcp_server.py        # Flask API endpoints to interact with all agents
│
├── tests/
│   └── test_agents.py       # Unit tests for core functionality
│
├── main.py                  # Entry point to start the server
├── requirements.txt         # Python dependencies
└── README.md                
```

---

## 🧠 How It Works

The system spins up a Flask server that exposes endpoints corresponding to different agents:

### 1. `CodeAgent` (analyze GitHub repo)

- Extracts data from a GitHub-like repository (mocked).
- Returns high-level analysis (e.g., number of files).
- Saves the result in memory.

### 2. `DataAgent` (get weather data)

- Accepts a location input.
- Returns mock weather data (can be connected to OpenWeatherMap, etc.).

### 3. `SummaryAgent` (text summarizer)

- Accepts long text and returns a basic summary.
- You can extend this to use GPT or HuggingFace models.

### 4. `MemoryManager`

- Saves outputs for reuse.
- Supports simple key-value memory (can be upgraded to Redis or vector DB).

---

## 🔌 API Endpoints

| Method | Endpoint             | Description                          |
|--------|----------------------|--------------------------------------|
| POST   | `/analyze_repo`      | Analyze a GitHub repo                |
| POST   | `/get_weather`       | Get mock weather data                |
| POST   | `/summarize`         | Summarize a block of text            |
| POST   | `/retrieve_memory`   | Retrieve stored memory for a task    |

### 🔧 Example Usage

```bash
curl -X POST http://localhost:5000/analyze_repo \
  -H "Content-Type: application/json" \
  -d '{"repo_url": "https://github.com/example/repo"}'
```

---

## 🧪 Testing

Run unit tests with:

```bash
python -m unittest discover tests
```

---

## 🛠 Installation & Run

### Prerequisites

- Python 3.7+
- `pip` installed

### Install dependencies

```bash
pip install -r requirements.txt
```

### Start the server

```bash
python server/mcp_server.py
```

---

##  Ideas for Expansion

- Replace mock tools with real APIs (GitHub, OpenWeather, LangChain tools).
- Use vector databases like Pinecone or ChromaDB for persistent memory.
- Add LangGraph for long-running planning workflows.
- Replace summary agent with GPT-4 or HuggingFace Transformers.
- Add authentication, logging, and rate-limiting.


## 🙋‍♂ Author

Made by Adad — an open-source AI agent framework for rapid prototyping and experimentation.
