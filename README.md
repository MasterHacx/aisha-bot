# Aisha Bot 🤖

A personal Telegram AI assistant with **Groq multi-model support**, **Google Drive integration** (Nexus file system), and **persistent memory**. Built for private use — runs locally, no cloud dependencies.

---

## ✨ Features

| Category | Details |
|---|---|
| **AI Personalities** | `/angel` (polite student) ↔ `/evil` (sassy Hinglish) — instant switch |
| **Multi-Model Brain** | `/chmod` — pick from 6 Groq models (Kimi K2, Llama 4 Maverick, GPT-OSS-120B, Compound, Llama 3.3 70B, Qwen 32B) |
| **Persistent Memory** | Remembers facts across sessions (`memory.json`) — just say "remember that..." |
| **Chat History** | Private history (`/history`, `/delete_history`) + group context awareness |
| **Google Drive (Nexus)** | `/f <query>` search, `/g <file_id>` download, `/s` (reply) upload — resumable, PDF↔Office fallback |
| **Admin Tools** | `/send` broadcast to groups, `/note` share files, `/del_grp_hist` wipe group memory |
| **Smart Replies** | Detects reply/swipe context, keywords, mentions — replies in private always, selective in groups |

---

## 🚀 Quick Start

```bash
git clone https://github.com/MasterHacx/aisha-bot.git
cd aisha-bot
pip install -r requirements.txt
cp .env.example .env
# Edit .env with your tokens
python aisha_bot.py
```

---

## 🔧 Configuration (`.env`)

| Variable | Required | Description |
|---|---|---|
| `TELEGRAM_BOT_TOKEN` | ✅ | From [@BotFather](https://t.me/BotFather) |
| `GROQ_API_KEY` | ✅ | From [Groq Console](https://console.groq.com/keys) |
| `OWNER_ID` | ✅ | Your numeric Telegram user ID |
| `GOOGLE_CREDENTIALS_FILE` | For Drive | Path to OAuth `credentials.json` (Google Cloud Console) |
| `GOOGLE_TOKEN_FILE` | Auto | Stores OAuth token (auto-generated) |
| `GOOGLE_SERVICE_ACCOUNT_FILE` | Alt | Service account JSON (alternative to OAuth) |
| `SEM_6_FOLDER_ID` | Optional | Drive folder ID for Sem 6 notes |
| `AISHAS_FILES_FOLDER_ID` | Optional | Drive folder for uploads |

> **First run:** If using OAuth, the script will open a browser for Google consent. Token saved to `token.json`.

---

## 📋 Commands

| Command | Scope | Description |
|---|---|---|
| `/start` | Private | Welcome |
| `/help` | Private | Full command list |
| `/angel` / `/evil` | Private | Switch persona |
| `/chmod` | Private | Choose AI model (inline buttons) |
| `/history` | Private | Last 10 chats |
| `/delete_history` | Private | Wipe your data |
| `/f <query>` | Private | Search Drive files |
| `/g <file_id>` | Private | Download file to chat |
| `/s` (reply) | Private | Upload replied file to Drive |
| `/getid` | Group | Show group ID |
| `/del_grp_hist` | Group | Clear group memory (admin) |
| `/send` | Private (owner) | Broadcast message to group |
| `/note` | Private (owner) | Share file to group |

---

## 🧠 Memory & Data Files (gitignored)

| File | Purpose |
|---|---|
| `memory.json` | Long-term user facts ("remember that I like coffee") |
| `chat_history.json` | Private conversation history (last 300 per user) |
| `group_chat_history.json` | Group context (last 250 per group) |
| `user_models.json` | Per-user selected Groq model |
| `token.json` | Google OAuth token (auto-refresh) |

---

## 🛡️ Security

- **No secrets in code** — all via `.env`
- **gitignore covers** credentials, tokens, service accounts, runtime data
- **Runs locally** — your data never leaves your machine
- **Owner-only admin commands** — `OWNER_ID` enforced

---

## 📦 Project Structure

```
aisha-bot/
├── aisha_bot.py          # Single-file bot (all logic)
├── requirements.txt      # Python deps
├── .env.example          # Config template
├── .gitignore            # Excludes secrets & runtime data
└── README.md             # This file
```

---

## 👤 Author

**MasterHacx** — [GitHub](https://github.com/MasterHacx)

> *Aisha — your Hinglish-speaking, Drive-connected, memory-keeping Telegram sidekick.*