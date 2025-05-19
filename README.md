# Jarvis: Your Personal AI Assistant for Home Automation and Banter

![Python](https://img.shields.io/badge/Python-3.10+-blue)
![License](https://img.shields.io/badge/License-MIT-green)
![Status](https://img.shields.io/badge/Status-Internal%20WIP-orange)

### ⚠️ This is still internal...needs more polishing for before public use...

> **⚠️ WARNING: This project is a work in progress. Use at your own risk.**  
> Please test in a safe environment — not your production smart home — unless you're into chaos.

![Jarvis](https://img.shields.io/badge/Jarvis-Home%20AI%20Assistant-9cf?logo=home-assistant)

> "Yes, sir? Shall I dim the lights and play something dramatic?"  
> — Jarvis, probably

---

## 🧠 What is Jarvis?
Jarvis is a voice-activated AI assistant built to control your smart home, entertain with personality, and evolve with memory. It combines OpenAI's GPT-4-turbo with ElevenLabs TTS, Home Assistant integrations, and long + short term memory to simulate a snarky British AI sidekick that would make Tony Stark proud.

Jarvis lives locally on a server or VM (like on Proxmox) and can:
- Control smart devices via Home Assistant
- Respond to your voice with ElevenLabs speech
- Resume Spotify playlists on demand
- Remember past interactions
- Understand context, wit, sarcasm, and subtlety
- Fall back to local models when needed (planned)

---

## 🚀 Features (Current)

### 🎙️ Wake Word Listener
- Waits in standby until you say "Jarvis"
- Listens for commands in a conversational flow
- Deactivates with phrases like "that's all for now"

### 💡 Home Assistant Integration
- Pulls all entity IDs automatically
- Converts voice commands into Home Assistant service calls
- Supports native actions (e.g. `light.turn_on`, `media_player.play_media`)

### 🔈 Spotify Casting
- Uses the `spotcast.start` service
- Supports playing Spotify playlists on Nest/Hue speakers
- Picks proper `entity_id` and `uri` with natural phrasing

### 🧠 Dual Memory System
- **Short-term memory**: Active chat history in each session
- **Long-term memory**: Vector memory powered by FAISS + OpenAI embeddings
- Remembers what you ask it to ("remember that I like Lo-Fi in the mornings")

### 💬 GPT-4o-turbo Integration
- Uses OpenAI for natural conversation, sarcasm, banter
- Special prompt tuning for wit, brevity, and personality
- Keeps contextual replies based on current and past interactions

### 🔊 ElevenLabs TTS
- Full voice replies with British sarcasm baked in
- Voice output toggle via `.env` with `JARVIS_TTS_ENABLED=false`

### 🧾 Quota Awareness
- Warns when you approach OpenAI or ElevenLabs usage limits

---

## 🛠️ Planned Features
- **Fallback to local LLMs** (Mistral, Phi, etc. via Ollama)
- **Model router**: Automatic switch between GPT-4o and local model based on task
- **Offline mode**: Full local operation during internet outages
- **Voice toggles**: "Jarvis, go mute" or "Jarvis, think locally"
- **System status queries**: "How's my Proxmox cluster doing?"
- **Dockerized deployment**
- **TUI frontend for manual interaction (Textual UI)**

---

## 📦 Requirements
- Python 3.10+
- ElevenLabs API key (for speech)
- OpenAI API key (GPT-4-turbo or GPT-4o)
- Home Assistant instance with API access
- Spotcast installed in HACS for Spotify integration

---

## 🌍 Environment Variables
```
OPENAI_API_KEY=...
OPENAI_MODEL=gpt-4o
OPENAI_ORG_ID=...
ELEVENLABS_API_KEY=...
HOME_ASSISTANT_URL=http://your-hass.local:8123
HOME_ASSISTANT_TOKEN=...
JARVIS_TTS_ENABLED=true
JARVIS_MUTE_INTRO=false
```

---

## 🧠 Voice Flow Example
```
You: "Jarvis!"
Jarvis: "Yes, sir?"
You: "Play my chill playlist in the bedroom."
Jarvis: "Initiating sonic tranquility in your sleep chamber."
[Executes spotcast.start → media_player.bedroom_speaker]

```

---

## 👨‍💻 Dev Notes
- Voice recognition uses Google Speech Recognition
- All prompts are tuned for smart home relevance and sarcasm
- Spotcast casting logic is handled through context injection in the system prompt

---

## 🤝 Credits
- [OpenAI](https://openai.com) for GPT models
- [ElevenLabs](https://elevenlabs.io) for realistic voice
- [Home Assistant](https://www.home-assistant.io/) for smart home control
- [Spotcast](https://github.com/fondberg/spotcast) for Spotify casting
- [Ollama](https://ollama.com) for future local LLM support

---

## 👁️‍🗨️ License
MIT License. Use freely, modify wildly, and build your own Jarvis army.

> "If I had a body, I'd roll my eyes at you right now. Fortunately for us both, I don't."  
> — Jarvis

