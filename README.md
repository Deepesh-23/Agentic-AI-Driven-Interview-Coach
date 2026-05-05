## AI Interview Coach Platform

Reimagining interview preparation with non-invasive AI-driven coaching and real-time posture analytics.

## Overview

This AI Interview Coach Platform is a sophisticated full-stack application that combines agentic AI orchestration with real-time posture tracking to provide comprehensive interview coaching. Instead of one-dimensional feedback, this system evaluates what you say, how you say it, and how you present yourself — all simultaneously.

Key Capabilities:

- Multi-Agent Evaluation: Parallel AI agents analyze speech patterns, posture, content quality, and emotional intelligence
- Real-Time Posture Tracking: MediaPipe analyzes body language and eye contact in real-time, running entirely client-side
- Three Coaching Modes: Interview Practice, Debate Training, and Self-Introduction coaching
- Performance Dashboard: Track progress across multiple sessions with historical analytics
- Secure Authentication: JWT-based user authentication with encrypted data storage
- Intelligent Intent Routing: NLP-based routing to automatically direct users to the appropriate coaching mode

---

## System Architecture

Session Input (Audio & Posture Data) + Chat History
↓
Data Preprocessing & Extraction
↓
Feature Integration
↓
Multi-Agent Processing (Parallel Execution)
↓
Synthesis & Score Aggregation
↓
Confidence Classification (Low / Medium / High)
↓
Personalized Coaching Report

Component Breakdown:

Speech Agent:
- Analyzes pacing, clarity, filler words
- Calculates words-per-minute and speech patterns
- Detects tone and confidence levels

Posture Agent:
- Evaluates eye contact and body alignment
- Scores hand gestures and physical engagement
- Analyzes facial expressions

Content Agent:
- Grades factual accuracy and argument structure
- Evaluates logical flow and technical depth
- Assesses clarity of explanations

---

## Tech Stack

Languages and Tools:
- Python 3.10+, SQLite, JavaScript (React), FastAPI

Backend Libraries:
- FastAPI 0.104+ for REST API framework
- LangGraph 0.2+ for AI agent orchestration
- LangChain 0.3+ for language model integration
- Google Generative AI for Gemini API access
- PyJWT and bcrypt for authentication
- Pandas and NumPy for data processing
- TextStat for text analysis
- Pydantic for data validation
- Pytest for testing
- Uvicorn as ASGI server

Frontend Libraries:
- React 18.2+ with JSX support
- Vite 4.4+ for build tooling
- React Router DOM 6.22+ for navigation
- MediaPipe Pose SDK for pose detection
- MediaPipe Face Mesh for facial tracking
- MediaPipe Camera Utils for camera access
- TensorFlow.js for machine learning in browser
- COCO-SSD model for object detection
- Recharts 2.12+ for data visualization

Infrastructure:
- Google Gemini API for content evaluation
- Web Audio API for real-time audio capture
- SQLite database for session persistence
- JWT-based authentication system

Hardware Requirements:
- Minimum 8GB RAM
- Modern web browser with WebGL support
- Webcam for posture tracking
- Microphone for audio capture

---

## Core Modules and Features

Multi-Agent Evaluation Engine:
The LangGraph orchestrator coordinates three specialized agents that run in parallel:

Speech Analysis Agent:
- Measures words-per-minute (WPM)
- Detects filler words and Speech patterns
- Analyzes tone and confidence levels
- Calculates speech clarity scores

Posture and Body Language Agent:
- Eye contact detection using MediaPipe Face Mesh
- Body posture analysis using MediaPipe Pose (33 landmarks)
- Hand gesture and movement detection
- Physical engagement and composure scoring

Content Quality Agent:
- Factual accuracy evaluation using Gemini LLM
- Argument structure and logical flow analysis
- Technical depth assessment
- Clarity of explanations grading

Feature Integration and Synthesis:
- Combines biometric and analytical data
- Aggregates multi-modal scores with weighted averaging
- Generates unified confidence classification
- Produces actionable feedback and recommendations

---

## Key Components

Backend Services:

Audio Service:
- Real-time audio capture from browser
- Audio transcription and analysis
- Speech pattern extraction

Content Analysis Service:
- LLM-powered by Google Gemini API
- Factual accuracy grading
- Response quality evaluation

Emotion Service:
- Tone detection from speech
- Confidence level analysis
- Emotional engagement scoring

Evaluation Service:
- Score aggregation from all agents
- Weighted scoring calculation
- Overall performance grading

NLP Service:
- Text processing and cleaning
- Linguistic metric calculation
- Feature extraction from transcripts

Frontend Components:

AudioRecorder:
- WebAudio API integration
- Real-time recording control
- Audio quality monitoring

LivePostureTracker:
- MediaPipe Pose model initialization
- Real-time pose detection and visualization
- Landmark tracking and analysis

EvaluationReport:
- Score visualization and display
- Feedback presentation
- Performance metrics charts

---

Prerequisites:
- Node.js v18 or higher with npm
- Python 3.10 or higher
- Google Gemini API Key (available free at aistudio.google.com)
- Web browser with WebGL support
- Webcam and microphone

Setup Instructions:

1. Clone and Configure:
   git clone https://github.com/<your-username>/AI-Interview-Coach-Platform.git
   cd AI-Interview-Coach-Platform
   cp .env.example .env

2. Add Environment Variables to .env:
   GOOGLE_API_KEY=your_gemini_api_key_here
   JWT_SECRET_KEY=your_jwt_secret_key_here

   Generate JWT secret: python -c "import secrets; print(secrets.token_hex(32))"

3. Start Backend Server:
   python -m venv backend/venv
   
   On Windows:
   backend\venv\Scripts\activate
   
   On macOS/Linux:
   source backend/venv/bin/activate
   
   pip install -r requirements.txt
   python run_backend.py

   Backend API will run at: http://localhost:8000

4. Start Frontend Application:
   cd frontend
   npm install
   npm run dev

   Frontend will run at: http://localhost:5173

5. Access the Application:
   - Open http://localhost:5173 in your web browser
   - Create a new account with email and password
   - Begin your first coaching session

---

## Running Individual Modules

The backend is organized into modular components that can be tested independently:

Core Services (Python modules):
- Audio transcription and processing
- Content analysis with LLM
- Emotion and tone detection
- Evaluation and score aggregation
- NLP utilities and text processing

Frontend Components (React):
- Audio recording interface
- Posture tracking visualization
- Session participation UI
- Results and evaluation display

Testing Each Module:

Run all tests:
pytest tests/ -v

Run unit tests only:
pytest tests/test_unit.py -v

Run integration tests:
pytest tests/test_integration.py -v

Run system tests:
pytest tests/test_system.py -v

Run service-specific tests:
pytest tests/test_services.py -v

---

System Workflow:

1. Create Account:
   Sign up with email and password on the login page

2. Describe Your Goal:
   Tell the AI what you want to practice
   Example: "I want to practice for a software engineer interview"

3. Start Session:
   The system automatically routes you to the appropriate coaching mode based on your request

4. Participate in Session:
   Answer questions from the AI coach while your posture and audio are analyzed in real-time

5. Receive Evaluation:
   After the session ends, you will receive:
   - Overall confidence score (0-100)
   - Speech score (pacing, clarity, filler words)
   - Posture score (eye contact, body alignment, gestures)
   - Content score (accuracy, logic, depth)
   - Personalized feedback and actionable recommendations

6. Track Progress:
   View your performance dashboard to see:
   - Historical session data
   - Improvement trends
   - Comparative analytics across different session types

Coaching Modes:

Interview Mode:
- Role-specific questions based on job title
- Realistic interview scenarios
- Performance metrics relevant to hiring decisions
- Real-time feedback on communication and presentation

Debate Mode:
- Argumentative reasoning evaluation
- Counter-argument handling analysis
- Logical structure assessment
- Rhetorical effectiveness scoring

Self-Introduction Mode:
- Personal branding evaluation
- Story narrative quality assessment
- Professional pitch effectiveness analysis
- Confidence and clarity metrics

---

## Testing

Running Tests:

Navigate to backend directory:
cd backend

Activate virtual environment:
On Windows:
backend\venv\Scripts\activate

On macOS/Linux:
source venv/bin/activate

Run all tests:
pytest tests/ -v

Run specific test file:
pytest tests/test_unit.py -v

API Documentation:
Access interactive API documentation at http://localhost:8000/docs
(when backend server is running)

---
