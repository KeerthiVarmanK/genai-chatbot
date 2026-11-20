# 🤖 Gen AI Chatbot

A conversational AI chatbot built using **Python, Streamlit, LangChain, and Groq API**. It allows users to interact with an AI assistant through a simple and user-friendly chat interface.

## 🚀 Features

- Interactive chatbot interface using Streamlit.
- Powered by Groq's LLM API.
- Uses LangChain's `ChatGroq` integration.
- Maintains conversation history using Streamlit session state.
- Secure API key configuration using environment variables.
- Real-time AI-generated responses.

## 🛠️ Technologies Used

- Python
- Streamlit
- LangChain
- LangChain-Groq
- Groq API
- Python Dotenv

## 📂 Project Structure

```text
genai-chatbot/
│
├── app.py
├── requirements.txt
├── render.yaml
├── .env
├── .gitignore
└── README.md
```

## ⚙️ Installation and Setup

### 1. Clone the repository

```bash
git clone https://github.com/KeerthiVarmanK/genai-chatbot.git
cd genai-chatbot
```

### 2. Create a virtual environment

```bash
python -m venv venv
```

Activate it:

**Windows:**
```bash
venv\Scripts\activate
```

**Mac/Linux:**
```bash
source venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure the Groq API key

Create a `.env` file in the project root:

```env
GROQ_API_KEY=your_groq_api_key
```

Get your API key from [Groq Console](https://console.groq.com/).

### 5. Run the application

```bash
streamlit run app.py
```

The application will open in your browser.

## 🌐 Deployment

This application is deployed using **Render**.

- Build command: `pip install -r requirements.txt`
- Start command: `streamlit run app.py --server.port $PORT --server.address 0.0.0.0`
- Environment variable: `GROQ_API_KEY`

Configure your Groq API key in Render's Environment settings. Do not upload your `.env` file or API key to GitHub.

## 🧠 Model Configuration

The chatbot uses the following Groq model:

```python
model="openai/gpt-oss-120b"
```

## 👨‍💻 Author

**Keerthi Varman K**

GitHub: [KeerthiVarmanK](https://github.com/KeerthiVarmanK)