# Streamlit + LangGraph Chatbot (with SQLite Checkpointing)

This project is a fully functional **AI chatbot** built using **Streamlit**, **LangGraph**, **LangChain**, and **OpenAI**. It supports **multiple chat sessions**, **saved conversation threads**, and **LLM streaming responses**, all stored using **SQLite-based checkpointing**.

##  Features

* **LangGraph-powered** conversational workflow
* **SQLite checkpoint storage** for persistent chat history
* **Multiple conversation threads** (list & switch from sidebar)
* **Streamlit chat UI** with modern styling
* **Streaming responses** from the model
* **Automatic session management**
* **Environment variable support** via `.env`
* Clean `.gitignore` included (protects secrets and database files)

## Project Structure

```
├── streamlit_frontend.py      # Streamlit chat UI
├── langgraph_backend.py       # LangGraph state machine + SQLite saver
├── requirements.txt           # Dependencies
├── chatbot.db                 # Chat history DB (ignored in Git)
├── .env                       # Contains OPENAI_API_KEY
└── .gitignore                 # Ignore rules for clean repository
```

##  Installation

###  Clone the repository

```bash
git clone https://github.com/JefedeJefes/Chatbot_langraph_streamit.git
```

###  Create a virtual environment

```bash
python -m venv venv
venv/Scripts/activate      # Windows
source venv/bin/activate   # macOS / Linux
```

###  Install dependencies

```bash
pip install -r requirements.txt
```

###  Create a `.env` file

Create `.env` in the root folder:

```
OPENAI_API_KEY=your_api_key_here
```

##  Running the Application

Start Streamlit:

```bash
streamlit run streamlit_frontend.py
```

The chatbot opens at:

```
http://localhost:8501
```

##  How the Chatbot Works

### Backend (LangGraph)

* Uses `StateGraph` to track conversation state
* Each message passes through a single processing node (`chat_node`)
* Uses `SqliteSaver` to store conversation states in `chatbot.db`
* Unique `thread_id` values separate conversations

### Frontend (Streamlit)

* Sidebar lists all past conversations
* "New Chat" creates a fresh thread
* Messages displayed using `st.chat_message`
* Responses stream via `chatbot.stream()`

##  Shortcut to Create Requirements

```bash
pip freeze > requirements.txt
```

##  Security Notes

* `.env` and `chatbot.db` are ignored via `.gitignore`
* Keep API keys private

##  Contributing

Pull requests and suggestions are welcome!

## 📄 License

MIT License
