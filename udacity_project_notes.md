Project Scenario
You’ve been hired as an AI Engineer at a gaming analytics company developing an assistant called UdaPlay. Executives, analysts, and gamers want to ask natural language questions like:

“Who developed FIFA 21?”
“When was God of War Ragnarok released?”
“What platform was Pokémon Red launched on?”
“What is Rockstar Games working on right now?”
Your agent should:

Attempt to answer the question from internal knowledge (about a pre-loaded list of companies and games)
If the information is not found or confidence is low, search the web
Parse and persist the information in long-term memory
Generate a clean, structured answer/report
Project Specifications
In this project, you will build an AI Research Agent called UdaPlay designed to answer questions about video games. The agent will be capable of:

Answering user questions about games, including:
Game titles and their details
Release dates and platforms
Game descriptions and genres
Publisher information
Using a two-tier information retrieval system:
Primary: RAG (Retrieval Augmented Generation) over a local dataset of games
Secondary: Web search using the Tavily API when internal knowledge is insufficient
Implementing a robust evaluation system:
Assessing the quality of retrieved information
Determining when to fall back to web search
Providing confidence levels in answers
Generating clear, well-structured responses that:
Cite information sources
Combine information from multiple sources when needed
Present information in a natural, readable format

--
Environment Setup

For this project you'll use the following libraries:

chromadb>=1.0.4

openai>=1.73.0

pydantic>=2.11.3

python-dotenv>=1.1.0

tavily-python>=0.5.4

These are installed in the included workspace.
Workspace Instructions
Sign up for a free Tavily account, which will allow you to search the web and get back N pages and textual content for the pages, for free (first 1000 requests are free)

After signing up, you can get your API key here: https://app.tavily.com/home(opens in a new tab)(opens in a new tab)

Create a file named .env in the same directory as the project notebook, and a entries for both OPENAI_API_KEY and TAVILY_API_KEY

e.g.

OPENAI_API_KEY="sk-**********"
TAVILY_API_KEY="tvly-********"
OPENAI_BASE_URL="https://openai.vocareum.com/v1"
Use python-dotenv to load the .env file and ensure the appropriate env variables are set:

# Load in the OpenAI key and Tavily key.
# In the project folder, create a file named 'config.env'
# ensure your config.env file contains:
# OPENAI_API_KEY="your key"
# TAVILY_API_KEY="your key"
# OPENAI_BASE_URL="https://openai.vocareum.com/v1"

from dotenv import load_dotenv
import os

load_dotenv("config.env")

assert os.getenv("OPENAI_API_KEY") is not None
assert os.getenv("TAVILY_API_KEY") is not None

OPENAI_BASE_URL = os.getenv(
    "OPENAI_BASE_URL",
    "https://openai.vocareum.com/v1"
)

---
Part 1 - RAG Pipeline
Set up a ChromaDB vector database
Process and embed game data from JSON files
Implement semantic search functionality
Create a reusable vector store manager

Part 2 - Agent Implementation
Build an agent with three core tools:
retrieve_game: Search the vector database
evaluate_retrieval: Assess answer quality
game_web_search: Fall back to web search
Implement a state machine for agent workflow
Create a reporting system for clear output
Submission Instructions
You will be presented with the opportunity to submit your workspace solution during the final Submit Project step.