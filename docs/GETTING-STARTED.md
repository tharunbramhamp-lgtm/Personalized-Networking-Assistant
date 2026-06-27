# Getting Started - Complete Beginner's Guide

## 👋 Welcome!

You're about to build a **Personalized Networking Assistant** - an AI-powered application that helps professionals prepare for networking events.

### What Will You Build?

An intelligent assistant that:
- 🎯 Generates personalized conversation starters for networking events
- 🔍 Fact-checks claims before you share them
- 📚 Stores conversation history
- 💬 Collects feedback to improve suggestions

### Prerequisites

Before you start, make sure you have:

1. **Python 3.10+**
   ```bash
   python --version  # Should show 3.10 or higher
   ```
   - Download from: https://www.python.org/
   - **Windows:** Check "Add Python to PATH" during installation

2. **Git & GitHub**
   ```bash
   git --version  # Should show a version number
   ```
   - Download from: https://git-scm.com/
   - Create free account at: https://github.com

3. **Text Editor**
   - **VS Code** (Recommended): https://code.visualstudio.com/
   - Alternative: PyCharm, Sublime Text

4. **Google Account**
   - For free Gemini API access
   - No credit card required!

---

## 📚 Project Structure

```
personalized-networking-assistant/
├── backend/              ← Python/FastAPI code
│   ├── services/         ← Business logic (AI calls, processing)
│   ├── routers/          ← API endpoints
│   ├── models/           ← Database models
│   └── tests/            ← Unit tests
├── frontend/             ← Streamlit UI (what users see)
│   ├── pages/            ← Different pages of the app
│   └── components/       ← Reusable UI pieces
├── docs/                 ← Documentation & guides
├── data/                 ← SQLite database (stores data)
└── README.md
```

---

## 🎯 Your Learning Journey

### **Phase 1: Foundation (Today) - Epic 1**
- Choose AI model: Google Gemini ✅
- Understand architecture
- Set up environment
- **Time:** ~2.5 hours

### **Phase 2: Backend (Day 1-2) - Epic 2**
- Design database schema
- Build 5 services (business logic)
- Create 4 API endpoints
- **Time:** ~4 hours

### **Phase 3: Connection (Day 2) - Epic 3**
- Connect all services
- Set up routing
- **Time:** ~1.5 hours

### **Phase 4: Frontend (Day 3) - Epic 4**
- Build Streamlit UI
- Create user input forms
- Display results
- **Time:** ~3 hours

### **Phase 5: Polish (Day 4) - Epic 5**
- Write tests
- Deploy locally
- Manual testing
- **Time:** ~3 hours

**Total:** ~14 hours of hands-on learning

---

## 🚀 Quick Start Commands

```bash
# 1. Create project folder
mkdir personalized-networking-assistant
cd personalized-networking-assistant

# 2. Initialize git
git init

# 3. Create virtual environment
python -m venv venv

# 4. Activate it
# Windows:
venv\Scripts\activate
# macOS/Linux:
source venv/bin/activate

# 5. Create folder structure
mkdir -p backend/{services,routers,models,tests}
mkdir -p frontend/{pages,components}
mkdir docs data

# 6. Copy requirements files (from this repo)
# ... then install:
pip install -r backend/requirements.txt
pip install -r frontend/requirements.txt

# 7. Create .env file with your Gemini API key
echo "GEMINI_API_KEY=AIzaSy..." > backend/.env

# 8. Ready to code!
```

---

## 🎓 Key Concepts You'll Learn

### **1. APIs (Application Programming Interface)**
- How frontend talks to backend
- REST API principles
- JSON data format

### **2. Backend Development**
- FastAPI framework
- Request/response handling
- Business logic implementation

### **3. Database Design**
- Tables and relationships
- SQLAlchemy ORM
- SQLite database

### **4. Frontend Development**
- Streamlit framework
- Interactive components
- State management

### **5. AI/LLM Integration**
- Google Gemini API
- Prompt engineering
- Response parsing

### **6. Software Architecture**
- Separation of concerns
- Service-oriented design
- Scalability principles

### **7. Testing**
- Unit tests
- Integration tests
- Test-driven development

### **8. DevOps/Deployment**
- Local deployment
- Environment variables
- Production considerations

---

## 💡 Tips for Success

1. **Follow the Stories in Order**
   - Don't skip ahead
   - Each story builds on the previous

2. **Code Along**
   - Don't just read
   - Actually type and run the code

3. **Test Frequently**
   - After each step, verify it works
   - Print debug information

4. **Commit to Git**
   - After each story: `git add . && git commit -m "Complete Story X.Y"`
   - Helps track progress

5. **Read the Documentation**
   - Each epic has detailed docs
   - Understand "why" not just "what"

6. **Experiment**
   - Try changing parameters
   - Break things intentionally
   - Fix and learn from errors

7. **Ask Questions**
   - Google error messages
   - Read Stack Overflow
   - Check framework docs

---

## 🔍 Understanding the Tech Stack

### **Backend: FastAPI**
- Modern Python web framework
- Built-in API documentation
- Handles HTTP requests/responses
- Perfect for beginners

### **Frontend: Streamlit**
- Python-based UI framework
- No need to learn HTML/CSS/JavaScript
- Perfect for data science apps
- Rapid prototyping

### **Database: SQLite**
- Simple file-based database
- No server needed
- Perfect for learning
- Runs on your laptop

### **AI: Google Gemini**
- Free API with generous free tier
- Excellent conversation quality
- Great documentation
- Perfect for networking assistant

### **Storage: Python Packages**
```
Pydantic     → Data validation
SQLAlchemy   → Database ORM
requests     → HTTP library
pytest       → Testing framework
```

---

## 🎯 Your First Task

**Complete Epic 1: Model Selection and Architecture**

1. Read `docs/EPIC-1-MODEL-SELECTION.md`
2. Follow Story 1.1 (Model Research)
3. Follow Story 1.2 (Architecture)
4. Follow Story 1.3 (Environment Setup)
5. Make your first git commit

**Estimated Time:** 2-3 hours

---

## ✅ How to Know You're Ready for Epic 2

After Epic 1, you should be able to answer:

- [ ] What is Google Gemini API?
- [ ] Why did we choose it over alternatives?
- [ ] What are the 5 main layers of our architecture?
- [ ] What does each folder in `backend/` do?
- [ ] How do frontend and backend communicate?
- [ ] Where does the database file live?
- [ ] What is a virtual environment?
- [ ] Where do I keep my API key (safely)?
- [ ] Can I run `python --version` and see 3.10+?
- [ ] Can I run `git init` successfully?

---

## 🆘 Need Help?

### Common Issues:

**Issue:** Python not found
```bash
# Make sure it's installed and added to PATH
python --version  # Should show 3.10+
```

**Issue:** Virtual environment not activating
```bash
# Try this:
python -m venv venv
# Then activate it again
```

**Issue:** Can't get Gemini API key
```bash
# Go to: https://ai.google.dev
# Click "Get API Key"
# No credit card needed!
```

**Issue:** Git commands not working
```bash
# Install from: https://git-scm.com/
# Restart terminal after installation
```

---

## 📖 Next Steps

1. ✅ You're reading this - good start!
2. Make sure all prerequisites are installed
3. Start **docs/EPIC-1-MODEL-SELECTION.md**
4. Follow the stories step-by-step
5. Don't skip ahead
6. Commit to git after each story
7. Have fun building! 🎉

---

**Ready to start? Go to `docs/EPIC-1-MODEL-SELECTION.md`**
