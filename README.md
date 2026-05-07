# Rag-based-Telegram-Interview-ChatBot

# 🤖 Interview Prep Telegram Bot

An AI-powered Telegram bot that generates a complete, structured **Interview Preparation Guide** instantly — just send your job role, company name, and experience level, and the bot does the rest.

Built with **n8n**, **Groq (LLaMA 3.3 70B)**, **Supabase Vector Store**, and **HuggingFace Embeddings** using a RAG (Retrieval-Augmented Generation) architecture.

---

## 📌 What It Does

Send a message like:

> *"I have an interview at TCS for a Python Developer role. I have 1 year of experience."*

The bot will instantly reply with a full **Interview Prep Guide** containing:

- ✅ **10 Technical Questions** — with why they're asked + clear answers
- ✅ **10 HR & Behavioral Questions** — answered using the STAR method
- ✅ **5 Company-Specific Questions** — tailored to the company (if mentioned)
- ✅ **5 Quick Prep Tips** — personalized to your role and experience level

---

## 🧠 How It Works

```
User Message (Telegram)
        ↓
  [Telegram Trigger]
        ↓
  [If Node] ── /start or /help? ──→ (ignored / no response)
        ↓ (any other message)
  [AI Agent]
    ├── LLM: Groq (LLaMA 3.3 70B)
    └── Tool: Supabase Vector Store (RAG)
              └── Embeddings: HuggingFace Inference
        ↓
  [Send Reply to Telegram Chat]
```

### Flow Breakdown

| Step | Node | Purpose |
|------|------|---------|
| 1 | **Telegram Trigger** | Listens for incoming messages |
| 2 | **If Node** | Filters out `/start` and `/help` commands |
| 3 | **AI Agent** | Orchestrates LLM + RAG tool to generate the guide |
| 4 | **Groq Chat Model** | LLaMA 3.3 70B — the brain of the bot |
| 5 | **Supabase Vector Store** | Retrieves relevant questions from the database |
| 6 | **HuggingFace Embeddings** | Converts text into vectors for similarity search |
| 7 | **Send Message** | Sends the formatted guide back to the user |

---

## 🛠️ Tech Stack

| Tool | Role |
|------|------|
| [n8n](https://n8n.io) | Workflow automation platform |
| [Telegram Bot API](https://core.telegram.org/bots/api) | Chat interface |
| [Groq](https://groq.com) | LLM inference — LLaMA 3.3 70B Versatile |
| [Supabase](https://supabase.com) | Vector Store (PostgreSQL + pgvector) |
| [HuggingFace](https://huggingface.co) | Text embedding model (Inference API) |

---

## ⚙️ Setup Instructions

### Prerequisites

- An [n8n](https://n8n.io) instance (cloud or self-hosted)
- A [Telegram Bot Token](https://t.me/BotFather) from BotFather
- A [Groq API Key](https://console.groq.com)
- A [Supabase](https://supabase.com) project with a `interview_questions` table (pgvector enabled)
- A [HuggingFace API Key](https://huggingface.co/settings/tokens)

### Steps

1. **Clone this repository**
   ```bash
   git clone https://github.com/your-username/telegram-interview-prep-bot.git
   ```

2. **Import the workflow into n8n**
   - Open your n8n dashboard
   - Go to **Workflows → Import from File**
   - Upload `Interview_Prep_Telegram_Bot.json`

3. **Set up credentials in n8n**
   - **Telegram API** → Add your Bot Token
   - **Groq API** → Add your Groq API Key
   - **Supabase API** → Add your Supabase URL and Service Key
   - **HuggingFace API** → Add your HuggingFace Inference API Key

4. **Set up Supabase Vector Store**
   - Enable the `pgvector` extension in your Supabase project
   - Create a table named `interview_questions` with vector support
   - Upload your interview question data and generate embeddings

5. **Activate the workflow**
   - Click **Activate** in n8n to start the Telegram webhook

6. **Test it**
   - Open your Telegram bot and send:
     > *"Python Developer at Infosys, fresher level"*

---

## 💬 Example Output (Snippet)

```
INTERVIEW PREP GUIDE FOR: Python Developer at Infosys

ROLE OVERVIEW
A Python Developer at Infosys works on building scalable backend systems...

─────────────────────────
TECHNICAL QUESTIONS
─────────────────────────

*Q1: What are Python's key features that make it popular?*
Why they ask: They want to test your foundational Python knowledge.
Answer: Python is easy to read, has a large library ecosystem, supports multiple paradigms...

...and 9 more Technical Questions
...10 HR & Behavioral Questions
...5 Company-Specific Questions
...5 Quick Prep Tips
```

---

## 📁 Repository Structure

```
📦 telegram-interview-prep-bot
 ┣ 📄 Interview_Prep_Telegram_Bot.json   ← n8n workflow file
 ┗ 📄 README.md
```

---

## 🙋 Author

**Surya**
- B.Tech in Cyber Security | Generative AI Developer
- [LinkedIn](www.linkedin.com/in/suryasrikarpodicheti)

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).
