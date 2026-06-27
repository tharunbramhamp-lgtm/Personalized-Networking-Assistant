# Personalized Networking Assistant 🤝

A beginner-friendly AI-powered application that helps professionals generate personalized conversation starters, fact-check claims, and improve their networking skills.

## 🎯 What This Project Does

- **Generate Personalized Conversations:** Create contextually relevant conversation starters based on your networking event details
- **Fact-Check Claims:** Verify claims before sharing them in conversations
- **Track Conversation History:** Store and review past interactions
- **Collect Feedback:** Learn from feedback to improve future suggestions

## 🏗️ Project Structure

```
personalized-networking-assistant/
├── backend/                      # FastAPI backend
│   ├── main.py
│   ├── config.py
│   ├── database.py
│   ├── models/
│   ├── services/
│   ├── routers/
│   └── tests/
├── frontend/                     # Streamlit UI
│   ├── app.py
│   └── pages/
├── docs/                         # Documentation
├── data/                         # SQLite database
└── README.md
```

## 📚 Learning Path - 5 Epics

### **Epic 1: Model Selection and Architecture (2-3 days)**
- Research AI models (GPT, Claude, Ollama)
- Design system architecture
- Set up development environment

### **Epic 2: Core Functionalities (3-4 days)**
- Define database schema
- Build service layer (5 services)
- Implement API routes

### **Epic 3: Application Logic (1-2 days)**
- Connect all services
- Integrate FastAPI features

### **Epic 4: Frontend UI (2-3 days)**
- Build Streamlit interface
- Implement feedback system
- Add history views

### **Epic 5: Testing & Deployment (2-3 days)**
- Write unit tests
- Deploy locally
- Manual testing

## 🚀 Quick Start

```bash
# 1. Clone and enter directory
git clone <repo-url>
cd personalized-networking-assistant

# 2. Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# 3. Install dependencies
pip install -r backend/requirements.txt
pip install -r frontend/requirements.txt

# 4. Run backend
cd backend
python main.py

# 5. Run frontend (in new terminal)
cd frontend
streamlit run app.py
```

## 📖 Documentation

- [Epic 1: Model Selection & Architecture](docs/epic-1-overview.md)
- [Epic 2: Core Functionalities](docs/epic-2-overview.md)
- [Epic 3: Application Logic](docs/epic-3-overview.md)
- [Epic 4: Frontend UI](docs/epic-4-overview.md)
- [Epic 5: Testing & Deployment](docs/epic-5-overview.md)

## 🛠️ Tech Stack

- **Backend:** FastAPI, SQLAlchemy, Pydantic
- **Frontend:** Streamlit
- **Database:** SQLite
- **AI Model:** OpenAI GPT-3.5 / Local Ollama
- **Testing:** pytest

## 📋 Prerequisites

- Python 3.9+
- pip (Python package manager)
- Git
- Text editor (VS Code recommended)

## 🎓 What You'll Learn

✅ Building production-like APIs with FastAPI  
✅ Database design and SQLite  
✅ Service-oriented architecture  
✅ Frontend development with Streamlit  
✅ Integration with AI/LLM APIs  
✅ Unit testing and deployment  
✅ Git workflows  

## 📞 Support

For each story, detailed setup and implementation guides are provided in the docs folder.

---

**Start with Epic 1 → Story 1.1: Model Research & Selection**
