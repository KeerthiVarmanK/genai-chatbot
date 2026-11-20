📌 Project Overview
This project is a beginner-friendly example of building a practical Generative AI application with Python.

The application allows users to:

Enter questions or prompts
Receive responses from an LLM
Continue a conversation using previous messages
Interact with the AI through a simple chat interface
The application uses Groq for fast LLM inference and LangChain to integrate the Groq chat model with the Python application.

🏗️ Application Flow
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
│ openai/gpt-oss-120b  │
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
✨ Features
💬 Interactive chat interface
🤖 Generative AI responses
🧠 Conversation history during the current session
🔄 Previous messages are sent as conversation context
⚡ Fast inference using Groq
🦙 openai/gpt-oss-120b model
🐍 Built completely with Python
🎨 Simple and clean Streamlit interface
🔐 API key managed using environment variables
☁️ Ready for Streamlit deployment
🛠️ Technologies Used
Technology	Purpose
Python	Main programming language
Streamlit	Web application and chat interface
LangChain	LLM integration and message handling
langchain-groq	Integration between LangChain and Groq
Groq	LLM inference platform
openai/gpt-oss-120b	Language model used by the chatbot
python-dotenv	Loading environment variables
langchain-community	LangChain community integrations
📁 Project Structure
streamlit-genai-chatbot/
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
└── README.md
    └── Project documentation
🔍 How the Application Works
1. Load Environment Variables
The application uses python-dotenv to load the Groq API key from the .env file.

from dotenv import load_dotenv

load_dotenv()
The API key should never be hard-coded directly into the Python source code.

2. Configure Streamlit
The application uses Streamlit to create the web interface.

st.set_page_config(
    page_title="Chatbot",
    page_icon="🤖",
    layout="centered",
)
The chatbot title is then displayed using Streamlit.

3. Maintain Chat History
Conversation history is stored using Streamlit's session state.

if "chat_history" not in st.session_state:
    st.session_state.chat_history = []
This allows the application to keep track of messages during the current session.

4. Initialize the LLM
The project uses LangChain's ChatGroq integration.

llm = ChatGroq(
    model="llama-3.3-70b-versatile",
    temperature=0.0,
)
The chatbot uses the openai/gpt-oss-120b model through Groq.

5. Accept User Input
Streamlit provides a built-in chat input component:

user_prompt = st.chat_input("Ask Chatbot...")
When the user submits a prompt, it is added to the conversation history.

6. Send Conversation to the LLM
The chatbot sends the system instruction along with the conversation history to the model.

response = llm.invoke(
    input=[
        {
            "role": "system",
            "content": "You are a helpful assistant"
        },
        *st.session_state.chat_history
    ]
)
This allows the model to use previous messages as context.

7. Display the AI Response
The generated response is stored in the conversation history and displayed in the Streamlit interface.

assistant_response = response.content

st.session_state.chat_history.append(
    {
        "role": "assistant",
        "content": assistant_response
    }
)
The result is then rendered using Streamlit's chat message component.
