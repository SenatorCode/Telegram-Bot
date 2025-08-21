🤖 Telegram Bot Powered by Local LLM (LM Studio)

This project is a Telegram chatbot that connects directly to a local LLM running in LM Studio.
It allows you to interact with open-source models (like TinyLlama, Mistral, etc.) from Telegram in real-time.

✨ Features

✅ Chat with LLM inside Telegram – Ask questions and get responses instantly.
✅ Local-first – No external API keys required; everything runs on your machine.
✅ Supports any GGUF model loaded in LM Studio.
✅ Follows OpenAI-style API (so you can swap in different clients easily).
✅ Custom Commands – Extendable (e.g., /ask, /summary, /ppt).
✅ Secure – Only works with the bot token you generate.

🛠️ How It Works

You send a message in Telegram (e.g., /ask What is gravity?).

The bot receives the message using Telethon / python-telegram-bot.

The bot forwards your text to LM Studio via its local REST API:

http://127.0.0.1:1234/v1/chat/completions


LM Studio runs the model and generates a response.

The bot sends the response back to you in Telegram chat.

Flow diagram:

[ You ] → [ Telegram Bot ] → [ LM Studio API ] → [ Model Response ] → [ You ]

📦 Installation
1. Clone the Repo
git clone https://github.com/yourusername/telegram-llm-bot.git
cd telegram-llm-bot

2. Create Virtual Environment (Optional but Recommended)
python -m venv venv
source venv/bin/activate   # Linux / Mac
venv\Scripts\activate      # Windows

3. Install Dependencies
pip install -r requirements.txt


Dependencies include:

telethon (or python-telegram-bot) – for Telegram integration

requests – to call LM Studio API

python-dotenv – to manage secrets

🔑 Setup
1. Create a Telegram Bot

Open Telegram and search for BotFather.

Run /newbot and follow instructions.

Copy the Bot Token.

2. Configure LM Studio

Open LM Studio.

Load a model (e.g., TinyLlama, Mistral).

Enable the Local Server from settings.

Note the API endpoint (usually http://127.0.0.1:1234).

3. Add Environment Variables

Create a .env file in the project root:

TELEGRAM_API_ID=your_api_id
TELEGRAM_API_HASH=your_api_hash
TELEGRAM_BOT_TOKEN=your_bot_token
LMSTUDIO_URL=http://127.0.0.1:1234/v1/chat/completions
MODEL_NAME=tinyllama-1.1b-chat-v1.0

🚀 Usage

Run the bot with:

python bot.py


Then in Telegram:

/ask Who is Isaac Newton? → Bot replies with LLM output.

/summary <text> → Summarizes text using LLM.

/ppt <topic> (future feature) → Generates a PowerPoint outline.

📂 Project Structure
telegram-llm-bot/
│── bot.py              # Main bot script
│── requirements.txt     # Dependencies
│── README.md            # Project docs
│── .env                 # Secrets (not pushed to GitHub)

🛠️ Roadmap

 Basic Telegram chat integration

 Forwarding messages to LM Studio

 Add /summary feature

 Add /ppt auto-slide generator

 Add conversation memory

 Dockerize for easy deployment

⚠️ Notes

Bot only works if LM Studio server is running.

Ensure LMSTUDIO_URL matches your local server address.

Some models may respond slower depending on hardware.

📜 License

MIT License – feel free to use, modify, and share.
