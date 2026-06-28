<div align="center">

<img src="https://img.shields.io/badge/FocAi-Vision%20Intelligence-8b5cf6?style=for-the-badge&logo=eye&logoColor=white" alt="FocAi" />

# 👁️ FocAi — Conversational Image Recognition Chatbot

**An AI-powered multi-turn chatbot that sees, understands, and converses about any image.**  
Built with Claude claude-sonnet-4-6 Vision API · React · Vanilla CSS

[![Live Demo](https://img.shields.io/badge/Live%20Demo-Try%20FocAi-8b5cf6?style=for-the-badge)](https://github.com/VishalRS2466-maker/FocAi)
[![Built With Claude](https://img.shields.io/badge/Powered%20By-Claude%20claude-sonnet-4--6-6366f1?style=for-the-badge)](https://www.anthropic.com)
[![React](https://img.shields.io/badge/React-18-61DAFB?style=for-the-badge&logo=react)](https://reactjs.org)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)

<br/>

> *"Upload anything. Ask anything. FocAi sees what you mean."*

<br/>

![FocAi Screenshot](https://via.placeholder.com/800x450/0d0b1f/a78bfa?text=FocAi+%E2%80%94+Vision+Intelligence+Chatbot)

</div>

---

## ✨ What is FocAi?

FocAi is a **fully conversational, multi-turn image recognition chatbot** that combines the vision capabilities of Claude claude-sonnet-4-6 with a sleek, intuitive chat interface. Unlike static image analyzers, FocAi **remembers the image across the entire conversation** — you upload once, then ask as many follow-up questions as you want.

Whether you're identifying a plant, debugging an error screen, extracting text from a photo, or turning ingredient photos into recipes — FocAi adapts its intelligence to match your intent.

---

## 🚀 Features

| Feature | Description |
|---|---|
| 🧠 **Multi-turn Memory** | Upload once, ask multiple follow-up questions — FocAi keeps the image in context throughout the session |
| 🔍 **Deep Visual Analysis** | Identifies objects, text (OCR), colors, spatial layout, mood, and context |
| 🍳 **Adaptive Intelligence** | Responds as a chef, tech support agent, botanist, or analyst — based on what you upload |
| 📄 **Text Extraction** | Transcribes and summarizes any text visible in an image |
| 🔧 **Troubleshooting Mode** | Upload error codes or broken items — get step-by-step expert fixes |
| 💬 **Conversational Follow-ups** | Every response ends with a context-aware question to dive deeper |
| 🖱️ **Drag & Drop Upload** | Drag images directly onto the chat interface |
| ✨ **Markdown Rendering** | Responses render with bold, bullets, code blocks, and headers |
| 🌙 **Dark UI** | Sleek deep violet/indigo dark theme built for focus |

---

## 🎯 Use Cases

```
📸 Upload a photo of ingredients  →  Get a step-by-step recipe
🖥️ Upload a screenshot of an error  →  Get expert troubleshooting steps
🌿 Upload a plant or animal  →  Get identification + scientific context
📝 Upload a handwritten note  →  Get transcription + summary
🛒 Upload a product photo  →  Get specs, comparisons, and alternatives
🗺️ Upload a diagram or chart  →  Get explained insights
```

---

## 🛠️ Tech Stack

```
Frontend     →  React 18 (JSX), Vanilla CSS, Google Fonts (Inter + Space Grotesk)
AI Engine    →  Anthropic Claude claude-sonnet-4-6 (Vision + Language)
API          →  Anthropic Messages API (/v1/messages)
Image Input  →  Base64 encoding via FileReader API
State        →  React useState / useRef (no external state library)
Deployment   →  Claude.ai Artifacts (zero-setup, instant live)
```

---

## 🏗️ Architecture

```
User Uploads Image
        │
        ▼
  FileReader API
  (Base64 Encoding)
        │
        ▼
  React State Layer
  (Session Image Memory)
        │
        ▼
  Anthropic /v1/messages
  ┌─────────────────────────┐
  │  System Prompt: FocAi   │
  │  Model: claude-sonnet-4-6│
  │  Vision: image block     │
  │  History: full context   │
  └─────────────────────────┘
        │
        ▼
  Markdown Response Parser
        │
        ▼
  Chat UI (Animated Bubbles)
```

**Key Design Decisions:**
- **Full conversation history** is sent on every API call — enables true multi-turn context
- **Session image persistence** — image base64 stored in React state, attached to every subsequent message
- **System prompt engineering** — FocAi's persona, tone, and behavioral rules are injected as a system-level instruction

---

## 🚦 Getting Started

### Option 1 — Run Instantly (Recommended)
FocAi is built as a **Claude Artifact** (React JSX). To run it instantly:
1. Open [Claude.ai](https://claude.ai)
2. Paste the contents of `FocAi.jsx` into the chat
3. Claude renders it live — no setup, no build step

### Option 2 — Local Development

```bash
# Clone the repo
git clone https://github.com/VishalRS2466-maker/FocAi.git
cd FocAi

# Install dependencies
npm install

# Add your Anthropic API key
echo "VITE_ANTHROPIC_API_KEY=your_key_here" > .env

# Start dev server
npm run dev
```

> ⚠️ **Note:** For production deployments, always proxy Anthropic API calls through a backend server. Never expose API keys in client-side code outside of sandboxed environments.

---

## 📁 Project Structure

```
FocAi/
├── FocAi.jsx          # Main chatbot component (self-contained)
├── README.md          # You are here
└── LICENSE            # MIT License
```

`FocAi.jsx` is intentionally **self-contained** — all styles, logic, and API calls live in one file for maximum portability and easy deployment as a Claude Artifact.

---

## 🧩 How the Vision API Works

FocAi sends images to Claude as **base64-encoded image blocks** alongside the text prompt:

```javascript
{
  role: "user",
  content: [
    {
      type: "image",
      source: {
        type: "base64",
        media_type: "image/jpeg",   // or png, gif, webp
        data: "<base64_string>"
      }
    },
    {
      type: "text",
      text: "What ingredients are in this image?"
    }
  ]
}
```

For multi-turn conversations, the **full message history** (including prior image blocks) is sent on each request, giving FocAi persistent visual memory throughout the session.

---

## 🎨 UI Design Decisions

| Choice | Reasoning |
|---|---|
| Deep violet `#0a0a0f` background | Reduces eye strain; makes image thumbnails pop |
| `Space Grotesk` for the logo | Technical yet distinctive — not a generic sans-serif |
| `Inter` for body text | Optimal readability at small sizes in chat bubbles |
| Animated glowing avatar | Signals AI "thinking" — reinforces the intelligent assistant identity |
| Purple `#8b5cf6` as primary accent | Distinctive in the AI product space; avoids the generic blue |
| Bubble tails (border-radius asymmetry) | Classic chat UX pattern — instantly signals conversation mode |

---

## 🔮 Roadmap

- [ ] Voice input support (Web Speech API)
- [ ] Image comparison mode (upload 2 images, compare side-by-side)
- [ ] Export conversation as PDF
- [ ] Multiple image upload in one message
- [ ] Light mode toggle
- [ ] Mobile-optimized layout
- [ ] History persistence (localStorage)

---

## 👨‍💻 About the Developer

<div align="center">

**Vishal R S**  
*AI/ML Engineer · Aspiring Technical Product Manager*  
B.E. Computer Science & Engineering (AI & ML)  
VSB College of Engineering, Karur · Class of 2029

[![LinkedIn](https://img.shields.io/badge/LinkedIn-vishal--r--s-0077B5?style=flat-square&logo=linkedin)](https://www.linkedin.com/in/vishal-r-s-875002390)
[![GitHub](https://img.shields.io/badge/GitHub-VishalRS2466--maker-181717?style=flat-square&logo=github)](https://github.com/VishalRS2466-maker)
[![Email](https://img.shields.io/badge/Email-vishalrs2466@gmail.com-D14836?style=flat-square&logo=gmail)](mailto:vishalrs2466@gmail.com)

</div>

FocAi is part of a portfolio of AI/ML projects built independently in Year 1 of engineering:

| Project | Description | Stack |
|---|---|---|
| 🤖 [**Mithran**](https://github.com/VishalRS2466-maker/rural-chatbot) | Offline rural AI assistant for government welfare schemes | Python · spaCy · DistilBERT (Quantized) · SQLite |
| 💬 [**Ayra**](https://github.com/VishalRS2466-maker/ayra-chatbot) | Multi-turn conversational AI assistant | Python · NLTK · scikit-learn (SVM) |
| 👁️ **FocAi** *(this repo)* | Conversational image recognition chatbot | React · Claude Vision API |

---

## 📄 License

MIT License — see [LICENSE](LICENSE) for details.

---

<div align="center">

**Built with 🟣 by Vishal R S · Powered by Anthropic Claude**

*If FocAi helped you, give it a ⭐ — it means a lot!*

</div>
