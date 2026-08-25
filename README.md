# Gemini AI Personal Assistant

A modern, mobile-first bilingual AI personal assistant powered by Google's Gemini API.

The project is designed to provide a fast and responsive AI assistant experience with real-time streaming, multiple conversations, voice features, customizable assistant behavior, model selection, local persistence, and a modular TypeScript architecture.

---

## ✨ Features

### 🤖 AI & Gemini Integrations
- Google Gemini API integration
- Dynamic Gemini model discovery and selection
- Multi-turn conversations and history tracking
- Custom system instructions and multiple assistant personas
- Adjustable temperature control
- Real-time response streaming with generation cancellation
- Built-in error handling and recovery

### 💬 Chat Sessions
- Create, search, and continue multiple conversations
- Automatic session title generation
- Smart session grouping (*Today / Yesterday / Older*)
- Delete and export conversations
- Local conversation persistence via browser storage

### 🎤 Voice Features
- Speech-to-Text (Voice input)
- Text-to-Speech (Voice output controls)
> *Note: Voice functionality depends on browser and device support.*

### 🌐 Bilingual Interface
Supported languages:
- English
- বাংলা (Bengali)

### 🎨 User Interface
- Mobile-first, responsive design with dark mode
- Real-time response streaming and auto-scroll
- Stop-generation and touch-friendly controls
- Notifications and responsive typography

---

## 🖥️ System Architecture

Gemini AI Personal Assistant uses a client-server architecture built around Google Gemini and Vercel.

```text
┌──────────────────────────┐
│       User Device        │
│   Android / iOS / Web    │
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│    TypeScript Frontend   │
│      HTML + CSS + JS     │
└────────────┬─────────────┘
             │
             │ HTTPS / SSE
             ▼
┌──────────────────────────┐
│     Vercel Platform      │
│     API Functions        │
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│      Google Gemini       │
│          API             │
└────────────┬─────────────┘
```

### ⚙️ Core Systems
- **Frontend:** TypeScript, HTML5, CSS3
- **AI Engine:** Google Gemini API
- **Backend:** TypeScript + Vercel API Functions
- **Streaming:** Server-Sent Events (SSE)
- **Storage:** Browser `LocalStorage`
- **Deployment:** GitHub + Vercel

---

## 🏗️ Technology Stack

### Frontend
- TypeScript
- HTML5 / CSS3
- Browser Web APIs
- LocalStorage

### Backend
- Node.js
- TypeScript
- Vercel API Functions
- Google Gemini API

### Deployment & Infrastructure
- GitHub
- Vercel (Serverless Functions)

---

## 📁 Project Structure

```text
ai-assistant/
│
├── api/
│   ├── chat.ts
│   ├── health.ts
│   ├── index.ts
│   └── models.ts
│
├── src/
│   ├── app/
│   │   ├── app.ts
│   │   ├── index.html
│   │   ├── robots.txt
│   │   └── sitemap.xml
│   │
│   ├── components/
│   │   ├── chat-search.ts
│   │   ├── chat-storage.ts
│   │   ├── copy-button.ts
│   │   ├── disclaimer.ts
│   │   ├── message-actions.ts
│   │   ├── model-selector.ts
│   │   ├── new-chat-ui.ts
│   │   ├── sidebar.ts
│   │   └── theme-default.ts
│   │
│   ├── lib/
│   │   ├── chat-scroll.ts
│   │   ├── chat-storage.ts
│   │   ├── markdown.ts
│   │   └── model-config.ts
│   │
│   └── styles/
│       ├── disclaimer.css
│       ├── globals.css
│       ├── message-actions.css
│       ├── model-selector.css
│       ├── new-chat-ui.css
│       ├── response-format.css
│       └── sidebar.css
│
├── build.ts
├── server.ts
├── package.json
├── tsconfig.json
├── tsconfig.frontend.json
├── vercel.json
├── LICENSE
└── README.md
```

---

## 🔄 Data & Execution Flow

```text
User ──> Chat Interface ──> Frontend Application ──(POST /api/chat)──> Vercel API ──> Gemini API
                                                                                            │
User <── AI Response <── Frontend <── (SSE) <── Streaming Response <────────────────────────┘
```

### ⚡ Streaming System
AI responses are delivered using **Server-Sent Events (SSE)**. The frontend receives response chunks progressively, providing a real-time conversational experience. An `AbortController` handles user cancellation requests during active generation.

---

## 🔐 Security & Best Practices

- **Environment Variables:** Credentials are securely managed outside source control.
  ```bash
  GEMINI_API_KEY=your_api_key_here
  ```
- **API Key Protection:** The Gemini API key remains isolated on the server side to avoid frontend exposure.
- **Content Sanitization:** HTML outputs are sanitized prior to UI injection.
- **External Links:** Safe link handling enforced using `target="_blank"` and `rel="noopener noreferrer"`.

---

## 💾 Local Persistence & Customization

- **Browser Storage:** Conversations, active sessions, and preferences are stored client-side in `LocalStorage`. No external database required. *(Note: Clearing browser data resets stored chats).*
- **Temperature Control:** Adjust creativity thresholds for precise vs. varied responses.
- **Assistant Personas:** Dynamic system instructions allow tailored assistant behaviors for distinct tasks.

---

## 🚀 Getting Started

### Prerequisites
- Node.js
- npm
- Google Gemini API Key

### Installation & Setup

1. **Install dependencies:**
   ```bash
   npm install
   ```

2. **Configure environment variables:**
   ```bash
   cp .env.example .env
   ```
   Add your API key inside `.env`:
   ```bash
   GEMINI_API_KEY=your_gemini_api_key_here
   ```

3. **Development Mode:**
   ```bash
   npm run dev
   ```

4. **Build Production Assets:**
   ```bash
   # Build frontend static files
   npm run build:frontend

   # Run full project build
   npm run build
   ```

---

## ☁️ Deployment

Deploy seamlessly via Vercel integration:

```text
GitHub Push ──> Vercel Trigger ──> TypeScript Build ──> Production Deployment
```

---

## 🧭 Project Focus & Roadmap

### Development Focus
- AI response quality & streaming reliability
- Responsive UI & mobile user experience
- Accessibility & performance optimizations

### 🗺️ Future Roadmap
- [ ] Progressive Web App (PWA) & offline support
- [ ] Cloud-based conversation sync & user authentication
- [ ] Multi-provider AI support
- [ ] Document/File analysis & Image understanding
- [ ] Custom tooling & advanced voice features

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 👨‍💻 Author

**URSourovAdikari**  
*Student & Developer*  
- **GitHub:** [@URSourovAdikari](https://github.com/URSourovAdikari)
- **Email:** `contact@sourovadikari.xyz`

*If you find this project useful, feel free to give it a ⭐! Built with ❤️ using TypeScript, Google Gemini, and Vercel.*
