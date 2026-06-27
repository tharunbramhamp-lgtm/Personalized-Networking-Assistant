# Quick Start Guide

## 🚀 Get Running in 10 Minutes

### 1. Clone/Download Project
```bash
git clone <repository-url>
cd personalized-networking-assistant
```

### 2. Set Up Environment
```bash
# Create virtual environment
python -m venv venv

# Activate
# Windows:
venv\Scripts\activate
# macOS/Linux:
source venv/bin/activate
```

### 3. Install Dependencies
```bash
cd backend
pip install -r requirements.txt
cd ..

cd frontend
pip install -r requirements.txt
cd ..
```

### 4. Configure API Key
```bash
# Create backend/.env with your Gemini API key:
echo "GEMINI_API_KEY=AIzaSy..." >> backend/.env
echo "DATABASE_URL=sqlite:///./data/app.db" >> backend/.env
```

### 5. Run Backend
```bash
cd backend
python main.py
# You should see: "Uvicorn running on http://127.0.0.1:8000"
```

### 6. Run Frontend (in new terminal)
```bash
cd frontend
streamlit run app.py
# Automatically opens http://localhost:8501
```

### 7. Use the App!
Visit `http://localhost:8501` and start generating conversations.

---

## 📝 Project Structure

```
backend/
  ├── main.py              # FastAPI app
  ├── config.py            # Settings
  ├── database.py          # DB connection
  ├── models/              # Data models
  ├── services/            # Business logic
  ├── routers/             # API endpoints
  └── tests/               # Unit tests

frontend/
  ├── app.py               # Streamlit main
  ├── pages/               # UI pages
  └── components/          # Reusable components

docs/                      # Documentation
data/
  └── app.db               # SQLite database
```

---

## 🛠️ Troubleshooting

### Backend won't start
```bash
# Make sure virtual environment is activated
source venv/bin/activate  # or venv\\Scripts\\activate on Windows

# Check Python version
python --version  # Should be 3.10+

# Reinstall dependencies
pip install --upgrade pip
pip install -r backend/requirements.txt
```

### Gemini API errors
```bash
# Verify API key is correct
echo $GEMINI_API_KEY

# Or check .env file
cat backend/.env
```

### Port already in use
```bash
# Change port in backend/.env
API_PORT=8001

# Or kill process using port
# macOS/Linux:
lsof -i :8000
kill -9 <PID>
```

---

## 📚 Learning Path

1. **Epic 1** (~2.5h): Setup and architecture ✅
2. **Epic 2** (~4h): Backend services and APIs
3. **Epic 3** (~1.5h): Connect services
4. **Epic 4** (~3h): Frontend UI
5. **Epic 5** (~3h): Testing and deployment

**Total Time:** ~14 hours of learning and building

---

## 🎯 What You'll Learn

✅ FastAPI backend development  
✅ Database design (SQLAlchemy)  
✅ Service-oriented architecture  
✅ Streamlit frontend  
✅ Google Gemini API integration  
✅ Testing with pytest  
✅ Git workflows  
✅ Production deployment

---

## 📖 Next Steps

- Read **docs/EPIC-1-MODEL-SELECTION.md** for detailed setup ✅ (Done)
- Start **docs/EPIC-2-CORE-FUNCTIONALITIES.md**
- Follow stories one by one
- Build incrementally
- Test after each story
- Commit to git frequently

Happy building! 🎉
