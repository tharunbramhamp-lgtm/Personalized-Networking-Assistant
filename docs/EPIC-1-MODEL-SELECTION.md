# Epic 1: Model Selection and Architecture

## 📋 Overview

This epic focuses on **foundational decisions** that will guide the entire project. You'll research AI models, design the system architecture, and set up your development environment.

**Duration:** 2-3 days | **Difficulty:** ⭐ (Beginner-friendly)

---

## Story 1.1: Model Research & Selection

### 🎯 What You'll Do
Research and choose an AI model for generating conversations and fact-checking.

### 📚 Research the Options

#### **Option A: Google Gemini API (RECOMMENDED FOR THIS PROJECT)**

**What it is:** Google's advanced AI model with free tier available

**Pros:**
- ✅ Free tier with 60 requests/minute
- ✅ Excellent conversation quality
- ✅ Great for fact-checking
- ✅ Easy setup
- ✅ Best for learning

**Cons:**
- ❌ Rate limited on free tier
- ❌ Requires internet
- ❌ External API dependency

**Cost Estimate:** Free for development, ~$0.50/1M tokens for production

**Setup:**
```bash
# Get free API key at https://ai.google.dev
# No credit card required!
```

**Why We Chose This:**
1. Free tier perfect for learning
2. No credit card needed
3. Great documentation
4. Perfect for networking use case
5. Gemini understands context very well

---

#### **Option B: Local Ollama (Alternative - FREE, OFFLINE)**

**Pros:**
- ✅ 100% free
- ✅ No internet needed
- ✅ Data stays on your laptop

**Cons:**
- ❌ Slower (5-10 seconds per response)
- ❌ Lower quality
- ❌ Requires 8GB+ RAM

---

#### **Option C: OpenAI GPT-3.5 (Alternative)**

**Pros:** Highest quality

**Cons:** Costs $5-20/month

---

### ✅ Decision Matrix

| Criteria | Gemini | Ollama | GPT-3.5 |
|----------|--------|--------|----------|
| Setup Time | 5 min | 15 min | 10 min |
| Quality | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| Speed | <1 sec | 5-10 sec | <1 sec |
| Cost | FREE | Free | $$ |
| Learning Value | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ |
| Free Tier | ✅ YES | ✅ YES | ❌ NO |

### 🎓 **RECOMMENDATION FOR THIS PROJECT:**

👉 **Use Google Gemini API** because:
1. ✅ Free tier with no credit card
2. ✅ Easiest to set up
3. ✅ Best for learning
4. ✅ Production-quality results
5. ✅ Perfect for networking assistant use case

---

### 📝 Getting Your Gemini API Key

**Step 1: Create Google Account**
- If you don't have one, create at https://accounts.google.com

**Step 2: Get API Key**
```bash
# Go to: https://ai.google.dev
# Click "Get API Key"
# Select "Create API key in new project"
# Copy your API key (keep it secret!)
```

**Step 3: Test Your Key**

Create a test file: `test_gemini.py`

```python
import google.generativeai as genai

# Configure API
genai.configure(api_key="YOUR_API_KEY_HERE")

# Test the model
model = genai.GenerativeModel('gemini-pro')
response = model.generate_content(
    "Help me start a conversation at a tech conference about AI."
)

print(response.text)
```

**Run the test:**
```bash
pip install google-generativeai
python test_gemini.py

# Expected output:
# A helpful conversation starter ✅
```

---

### ✅ Acceptance Criteria

- [ ] Read about all 3 model options
- [ ] Created Google account
- [ ] Got Gemini API key from https://ai.google.dev
- [ ] Tested API key works
- [ ] Saved API key securely (we'll add to .env later)
- [ ] Documented your choice in `docs/MODEL-SELECTION.md`

---

## Story 1.2: Defining the Application Architecture

### 🎯 What You'll Do
Understand and document how your entire application will be organized.

### 🏗️ System Architecture

```
┌─────────────────────────────────────────────────────────┐
│         Streamlit Frontend (UI)                         │
│    - User inputs (event details, interests)             │
│    - Display results (conversation starters)            │
│    - Feedback forms                                     │
└──────────────────────┬──────────────────────────────────┘
                       │
                       │ HTTP Requests (JSON)
                       ▼
┌─────────────────────────────────────────────────────────┐
│         FastAPI Backend (Server)                        │
│                                                         │
│  ┌──────────────────────────────────────────────────┐  │
│  │  API Routes (endpoints)                          │  │
│  │  /generate  /fact-check  /history                │  │
│  └──────────────────────────┬───────────────────────┘  │
│                             │                           │
│  ┌──────────────────────────▼───────────────────────┐  │
│  │  Services (business logic)                       │  │
│  │  - EventAnalyzer                                 │  │
│  │  - TopicGenerator (calls Gemini API)             │  │
│  │  - FactChecker (calls Gemini API)                │  │
│  │  - HistoryLogger                                 │  │
│  │  - FeedbackLogger                                │  │
│  └──────────────────────────┬───────────────────────┘  │
│                             │                           │
│  ┌──────────────────────────▼───────────────────────┐  │
│  │  Database Models (SQLAlchemy)                    │  │
│  │  Defines tables and relationships                │  │
│  └──────────────────────────┬───────────────────────┘  │
│                             │                           │
│  ┌──────────────────────────▼───────────────────────┐  │
│  │  External Services                               │  │
│  │  - Google Gemini API                             │  │
│  └──────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────┘
                       │
                       ▼
        ┌──────────────────────────┐
        │   SQLite Database        │
        │  (local file storage)    │
        │  Tables:                 │
        │  - conversations         │
        │  - fact_checks           │
        │  - user_feedback         │
        └──────────────────────────┘
```

### 📂 Detailed Directory Structure

```
personalized-networking-assistant/
│
├── backend/                          ← Backend code
│   ├── main.py                       ← FastAPI app starts here
│   ├── config.py                     ← Configuration settings
│   ├── database.py                   ← Database connection
│   │
│   ├── models/
│   │   ├── __init__.py
│   │   ├── schemas.py                ← API request/response models (Pydantic)
│   │   └── db_models.py              ← Database table definitions (SQLAlchemy)
│   │
│   ├── services/                     ← Business logic (do the actual work)
│   │   ├── __init__.py
│   │   ├── event_analyzer.py         ← Parse networking event context
│   │   ├── topic_generator.py        ← Generate conversation topics
│   │   ├── fact_checker.py           ← Verify facts
│   │   ���── history_logger.py         ← Save conversations
│   │   └── feedback_logger.py        ← Save user feedback
│   │
│   ├── routers/                      ← API endpoints
│   │   ├── __init__.py
│   │   ├── generation.py             ← POST /generate
│   │   ├── fact_checking.py          ← POST /fact-check
│   │   ├── history.py                ← GET /history
│   │   └── feedback.py               ← POST /feedback
│   │
│   ├── tests/
│   │   ├── __init__.py
│   │   ├── test_event_analyzer.py
│   │   ├── test_topic_generator.py
│   │   ├── test_fact_checker.py
│   │   └── test_api_routes.py
│   │
│   ├── requirements.txt               ← Dependencies
│   └── .env                          ← Secrets (don't commit!)
│
├── frontend/                         ← Streamlit UI
│   ├── app.py                        ← Streamlit main entry point
│   ├── requirements.txt
│   │
│   ├── pages/                        ← Different UI pages
│   │   ├── 01_home.py               ← Main generation page
│   │   ├── 02_fact_check.py         ← Fact-checking tool
│   │   ├── 03_history.py            ← View past conversations
│   │   └── 04_feedback.py           ← View feedback
│   │
│   └── components/                   ← Reusable UI components
│       ├── input_section.py
│       ├── results_display.py
│       └── feedback_form.py
│
├── docs/                             ← Documentation
│   ├── EPIC-1-MODEL-SELECTION.md
│   ├── EPIC-2-CORE-FUNCTIONALITIES.md
│   ├── EPIC-3-APPLICATION-LOGIC.md
│   ├── EPIC-4-FRONTEND-UI.md
│   ├── EPIC-5-TESTING-DEPLOYMENT.md
│   ├── ARCHITECTURE.md
│   └── API-DESIGN.md
│
├── data/
│   └── app.db                        ← SQLite database (auto-created)
│
├── .gitignore                         ← What Git should ignore
├── .env.example                       ← Example of .env file
└── README.md                          ← Project overview
```

### 🔄 How Data Flows Through the System

**Example: User wants to generate a conversation starter**

```
1. USER enters data in Streamlit (event name, industry, interests)
   ↓
2. Streamlit sends HTTP POST request to FastAPI
   POST /generate {"event": "Tech Summit", "industry": "AI", ...}
   ↓
3. FastAPI router receives request
   ↓
4. EventAnalyzer service processes the input
   ↓
5. TopicGenerator service calls Google Gemini API
   ↓
6. Response comes back from Gemini
   ↓
7. HistoryLogger saves it to SQLite database
   ↓
8. FastAPI returns JSON response to Streamlit
   ↓
9. Streamlit displays results to user
   ↓
10. User clicks "feedback" button
    ↓
11. Streamlit sends feedback to FastAPI
    ↓
12. FeedbackLogger saves it to database
```

### ✅ Key Design Principles

#### **1. Separation of Concerns**
Each file has ONE job:
- `services/` → Business logic
- `routers/` → API endpoints
- `models/` → Data structures
- `frontend/` → User interface

#### **2. Easy Testing**
Each service can be tested independently without running the whole app.

#### **3. Reusability**
Services can be used by different routes. If you need the same logic in 3 different endpoints, you use 1 service.

#### **4. Scalability**
If you need to add a new feature:
1. Create a new service
2. Create a new router
3. Done! No changes to existing code.

---

### ✅ Acceptance Criteria

- [ ] Understand the system architecture
- [ ] Know what each folder does
- [ ] Understand how data flows
- [ ] Ready to proceed to environment setup

---

## Story 1.3: Environment Setup

### 🎯 What You'll Do
Configure your laptop to run the application.

### Step 1: Verify Python Installation

```bash
# Check Python version (should be 3.10+)
python --version

# If not installed, download from https://www.python.org/
# Make sure to check "Add Python to PATH" during installation
```

### Step 2: Create Project Directory

```bash
# Navigate to where you want the project
cd Documents  # or wherever you prefer

# Create project folder
mkdir personalized-networking-assistant
cd personalized-networking-assistant

# Create subfolders
mkdir -p backend/{services,routers,models,tests}
mkdir -p frontend/pages frontend/components
mkdir -p docs
mkdir -p data
```

### Step 3: Initialize Git

```bash
# Initialize git repository
git init

# Configure Git
git config user.name "Your Name"
git config user.email "your.email@example.com"

# Create .gitignore
cat > .gitignore << 'EOF'
# Python
__pycache__/
*.py[cod]
*$py.class
*.so
.Python
build/
dist/
*.egg-info/

# Virtual Environment
venv/
env/
ENV/

# IDE
.vscode/
.idea/
*.swp
*.swo

# Environment variables
.env
.env.local

# Database
*.db
*.sqlite
*.sqlite3

# Streamlit
.streamlit/
EOF

git add .gitignore
git commit -m "Initial commit: Add .gitignore"
```

### Step 4: Create Virtual Environment

```bash
# Create virtual environment
python -m venv venv

# Activate it
# On Windows:
venv\Scripts\activate

# On macOS/Linux:
source venv/bin/activate

# You should see (venv) in your terminal
```

### Step 5: Create requirements.txt Files

**Create `backend/requirements.txt`:**

```txt
# FastAPI - Web framework
fastapi==0.104.1
uvicorn[standard]==0.24.0

# Data validation
pydantic==2.5.0
pydantic-settings==2.1.0

# Database
sqlalchemy==2.0.23

# Google Gemini API
google-generativeai==0.3.0

# HTTP
requests==2.31.0
httpx==0.25.1

# Environment
python-dotenv==1.0.0

# Testing
pytest==7.4.3
pytest-asyncio==0.21.1

# Utilities
python-multipart==0.0.6
```

**Create `frontend/requirements.txt`:**

```txt
# Streamlit - Frontend framework
streamlit==1.28.1

# HTTP
requests==2.31.0

# Data manipulation
pandas==2.1.3

# Environment
python-dotenv==1.0.0
```

### Step 6: Install Dependencies

```bash
# Navigate to project root
cd personalized-networking-assistant

# Install backend dependencies
cd backend
pip install -r requirements.txt

# Go back to project root
cd ..

# Install frontend dependencies
cd frontend
pip install -r requirements.txt

# Go back to project root
cd ..

# Verify installations
python -c "import fastapi; print('FastAPI:', fastapi.__version__)"
python -c "import streamlit; print('Streamlit:', streamlit.__version__)"
python -c "import google.generativeai; print('Gemini API:', 'installed')"
```

### Step 7: Create Configuration Files

**Create `backend/.env.example`:**

```
# Google Gemini API Configuration
LLM_PROVIDER=gemini
GEMINI_API_KEY=your-api-key-here

# Database
DATABASE_URL=sqlite:///./data/app.db

# API Settings
API_HOST=127.0.0.1
API_PORT=8000
DEBUG=True
```

**Create `backend/.env` (use your actual API key):**

```
LLM_PROVIDER=gemini
GEMINI_API_KEY=AIzaSyxxxxxxxxxxxxxxxxxxxxxx  # Your actual API key from https://ai.google.dev
DATABASE_URL=sqlite:///./data/app.db
API_HOST=127.0.0.1
API_PORT=8000
DEBUG=True
```

⚠️ **Important:** Never share your `.env` file! It contains secrets.

### Step 8: Create Initial Python Files

```bash
# Create empty __init__.py files
touch backend/__init__.py
touch backend/models/__init__.py
touch backend/services/__init__.py
touch backend/routers/__init__.py
touch backend/tests/__init__.py

touch frontend/__init__.py
touch frontend/pages/__init__.py
touch frontend/components/__init__.py
```

### Step 9: Create Basic Configuration

**Create `backend/config.py`:**

```python
from pydantic_settings import BaseSettings
from pathlib import Path

class Settings(BaseSettings):
    # LLM Configuration
    llm_provider: str = "gemini"
    gemini_api_key: str = ""
    
    # Database
    database_url: str = "sqlite:///./data/app.db"
    
    # API Settings
    api_host: str = "127.0.0.1"
    api_port: int = 8000
    debug: bool = True
    
    class Config:
        env_file = ".env"
        case_sensitive = False

settings = Settings()
```

**Create `backend/database.py`:**

```python
from sqlalchemy import create_engine
from sqlalchemy.ext.declarative import declarative_base
from sqlalchemy.orm import sessionmaker
from config import settings

DATABASE_URL = settings.database_url

engine = create_engine(
    DATABASE_URL,
    connect_args={"check_same_thread": False} if "sqlite" in DATABASE_URL else {}
)

SessionLocal = sessionmaker(
    autocommit=False,
    autoflush=False,
    bind=engine
)

Base = declarative_base()

def get_db():
    """Dependency for getting database session"""
    db = SessionLocal()
    try:
        yield db
    finally:
        db.close()
```

### Step 10: Verify Everything Works

```bash
# Make sure you're in the project root and venv is activated

# Test imports
python -c "from backend.config import settings; print('Config loaded:', settings.llm_provider)"

# Test database
python -c "from backend.database import engine; print('Database ready')"

# Test FastAPI
python -c "from fastapi import FastAPI; print('FastAPI ready')"

# Test Gemini API
python -c "import google.generativeai; print('Gemini API ready')"
```

### Step 11: First Git Commit

```bash
git add .
git commit -m "Add project structure and initial setup"
```

---

### ✅ Acceptance Criteria

- [ ] Python 3.10+ installed and verified
- [ ] Project directory structure created
- [ ] Virtual environment set up and activated
- [ ] Dependencies installed successfully
- [ ] `.env` file configured with Gemini API key
- [ ] All configuration files created
- [ ] Initial commit pushed to git
- [ ] All imports verified without errors

---

### 🎉 Epic 1 Complete!

You now have:
- ✅ A chosen AI model (Google Gemini)
- ✅ A clear system architecture
- ✅ A configured development environment
- ✅ Git repository initialized

**Next:** Proceed to **Epic 2: Core Functionalities Development**

---

## 📝 Summary of Epic 1

| Story | What | Time |
|-------|------|------|
| 1.1 | Choose AI model (Gemini recommended) | 30 min |
| 1.2 | Understand architecture | 1 hour |
| 1.3 | Set up environment, install packages | 1 hour |
| **Total** | | **~2.5 hours** |

---

## 🆘 Troubleshooting

### Problem: "Python not found"
**Solution:** Make sure Python 3.10+ is installed: `python --version`

### Problem: "Virtual environment won't activate"
**Solution:** Use `python -m venv venv` then try activating again

### Problem: "pip install fails"
**Solution:** 
```bash
pip install --upgrade pip
pip install -r requirements.txt
```

### Problem: "Gemini API key not working"
**Solution:** 
1. Go to https://ai.google.dev
2. Click "Get API Key"
3. Copy the entire key (keep it secret!)
4. Paste in `.env` file

### Problem: "Import errors"
**Solution:** Make sure virtual environment is activated (you should see `(venv)` in terminal)
