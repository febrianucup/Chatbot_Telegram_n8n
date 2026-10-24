# BIMBO AI Telegram Chatbot (n8n Workflow)

An intelligent tutoring assistant chatbot for Telegram powered by **n8n**, **DeepSeek AI**, and **Google Gemini**, acting as **Mr. Bimbo** — a friendly, patient, and supportive tutoring mentor.

---

## Features

1. **Pedagogical Persona ("Mr. Bimbo")**:
   - Guides students to understand concepts step-by-step rather than giving instant answers.
   - Strictly avoids using terms like "kakak", "kak", or "adik", addressing itself consistently as **Mr. Bimbo**.

2. **Multimodal Capabilities**:
   - **Text Messages**: Answers general inquiries, greets students, and prompts them for study topics.
   - **Photos & Images**: Analyzes attached problem images or screenshots.
   - **Documents & PDFs**: Extracts and analyzes text and problems from uploaded PDFs using Google Gemini.

3. **Memory & Context**:
   - Maintains conversation context per user using an n8n Memory Buffer Window keyed by Telegram Chat ID.

4. **Google Sheets Integration**:
   - Looks up student registration and grades data directly via Google Sheets nodes and tools.

---

## Workflow Structure (`Chatbot Telegram.sanitized.json`)

- **Telegram Trigger**: Receives incoming messages, photos, and documents from Telegram.
- **Message Sorter (Switch/If)**: Routes inputs based on whether they contain text, images, or documents.
- **Google Gemini (Analyze Document)**: Extracts contents and questions from uploaded PDFs or documents.
- **Final Prompt Node**: Combines user messages, image IDs, and extracted document contents into a structured prompt for the AI Agent.
- **AI Agent & LLM (DeepSeek Chat Model)**: Generates pedagogical responses following the Mr. Bimbo system prompt.
- **Simple Memory**: Stores and retrieves recent chat context.
- **Google Sheets Tool**: Allows the agent to query student data and scores on demand.
- **Error Handler**: Gracefully handles runtime issues and provides fallback messages.

---

## Setup & Deployment

1. Import `Chatbot Telegram.sanitized.json` into your **n8n** instance.
2. Configure your credentials:
   - Telegram Bot API Token
   - DeepSeek API
   - Google Gemini (PaLM) API
   - Google Sheets Service Account
3. Update placeholders (such as spreadsheet IDs and server URLs) in the workflow nodes to match your environment.
4. Activate the workflow and test interaction via your Telegram Bot.
