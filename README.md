# UdaPlay — AI Game Research Agent

An AI-powered research agent for the video game industry. UdaPlay answers natural language questions about video games using a two-tier retrieval system: local knowledge via a ChromaDB vector database, with web search fallback via Tavily.

## Project Structure

```
project/
├── starter/
│   ├── games/                 # 15 JSON files with game metadata
│   ├── lib/                   # Core library modules
│   │   ├── agents.py          # Agent class with state machine workflow
│   │   ├── documents.py       # Document/Corpus data abstractions
│   │   ├── evaluation.py      # Evaluation models and judge logic
│   │   ├── llm.py             # LLM abstraction over OpenAI
│   │   ├── memory.py          # Short-term and long-term memory
│   │   ├── messages.py        # Message types (System, User, AI, Tool)
│   │   ├── parsers.py         # Output parsers (Pydantic, JSON, etc.)
│   │   ├── rag.py             # RAG pipeline with state machine
│   │   ├── state_machine.py   # Generic state machine framework
│   │   ├── tooling.py         # Tool decorator and Tool class
│   │   └── vector_db.py       # VectorStore and VectorStoreManager
│   ├── Udaplay_01_starter_project.ipynb   # Part 1: Build vector DB
│   └── Udaplay_02_starter_project.ipynb   # Part 2: Build agent
├── .env                       # API keys (OPENAI_API_KEY, TAVILY_API_KEY)
├── requirements.txt           # Python dependencies
└── progress.md                # Project progress tracker
```

## Getting Started

### Dependencies

- Python 3.11+
- ChromaDB
- OpenAI API key
- Tavily API key ([free signup](https://app.tavily.com/home))

### Installation

```bash
# Create and activate virtual environment
python -m venv venv
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt
```

### Environment Setup

```bash
# Create .env file with your API keys
OPENAI_API_KEY="your-key"
TAVILY_API_KEY="your-key"
```

## Usage

### Part 1 — Build the Vector Database

Run `starter/Udaplay_01_starter_project.ipynb` to load 15 game JSON files into a persistent ChromaDB collection.

### Part 2 — Run the Agent

Run `starter/Udaplay_02_starter_project.ipynb` to build and invoke the agent with three tools:

1. **retrieve_game** — Semantic search over the vector database
2. **evaluate_retrieval** — LLM-as-judge to assess result quality
3. **game_web_search** — Web search via Tavily API (fallback)

The agent follows a retrieve → evaluate → fallback workflow, produces structured answers with citations, and maintains conversation state across queries.

### Example Queries

```text
"When was Pokémon Gold and Silver released?"
"Which one was the first 3D platformer Mario game?"
"Was Mortal Kombat X released for PlayStation 5?"
```

## Built With

- [ChromaDB](https://www.trychroma.com/) — Vector database
- [OpenAI](https://openai.com/) — Embeddings and LLM
- [Tavily](https://tavily.com/) — Web search API
