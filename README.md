# Prism - AI-Powered UPSC Mains Answer Evaluator

**Part of Bloom UPSC | Built for BNB Marathon 2025**

## What is Prism?
Prism is an AI-powered evaluation engine that provides instant, actionable feedback on UPSC Civil Services Mains answers using a 6-dimensional framework. It reduces evaluation time from 72 hours to 30 seconds while providing paper-specific, expert-validated feedback.

## The Problem
- 10 lakh+ UPSC aspirants need quality feedback
- Traditional test series take 24-72 hours
- Generic feedback like "improve content depth" is useless
- 53% of aspirants struggle with mental health

## The Solution - 6 Core Differentiators
1. **6-Layer Autopsy Framework**: Content, Structure, Analysis, Substantiation, Presentation, Value Addition
2. **Paper-Specific Intelligence**: Different rubrics for GS1/2/3/4
3. **Actionable Feedback**: Specific fixes, not generic comments
4. **Mental Health Integration**: Weekly check-ins, score drop detection
5. **Day 1 Writing Enforcement**: Start writing from Day 1
6. **Progressive Pathways**: Beginner/Intermediate/Advanced adaptation

## Tech Stack
- **AI**: Gemini 2.5 Flash (PDF OCR + Structured Evaluation)
- **Backend**: Firebase (Auth, Storage, Firestore)
- **Frontend**: React
- **Deployment**: Cloud Run

## Demo Features (Built in 2 Days)
✅ Upload handwritten answer PDF  
✅ 30-second OCR + evaluation  
✅ Paper-specific scoring (GS1 vs GS2 vs GS3 vs GS4)  
✅ 6-dimensional feedback with actionable items  
✅ Progress tracking visualization  
✅ Mental health check-in integration  

## Quick Start
[Installation instructions]

## Project Structure
[Explain your folder structure]

## Author
Guru Sasidhar | 4 UPSC Attempts | NextLeap PM Fellow
```

### 3. **File Structure Should Be Self-Explanatory**

Rename files/folders to be crystal clear:

❌ Bad structure:
```
/src
  /components
  /utils
```

✅ Good structure:
```
/src
  /evaluation-engine       # Core AI evaluation logic
  /pdf-ocr                # Gemini PDF processing
  /feedback-generator     # 6-layer framework implementation
  /mental-health         # Check-in and intervention system
  /paper-specific-rubrics # GS1/2/3/4 evaluation criteria
  /components            # React UI components
