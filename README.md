# 🧭 AI Travel Guide

An AI-powered travel companion that generates **spoken audio guides** for famous places. Pick a destination (or search for one), choose the language, guide length and voice, and the app produces a written description plus a narrated audio guide you can play right in the browser.

## ✨ Features

- Browse featured destinations or search for any place
- **Two guide styles**: *Summary* (~200 words) and *Detailed* (~400 words)
- **Multilingual**: English, Hindi, Tamil and Telugu
- **Male / Female voice** selection for each language
- Built-in audio player and a collapsible **transcript**
- Responsive UI built with Tailwind CSS

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | HTML, JavaScript (vanilla), Tailwind CSS (CDN) |
| Backend | Python, Flask, Flask-CORS |
| Text generation | Google Gemini API (`google-genai`) |
| Text-to-speech | Murf AI API |

## 📁 Project Structure

```
Project_TRAVEL_GUIDE/
├── backend/
│   └── app.py          # Flask server: generates text + audio
├── frontend/
│   ├── index.html      # UI
│   └── index.js        # UI logic and API calls
├── .gitignore
└── README.md
```

## ⚙️ How It Works

1. The user selects a place, language, guide length and voice in the frontend.
2. The frontend sends a `POST` request to the Flask backend.
3. The backend asks **Gemini** to write a tour-guide style description in the chosen language.
4. The text is sent to **Murf AI** to be converted into an MP3.
5. The backend returns the description and the audio (Base64) to the frontend, which plays it.

## 🚀 Getting Started

### Prerequisites

- Python 3.9+
- A [Google Gemini API key](https://aistudio.google.com/)
- A [Murf AI API key](https://murf.ai/api)

### 1. Clone the repository

```bash
git clone https://github.com/VitalVinayak/Project_TRAVEL_GUIDE.git
cd Project_TRAVEL_GUIDE
```

### 2. Set up the backend

```bash
cd backend
python -m venv venv

# Windows
venv\Scripts\activate
# macOS / Linux
source venv/bin/activate

pip install flask flask-cors google-genai requests python-dotenv
pip install -U google-genai
```

Or install everything at once from the included `requirements.txt`:

```bash
pip install -r requirements.txt
```

Create a `.env` file inside the `backend` folder:

```env
MURF_API_KEY=your_murf_api_key_here
GEMINI_API_KEY=your_gemini_api_key_here
```

Start the server:

```bash
python app.py
```

You can also run it from the project root folder:

```bash
python .\Backend\app.py
```

The backend runs at `http://127.0.0.1:5000`.

### 3. Run the frontend

Open a new terminal:

```bash
cd frontend
```

Then either open `index.html` directly in your browser, or use the **Live Server** extension in VS Code (right-click `index.html` → *Open with Live Server*).

> Make sure the backend is running first, otherwise audio generation will fail.

## 💻 Commands Used

### Install dependencies

```bash
pip install flask flask-cors google-genai
pip install -U google-genai
pip install flask-cors
```

### Run the backend

```bash
python .\Backend\app.py
```

### Push the project to GitHub

```bash
git init
git add .
git commit -m "Initial commit: AI Travel Guide"
git branch -M main
git remote add origin https://github.com/VitalVinayak/Project_TRAVEL_GUIDE.git
git push -u origin main
```

### Update GitHub after making changes

```bash
git add .
git commit -m "Describe your change"
git push
```

## 🔌 API Reference

### `POST /generate-audio-guide`

**Request body**

```json
{
  "place": "Taj Mahal",
  "answerType": "Summary",
  "language": "English",
  "voiceId": "Matthew",
  "locale": "en-US"
}
```

| Field | Description |
|-------|-------------|
| `place` | Name of the destination |
| `answerType` | `Summary` or `Detailed` |
| `language` | `English`, `Hindi`, `Tamil` or `Telugu` |
| `voiceId` | Murf voice name (e.g. `Matthew`, `Alicia`, `Aman`) |
| `locale` | Language locale (e.g. `en-US`, `hi-IN`) |

**Response**

```json
{
  "description": "Generated text of the guide...",
  "audioBase64": "<base64-encoded MP3>"
}
```

## 🎙️ Supported Voices

| Language | Male | Female |
|----------|------|--------|
| English | Matthew | Alicia |
| Hindi | Aman | Namrita |
| Tamil | Murali | Iniya |
| Telugu | Zion | Josie |

## 🔐 Security Note

API keys are loaded from a `.env` file, which is excluded from Git via `.gitignore`. **Never commit your keys to GitHub.**

## 🔮 Future Improvements

- Support for more languages and voices
- Save and download generated audio guides
- Add user accounts and favourite places
- Deploy the backend and frontend online

## 👤 Author

**Vital Vinayak**
GitHub: [@VitalVinayak](https://github.com/VitalVinayak)

---

⭐ If you like this project, give it a star!
