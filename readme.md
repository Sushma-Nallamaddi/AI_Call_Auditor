# AI Call Auditor

**AI Call Auditor** is a comprehensive, enterprise‑grade quality assurance platform that automates the evaluation of customer support interactions. Using advanced Generative AI, Retrieval‑Augmented Generation (RAG), and scalable NLP techniques, it audits both audio calls and chat logs against company policy to produce detailed quality scores, compliance insights, and formal reports.

The system is designed to help support teams, QA analysts, and compliance managers reduce manual review workload and improve customer experience through accurate, context‑aware automated auditing.

## Features

**Multi‑Format Support**  
Supports upload and analysis of audio files (`.mp3`, `.wav`) and chat logs (`.txt`, `.json`).

**Automated Transcription & Diarization**  
High‑accuracy speech‑to‑text conversion using OpenAI Whisper and speaker diarization via Senko, optimized for CPU or GPU environments.

**Policy‑Aware Auditing (RAG)**  
Retrieves relevant sections from company policy documents using LangChain with FAISS vector store to ensure contextual accuracy during audits.

**LLM‑Powered Analysis**  
Uses Google Gemini (`gemini‑3‑flash‑preview`) for detailed evaluation of interactions including empathy, clarity, professionalism, resolution quality, and compliance.

**Automated Reporting**  
Generates structured PDF audit reports summarizing findings and quality scores.

**Critical Alerts**  
Triggers automated alerts for low‑scoring interactions (e.g., scores below 30), optionally sent to managers via email.

**Audit History Tracking**  
Stores all audit results and metadata in a local SQLite database for historical tracking and trend analysis.

**Policy Management**  
Enables viewing and updating of active company policy within the interface. The RAG engine re‑indexes updated policies automatically on the next audit run.

AI‑Call‑Auditor/
├── app.py # Main Streamlit application entry point
├── requirements.txt # Python dependencies
├── .env # Environment variables (API keys)
├── policies/ # Policy document directory
│ └── company_policy.txt # Default policy document
├── src/ # Core source modules
│ ├── audio_processor.py # STT & diarization logic
│ ├── auditor.py # LLM audit interaction logic
│ ├── chat_normalizer.py # Chat log parsing logic
│ ├── database_manager.py # SQLite operations
│ ├── rag_engine.py # RAG implementation with FAISS
│ └── reporting.py # PDF generation and alerts
└── data/ # Generated & persistent data
├── uploads/ # Uploaded audio and logs
├── pdf‑reports/ # Generated audit reports
└── database/ # SQLite database files


## Tech Stack

* **Frontend:** Streamlit  
* **AI/LLM:** Google Gemini API, OpenAI Whisper, Senko (Diarization)  
* **RAG Framework:** LangChain + FAISS Vector Store, HuggingFace Embeddings (`all‑MiniLM‑L6‑v2`)  
* **Backend/Utils:** Python, Pandas, SQLite  
* **Reporting:** FPDF (PDF generation), SMTP (Email alerts)

## Prerequisites

* **Python 3.10+**
* **FFmpeg:** Required for audio processing

  * Windows: `winget install ffmpeg` or download and add to PATH  
  * Linux: `sudo apt install ffmpeg`  
  * Mac: `brew install ffmpeg`  

* **Google Gemini API Key:** Obtain from Google AI Studio  
* **Git:** To clone the repository

## Installation

1. **Clone the Repository**

   ```bash
   git clone <repository‑url>
   cd AI‑Call‑Auditor

2. **Create a Virtual Environment**
   python ‑m venv venv
# Windows
venv\Scripts\activate
# Mac/Linux
source venv/bin/activate

3. **Install Dependencies**
pip install ‑r requirements.txt

4. **Configure Environment Variables**
Create a .env file at the project root and add your keys:
   GEMINI_API_KEY=your_actual_api_key_here
   
**Usage**
1. **Start the Application**
   streamlit run app.py
3. **Access the Application**
   Open your browser and go to:
       http://localhost:8501
5. **Run an Audit**
    * Navigate to the “Run Audit” tab
    * Upload an audio file or chat log
    * Click Start Audit
    * Wait for the processing to complete (Transcription → RAG → Audit → Reporting)
7. **View Results**
    * Audit scores and compliance status are displayed in the UI
    * Download the detailed PDF report
    * If the score is critical, receive an alert if email config is enabled
9. **Manage History**
   *View past audits in the “Audit History” tab
   *Use sidebar options to reset or delete data

**Contributing**
Contributions are welcome. Please fork the repository and submit a pull request with a clear description of changes.

**License**
This project is licensed under the MIT License.
