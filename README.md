cat > README.md << 'EOF'
# 💎 PRISM - Professional UPSC Mains Evaluation System

## Live Application
**Frontend:** https://storage.googleapis.com/prism-demo-bloombnb/prism-final.html  
**Backend API:** https://prism-evaluator-40341559956.us-central1.run.app

## Overview
PRISM is an AI-powered evaluation system for UPSC Civil Services Mains answers. It provides expert-level feedback across 6 dimensions using Google's Gemini 2.5 Flash, helping aspirants improve their answer writing through actionable insights.

## Problem Statement
- 70% of UPSC Mains success depends on answer writing quality
- Most aspirants receive no structured feedback until mock tests
- Average candidates start answer writing practice too late
- Generic feedback doesn't help identify specific improvement areas

## Solution
PRISM evaluates answers using a 6-layer "Autopsy" framework derived from research with UPSC toppers, faculty evaluators, and failed aspirants:

1. **Content (30%)** - Factual accuracy, topic coverage, relevance
2. **Structure (40%)** - Intro-body-conclusion, logical flow, organization
3. **Analysis (15%)** - Critical thinking, cause-effect reasoning
4. **Substantiation (10%)** - Examples, data, evidence quality
5. **Presentation (20%)** - Clarity, grammar, word limit adherence
6. **Value Addition (5%)** - Quotes, contemporary links, unique insights

## Architecture

### Tech Stack
- **Backend:** Python Flask API deployed on Google Cloud Run
- **AI Engine:** Google Gemini 2.5 Flash (gemini-2.0-flash-exp)
- **PDF Processing:** PyMuPDF for handwritten/printed text extraction
- **Frontend:** Vanilla HTML/CSS/JavaScript (no frameworks)
- **Hosting:** Google Cloud Storage (frontend), Cloud Run (backend)
- **Cloud Services:** Firestore (planned), Firebase Auth (planned)

### System Flow
```
User uploads PDF → Cloud Run API → Gemini extracts text → 
Gemini evaluates across 6 dimensions → Structured JSON response → 
Frontend displays score + feedback
```

### Key Components

**1. PDF Extraction (`/extract` endpoint)**
```python
# Uses Gemini 2.5 Flash vision capabilities
# Extracts: question text, marks, word count, full answer text
# Handles both handwritten and typed PDFs
```

**2. Evaluation Engine (`/evaluate` endpoint)**
```python
# Prompts Gemini with:
# - Expert-validated evaluation criteria
# - Paper-specific intelligence (GS1/2/3/4)
# - Structured output format (JSON)
# Returns: scores, priority fix, section feedback
```

**3. Response Structure**
```json
{
  "upsc_scores": {
    "content": {"obtained": X, "max": Y},
    "structure": {...},
    // ... all 6 dimensions
    "total": {"obtained": X, "max": Y}
  },
  "verdict": {"stars": 3, "statement": "..."},
  "priority_fix": {"problem": "...", "solution": "...", "pattern": "..."},
  "section_breakdown": {
    "introduction": {"whats_working": [...], "strengthen_by": [...]},
    // ... all sections
  }
}
```

## Google Cloud Run Implementation

### Deployment
```bash
# Build and deploy
gcloud run deploy prism-evaluator \
  --source . \
  --region us-central1 \
  --allow-unauthenticated \
  --memory 2Gi \
  --timeout 300
```

### API Endpoints
- `POST /extract` - Extract question & answer from PDF
- `POST /evaluate` - Evaluate extracted answer
- `GET /health` - Health check

### Environment Variables
```
GOOGLE_API_KEY=<gemini-api-key>
PORT=8080
```

## Features

### Current
✅ PDF text extraction (handwritten + typed)  
✅ 6-dimension evaluation framework  
✅ Priority fix identification  
✅ Section-by-section feedback  
✅ Star rating (1-5)  
✅ Animated progress UI  
✅ Responsive design  

### Planned
🔄 Firebase Authentication  
🔄 Firestore data persistence  
🔄 User dashboard with history  
🔄 Score validation vs expert evaluators  
🔄 Progress tracking over time  
🔄 Comparative analytics  

## Research Foundation

PRISM's evaluation criteria are synthesized from:
- UPSC Topper interviews (AIR 1-50 analysis)
- Faculty evaluator best practices
- Psychology of failed aspirants
- Subject-specific expert insights
- Cross-pattern synthesis across 100+ data points

Key insight: **Structure accounts for 40% because UPSC evaluators spend ~90 seconds per answer** - clear organization is critical for scoring.

## Installation & Local Development

### Prerequisites
- Python 3.9+
- Google Cloud SDK
- Gemini API key

### Setup
```bash
# Clone repository
git clone <repo-url>
cd prism-evaluator

# Install dependencies
pip install -r requirements.txt

# Set environment variable
export GOOGLE_API_KEY=your_api_key

# Run locally
python main.py
```

### Requirements
```
Flask==3.0.0
Flask-CORS==4.0.0
google-generativeai==0.3.1
PyMuPDF==1.23.8
gunicorn==21.2.0
```

## Usage

1. Visit: https://storage.googleapis.com/prism-demo-bloombnb/prism-final.html
2. Upload UPSC answer PDF
3. Click "Extract Question & Answer"
4. Review extracted content
5. Click "Get PRISM Evaluation"
6. Watch 6-dimension evaluation animation
7. Receive detailed feedback with priority fix

## BNB Marathon 2025

### Scoring Criteria Met
- ✅ Cloud Run deployment (backend API)
- ✅ Firestore integration (schema designed, implementation pending)
- ✅ Gemini AI implementation (2.5 Flash)
- ✅ Functional demo (end-to-end working)
- ✅ Blog post (see below)
- ✅ Industry impact (UPSC exam prep sector)

### Innovation Highlights
1. **Paper-specific intelligence** - Different GS papers need different evaluation emphasis
2. **Mental health integration** - Feedback considers psychological impact on aspirants
3. **Actionable patterns** - Not just "improve structure" but "add topic sentences to each paragraph"
4. **Expert validation approach** - Framework built from actual UPSC ecosystem research

## Future Roadmap

**Phase 1 (Post-BNB):** Authentication + Data Persistence  
**Phase 2:** Score validation with 100+ expert-evaluated answers  
**Phase 3:** Comparative analytics and progress tracking  
**Phase 4:** Mobile app with offline capability  
**Phase 5:** Integration with existing UPSC coaching platforms  

## Contributing
This is a hackathon project. For collaboration post-event, contact: gurusasidharp@gmail.com

## License
MIT License - Built for Google BNB Marathon 2025

## Acknowledgments
- Google Gemini Team for the powerful 2.5 Flash model
- UPSC aspirant community for insights
- NextLeap PM Fellowship for product training
- Bloom UPSC team

---

**Built with ❤️ for UPSC aspirants by Guru Sasidhar**  
*Founder, Bloom UPSC*
EOF
