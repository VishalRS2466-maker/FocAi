# FocAi
<div align="center">

<br/>

```
███████╗ ██████╗  ██████╗ █████╗ ██╗
██╔════╝██╔═══██╗██╔════╝██╔══██╗██║
█████╗  ██║   ██║██║     ███████║██║
██╔══╝  ██║   ██║██║     ██╔══██║██║
██║     ╚██████╔╝╚██████╗██║  ██║██║
╚═╝      ╚═════╝  ╚═════╝╚═╝  ╚═╝╚═╝
```

### 👁️ Conversational Image Recognition Chatbot

<br/>

[![React](https://img.shields.io/badge/React-18-61DAFB?style=for-the-badge&logo=react&logoColor=black)](https://reactjs.org)
[![Claude](https://img.shields.io/badge/Claude-claude--sonnet--4--6-8b5cf6?style=for-the-badge)](https://anthropic.com)
[![Vision API](https://img.shields.io/badge/Vision-API-6366f1?style=for-the-badge&logo=eye&logoColor=white)](https://anthropic.com)
[![License](https://img.shields.io/badge/License-MIT-22c55e?style=for-the-badge)](LICENSE)

<br/>

> *"Upload anything. Ask anything. FocAi sees what you mean."*

<br/>

---

</div>

## 👁️ What is FocAi?

FocAi is a **fully conversational, multi-turn image recognition chatbot** that combines Claude claude-sonnet-4-6's vision capabilities with a sleek chat interface. Unlike static image analyzers, FocAi **remembers the image across the entire conversation** — upload once, then ask unlimited follow-up questions.

Whether you're identifying a plant, debugging an error screen, extracting text from a photo, or turning ingredient photos into recipes — FocAi adapts its intelligence to match your intent.

---

## 🎯 Use Cases

```
📸 Upload ingredients photo     →  Get a step-by-step recipe
🖥️ Upload an error screenshot   →  Get expert troubleshooting steps
🌿 Upload a plant or animal     →  Get ID + scientific context
📝 Upload handwritten notes     →  Get transcription + summary
🛒 Upload a product photo       →  Get specs and comparisons
🗺️ Upload a chart or diagram    →  Get explained insights
```

---

## ✨ Features

| Feature | Description |
|---|---|
| 🧠 **Multi-turn Memory** | Image stays in context throughout the session — ask unlimited follow-ups |
| 🔍 **Deep Visual Analysis** | Identifies objects, text (OCR), colors, spatial layout, mood, and intent |
| 🍳 **Adaptive Intelligence** | Responds as chef, tech support, botanist, or analyst — based on what you upload |
| 📄 **Text Extraction** | Transcribes and summarizes any text visible in an image |
| 🔧 **Troubleshooting Mode** | Upload error codes or broken items — get expert step-by-step fixes |
| 💬 **Conversational Follow-ups** | Every response ends with a context-aware question to go deeper |
| 🖱️ **Drag & Drop Upload** | Drop images directly onto the chat interface |
| ✨ **Markdown Rendering** | Responses render with bold, bullets, code blocks, and headers |
| 🌙 **Dark UI** | Deep violet/indigo theme built for focus and clarity |

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
  React State Layer ◄──── Session Image Memory
  (Persists across turns)
        │
        ▼
  Anthropic /v1/messages
  ┌──────────────────────────────┐
  │  System: FocAi Persona       │
  │  Model: claude-sonnet-4-6    │
  │  Content: image + text block │
  │  History: full conversation  │
  └──────────────────────────────┘
        │
        ▼
  Markdown Parser
        │
        ▼
  Animated Chat UI
```

**Key design decisions:**
- **Full conversation history** sent on every API call → true multi-turn context
- **Base64 image persisted** in React state → no re-upload needed between messages
- **System prompt engineering** → FocAi's tone, persona, and analysis rules injected at system level

---

## ⚙️ Tech Stack

| Layer | Technology | Role |
|---|---|---|
| **Frontend** | React 18 (JSX) | UI, state management, chat interface |
| **Styling** | Vanilla CSS + Google Fonts | Zero dependency, full control |
| **AI Model** | Claude claude-sonnet-4-6 (Anthropic) | Vision + language understanding |
| **API** | Anthropic Messages API `/v1/messages` | Multi-modal message handling |
| **Image Processing** | FileReader API (Base64) | Client-side image encoding |
| **Deployment** | Claude.ai Artifacts | Zero-setup instant live demo |

---

## 🚀 Getting Started

### Option 1 — Run Instantly (Recommended)

FocAi is built as a **self-contained React JSX file**. To run it instantly:
1. Open [Claude.ai](https://claude.ai)
2. Paste the contents of `FocAi.jsx` into the chat
3. Claude renders it live — no setup, no build, no config

### Option 2 — Local Development

```bash
# Clone the repository
git clone https://github.com/VishalRS2466-maker/FocAi.git
cd FocAi

# Install dependencies
npm install

# Add your Anthropic API key to .env
echo "VITE_ANTHROPIC_API_KEY=your_key_here" > .env

# Start dev server
npm run dev
```

> ⚠️ **Security note:** For production deployments, always route Anthropic API calls through a backend server. Never expose API keys in client-side bundles.

---

## 📁 Project Structure

```
FocAi/
├── FocAi.jsx        # Complete self-contained chatbot component
├── README.md        # You are here
└── LICENSE          # MIT License
```

`FocAi.jsx` is intentionally **single-file** — all logic, styles, and API calls in one place for maximum portability and easy Artifact deployment.

---

## 🔬 How Vision API Works

FocAi sends images as **base64-encoded image blocks** alongside text prompts:

```javascript
// Single API call — image + text + full conversation history
{
  model: "claude-sonnet-4-6",
  messages: [
    {
      role: "user",
      content: [
        {
          type: "image",
          source: {
            type: "base64",
            media_type: "image/jpeg",
            data: "<base64_string>"
          }
        },
        { type: "text", text: "What can I cook with these ingredients?" }
      ]
    }
  ]
}
```

For multi-turn conversations, the full message history (including prior image blocks) is sent on each request — giving FocAi persistent visual memory throughout the session.

---

## 🗺️ Roadmap

- [ ] Voice input via Web Speech API
- [ ] Side-by-side image comparison mode
- [ ] Export conversation as PDF
- [ ] Multiple image uploads in one message
- [ ] Light mode toggle
- [ ] Mobile-first layout
- [ ] Conversation history persistence

---

## 👨‍💻 Developer

<div align="center">

**Vishal R S**
*AI/ML Engineer · Aspiring Technical Product Manager*
B.E. CSE (AI & ML) · VSB College of Engineering, Karur · Class of 2029

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0077B5?style=flat-square&logo=linkedin)](https://www.linkedin.com/in/vishal-r-s-875002390)
[![GitHub](https://img.shields.io/badge/GitHub-Portfolio-181717?style=flat-square&logo=github)](https://github.com/VishalRS2466-maker)
[![Email](https://img.shields.io/badge/Email-vishalrs2466@gmail.com-D14836?style=flat-square&logo=gmail)](mailto:vishalrs2466@gmail.com)

</div>

### 🗂️ Full Project Portfolio

| Project | Stack | Description |
|---|---|---|
| 🌾 [**Mithran**](https://github.com/VishalRS2466-maker/rural-chatbot) | Python · spaCy · DistilBERT · SQLite | Offline rural AI for welfare scheme navigation |
| 💬 [**Ayra**](https://github.com/VishalRS2466-maker/ayra-chatbot) | Python · NLTK · scikit-learn (SVM) | Multi-turn conversational AI from scratch |
| 👁️ **FocAi** *(this repo)* | React · Claude Vision API | Conversational image recognition chatbot |

---


---

<div align="center">

Powered by Anthropic Claude 

*If FocAi impressed you, give it a ⭐ — it helps more people find it!*
***Built by Vishal R S***
</div>
