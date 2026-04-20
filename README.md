# AnyDoc's Translator - Translate Website and PDF Doc

> Fast, accurate, production-ready Chrome Extension — **no AI/LLM models used**.

---

## 🚀 Features

| Feature | Description |
|---|---|
| 🌐 **Web Page Translation** | One-click translate entire page, auto-detect language, DOM swap |
| 🖱️ **Word/Phrase Popup** | Select any text → floating popup with translation + dictionary |
| 📄 **Document Translation** | Upload PDF, DOCX, PPTX, TXT — translated & downloadable |
| 🖼️ **Image OCR Translation** | Upload JPG/PNG → extract text via Tesseract.js → translate |
| 🔄 **Multi-Engine** | Switch between Google, Microsoft, LibreTranslate |
| 📖 **Bilingual Mode** | Original + translated side-by-side |
| 🌍 **RTL Support** | Auto-applies `rtl` layout for Arabic, Hebrew, Urdu, etc. |
| 🎬 **YouTube Subtitles** | Bilingual subtitle overlay on any YouTube video |
| 🎓 **Academic Mode** | Skip equations (LaTeX), citations [1], URLs during doc translation |

---

## 📁 Project Structure

```
ATOZ Transletor/
├── manifest.json          # Chrome Extension Manifest v3
├── popup.html             # Main popup UI
├── popup.js               # Popup controller
├── popup.css              # Premium red-gradient UI styles
├── options.html           # Full settings page
├── options.js             # Settings controller
├── options.css            # Settings page styles
├── background.js          # Service worker (API calls, context menus)
├── content.js             # Page-injected script (DOM translation)
├── content-styles.css     # Injected styles for popups/bilingual
├── utils/
│   ├── translators.js     # Google / Microsoft / LibreTranslate engines
│   ├── cache.js           # LRU translation cache
│   ├── storage.js         # chrome.storage wrapper
│   ├── ui.js              # Toast, status, animate helpers
│   ├── languages.js       # 100+ language list with RTL detection
│   └── docProcessor.js    # PDF/DOCX/TXT/Image processing
└── assets/
    └── icons/             # 16/32/48/128px extension icons
```

---

## ⚙️ Installation (Developer Mode)

1. Open Chrome → go to `chrome://extensions/`
2. Toggle **"Developer mode"** ON (top right)
3. Click **"Load unpacked"**
4. Select the `ATOZ Transletor` folder
5. Pin the extension from the extensions toolbar

---

## 🔑 API Keys

| Engine | Key Required | How to get |
|---|---|---|
| **Google Translate** | ❌ No (uses unofficial API) | — |
| **Microsoft Translator** | ✅ Yes | [Azure Portal](https://portal.azure.com/#create/Microsoft.CognitiveServicesTextTranslation) |
| **LibreTranslate** | Optional | [libretranslate.com](https://libretranslate.com) |

Enter API keys in **Settings → Engines**.

---

## ⌨️ Keyboard Shortcuts

| Shortcut | Action |
|---|---|
| `Ctrl+Shift+T` (Mac: `⌘⇧T`) | Translate current page |
| `Ctrl+Shift+E` (Mac: `⌘⇧E`) | Toggle extension on/off |

---

## 🎨 UI Design

- **Theme**: Dark premium with red gradient (`#ff2d55 → #ff6b35`)
- **Fonts**: Inter + Poppins (Google Fonts)
- **Design style**: SaaS/AdBlocker Pro aesthetic
- **Animations**: Smooth toggle transitions, animated stat counters, toast notifications

---

## 🛠️ Tech Stack

- **Chrome Extension**: Manifest v3
- **Frontend**: Vanilla HTML/CSS/JavaScript (ES Modules)
- **Translation**: Google Translate (unofficial), Microsoft Azure, LibreTranslate
- **OCR**: [Tesseract.js](https://tesseract.projectnaptha.com/) (loaded from CDN)
- **PDF**: [PDF.js](https://mozilla.github.io/pdf.js/) (loaded from CDN)
- **DOCX**: [Mammoth.js](https://github.com/mwilliamson/mammoth.js) (loaded from CDN)
- **Dictionary**: [Free Dictionary API](https://dictionaryapi.dev/)
- **Caching**: LRU in-memory + chrome.storage.local

---

## ⚡ Performance

- **Batch translation**: Groups DOM text nodes into batches of 50 for fewer API calls
- **LRU Cache**: In-memory cache (500 entries) + persisted to `chrome.storage.local`
- **Debounced selection**: 300ms debounce on text selection to avoid spamming APIs
- **Non-blocking**: All translation happens asynchronously in background worker

---

## 🚫 No AI Used

All translations powered exclusively by:
- Google Translate Web API
- Microsoft Cognitive Services Translator
- LibreTranslate (open source)

**No ChatGPT, Gemini, Claude, or any LLM is used.**

---

## 🗺️ Roadmap

- [ ] Screenshot export of translated page
- [ ] PPTX layout-preserving translation
- [ ] Offline cache export/import
- [ ] Firefox support (WebExtensions API)
- [ ] Premium: bulk file queue
