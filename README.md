# 🌱 Botanic Defenders

> **AI-powered platform for farmers** — plant disease detection, smart crop recommendations, mental wellness support, and real-time agricultural insights. Built for the Hackathon.

---

## 🚀 Features

### 🔬 Plant Health Detection
- Upload a crop image → instant AI-powered disease identification
- Top-3 disease predictions with confidence scores
- Treatment recommendations (organic & chemical) via **Google Gemini AI**
- Fertilizer suggestions for plant recovery

### 🌾 Crop Yield Dashboard
- Real-time weather data based on your location (**OpenWeatherMap API**)
- AI-driven crop recommendations based on temperature & climate
- Agricultural tips tailored to your region and season
- Activity logger to track daily farm tasks

### 🧠 Mental Wellness (Therapy)
- AI chat therapy sessions for farmer stress & anxiety
- Mindfulness games: Breathing Exercise, Zen Garden, Forest Game, Ocean Waves
- Chat session history with timestamps
- Mood tracker and activity logger

### 🔐 Authentication
- User signup/login with session management
- Protected dashboard routes

---

## 🛠️ Tech Stack

### Frontend
| Technology | Purpose |
|-----------|---------|
| Next.js 14 (App Router) | React framework |
| TypeScript | Type safety |
| Tailwind CSS | Styling |
| Framer Motion | Animations |
| shadcn/ui + Radix UI | UI components |
| Recharts | Data visualization |
| React Markdown | Chat message rendering |

### Backend
| Technology | Purpose |
|-----------|---------|
| FastAPI (Python) | REST API server |
| Hugging Face Transformers | Plant disease ML model |
| PyTorch | Deep learning inference |
| Google Gemini AI | Treatment & remedy recommendations |
| Pillow (PIL) | Image preprocessing |
| Uvicorn | ASGI server |

---

## 📁 Project Structure

```
botanic-defenders/
├── frontend/                        # Next.js frontend
│   ├── app/
│   │   ├── page.tsx                 # Landing page
│   │   ├── dashboard/               # Farmer dashboard
│   │   ├── plant-health/            # Disease detection page
│   │   ├── therapy/[sessionId]/     # AI therapy chat
│   │   ├── login/ & signup/         # Auth pages
│   │   └── api/                     # Next.js API routes
│   │       ├── auth/                # Login, register, session
│   │       ├── plant-health/predict # Proxies to FastAPI backend
│   │       ├── chat/sessions/       # Therapy chat sessions
│   │       ├── mood/                # Mood tracking
│   │       └── activity/            # Activity logging
│   ├── components/
│   │   ├── crops/                   # Crop yield dashboard
│   │   ├── games/                   # Mindfulness games
│   │   ├── chat/                    # Chat UI components
│   │   ├── mood/                    # Mood tracker
│   │   ├── therapy/                 # Therapy session components
│   │   └── ui/                      # shadcn/ui components
│   └── lib/
│       ├── api/                     # API client functions
│       ├── contexts/                # Session context
│       └── hooks/                   # Custom React hooks
│
├── backend/                         # FastAPI backend
│   ├── main.py                      # FastAPI app + ML model
│   ├── api/index.py                 # Vercel serverless entry
│   ├── requirements.txt             # Python dependencies
│   ├── vercel.json                  # Backend deployment config
│   └── run.sh                       # Local run script
│
└── README.md
```

---

## ⚙️ Getting Started

### Prerequisites
- Node.js 18+
- Python 3.8+
- [Google Gemini API Key](https://makersuite.google.com/app/apikey)
- [OpenWeatherMap API Key](https://openweathermap.org/api)

---

### 🖥️ Frontend Setup

```bash
cd frontend
npm install
```

Create `.env.local` in `frontend/`:
```env
BACKEND_URL=http://localhost:8002
NEXT_PUBLIC_OPENWEATHER_API_KEY=your_openweather_key
```

```bash
npm run dev
```

Frontend → **http://localhost:3000**

---

### 🐍 Backend Setup

```bash
cd backend

# Create & activate virtual environment
python3 -m venv venv
source venv/bin/activate        # Linux/Mac
# venv\Scripts\activate         # Windows

pip install -r requirements.txt
```

Set Gemini API key:
```bash
export GEMINI_API_KEY=your_gemini_api_key   # Linux/Mac
# set GEMINI_API_KEY=your_key               # Windows
```

```bash
python main.py
```

Backend API → **http://localhost:8002**

---

## 🔌 API Endpoints

### Backend (Port 8002)
| Method | Endpoint | Description |
|--------|---------|-------------|
| GET | `/` | API status |
| GET | `/health` | Health check + model status |
| POST | `/predict` | Plant disease prediction from image |

### Frontend API Routes (Port 3000)
| Method | Endpoint | Description |
|--------|---------|-------------|
| POST | `/api/plant-health/predict` | Proxy to backend |
| POST | `/api/auth/register` | User registration |
| POST | `/api/auth/login` | User login |
| GET | `/api/auth/me` | Current user |
| GET/POST | `/api/chat/sessions` | Therapy sessions |
| POST | `/api/mood` | Log mood |
| POST | `/api/activity` | Log activity |

---

## 🧪 ML Model

Uses **[MobileNetV2 fine-tuned for plant disease identification](https://huggingface.co/linkanjarad/mobilenet_v2_1.0_224-plant-disease-identification)** from Hugging Face.

Detectable conditions include: Bacterial Spot, Early Blight, Late Blight, Leaf Mold, Septoria Leaf Spot, Spider Mites, Target Spot, Yellow Leaf Curl Virus, Mosaic Virus, and Healthy Plant ✅

---

## 🎮 Mindfulness Games

| Game | Description |
|------|-------------|
| 🫁 Breathing Exercise | Guided breathing animations |
| 🪨 Zen Garden | Interactive sand garden |
| 🌲 Forest Game | Calming forest environment |
| 🌊 Ocean Waves | Audio + visual wave relaxation |

---

## 🌐 Deployment

### Frontend → Vercel
```bash
cd frontend && vercel deploy
```

Add env vars in Vercel dashboard:
```
BACKEND_URL=https://your-backend.vercel.app
NEXT_PUBLIC_OPENWEATHER_API_KEY=your_key
```

### Backend → Vercel
```bash
cd backend && vercel deploy
```

`vercel.json` and `api/index.py` are already configured for serverless.

---

## 📦 Scripts

```bash
# Frontend
npm run dev        # Dev server
npm run build      # Production build
npm run lint       # ESLint

# Backend
python main.py         # Start server
python test_gemini.py  # Test Gemini connection
./run.sh               # Auto-reload server
```

---

## 🏆 Hackathon Project

Built by **Team Botanic Defenders** 🌱

## ⭐ Star this repo if you like it!

> Empowering farmers with AI — because every harvest matters. 🌾🤖

---

## 📄 License

MIT License
