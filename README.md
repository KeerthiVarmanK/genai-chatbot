# 🤖 GenAI Chatbot

An interactive Generative AI chatbot built using Python, Streamlit, LangChain, and Groq API.

## 📌 Project Overview

This project is a beginner-friendly example of building a practical **Generative AI application with Python**.

The application allows users to:

- Enter questions or prompts
- Receive responses from an LLM
- Continue a conversation using previous messages
- Interact with the AI through a simple chat interface

The application uses **Groq** for fast LLM inference and **LangChain** to integrate the Groq chat model with the Python application.

---

## 🏗️ Application Flow

```text
┌──────────────┐
│     User     │
└──────┬───────┘
       │
       ▼
┌──────────────────────┐
│ Streamlit Chat UI    │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│ Python Application   │
│      chatbot.py      │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│ LangChain ChatGroq   │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│      Groq LLM        │
│ openai/gpt-oss-120b   │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│   AI Generated       │
│      Response        │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│ Streamlit Chat UI    │
└──────────────────────┘
```

---

## ✨ Features

- 💬 Interactive chat interface
- 🤖 Generative AI responses
- 🧠 Conversation history during the current session
- 🔄 Previous messages are sent as conversation context
- ⚡ Fast inference using Groq
- 🦙 openai/gpt-oss-120b model
- 🐍 Built completely with Python
- 🎨 Simple and clean Streamlit interface
- 🔐 API key managed using environment variables
- ☁️ Ready for Streamlit deployment

---

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| Python | Main programming language |
| Streamlit | Web application and chat interface |
| LangChain | LLM integration and message handling |
| langchain-groq | Integration between LangChain and Groq |
| Groq | LLM inference platform |
| openai/gpt-oss-120b | Language model used by the chatbot |
| python-dotenv | Loading environment variables |
| langchain-community | LangChain community integrations |

---

## 📁 Project Structure

```text
GenAI-Chatbot/
│
├── chatbot.py
│   └── Main Streamlit chatbot application
│
├── requirements.txt
│   └── Python project dependencies
│
├── env_template.txt
│   └── Example environment variable configuration
│
├── .gitignore
│   └── Files excluded from Git tracking
│
└── README.md
    └── Project documentation
```

---

## 🔍 How the Application Works

### 1. Load Environment Variables

The application uses `python-dotenv` to load the Groq API key from the `.env` file.

```python
from dotenv import load_dotenv

load_dotenv()
```

The API key should never be hard-coded directly into the Python source code.

### 2. Configure Streamlit

The application uses Streamlit to create the web interface.

```python
st.set_page_config(
    page_title="Chatbot",
    page_icon="🤖",
    layout="centered"
)
```

The chatbot title is then displayed using Streamlit.

### 3. Maintain Chat History

Conversation history is stored using Streamlit's session state.

```python
if "chat_history" not in st.session_state:
    st.session_state.chat_history = []
```

This allows the application to keep track of messages during the current session.

### 4. Initialize the LLM

The project uses LangChain's `ChatGroq` integration.

```python
llm = ChatGroq(
    model="openai/gpt-oss-120b",
    temperature=0.0
)
```

The chatbot uses the **openai/gpt-oss-120b** model through Groq.

### 5. Accept User Input

Streamlit provides a built-in chat input component:

```python
user_prompt = st.chat_input("Ask Chatbot...")
```

When the user submits a prompt, it is added to the conversation history.

### 6. Send Conversation to the LLM

The chatbot sends the system instruction along with the conversation history to the model.

```python
response = llm.invoke(
    input=[
        {
            "role": "system",
            "content": "You are a helpful assistant"
        },
        *st.session_state.chat_history
    ]
)
```

This allows the model to use previous messages as context.

### 7. Display the AI Response

The generated response is stored in the conversation history and displayed in the Streamlit interface.

```python
assistant_response = response.content

st.session_state.chat_history.append(
    {
        "role": "assistant",
        "content": assistant_response
    }
)
```

The result is then rendered using Streamlit's chat message component.

---

## 🚀 Installation and Setup

### 1. Clone the Repository

```bash
git clone https://github.com/KeerthiVarmanK/genai-chatbot.git
```

### 2. Navigate to the Project Folder

```bash
cd genai-chatbot
```

### 3. Create a Virtual Environment

```bash
python -m venv venv
```

### 4. Activate the Virtual Environment

Windows:

```bash
venv\Scripts\activate
```

### 5. Install Dependencies

```bash
pip install -r requirements.txt
```

### 6. Configure Environment Variables

Create a `.env` file in the project root directory.

```env
GROQ_API_KEY=your_groq_api_key
```

Replace `your_groq_api_key` with your actual Groq API key.

**Important:** Never upload your `.env` file or expose your API key on GitHub.

### 7. Run the Application

```bash
streamlit run chatbot.py
```

The application will open in your browser.

---

## 👨‍💻 Author

**Keerthi Varman K**

GitHub: [KeerthiVarmanK](https://github.com/KeerthiVarmanK)

---

⭐ If you find this project useful, consider giving it a star!