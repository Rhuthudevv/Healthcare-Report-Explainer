<img width="2879" height="1525" alt="Screenshot 2026-05-09 165123" src="https://github.com/user-attachments/assets/74017de7-0700-4a4d-9620-0a0e065fd7cc" />


# Medical Imaging and Lab Report Explainer AI (Local Version)

A secure, offline AI application that analyzes medical reports (PDF/Text) and generates clear explanations tailored for both **Patients** (simplified language) and **Clinicians** (technical summary).

> **Privacy Focused**: This application runs entirely on your local machine using **GPT4All**. No medical data is sent to external servers or APIs (like OpenAI).

![Application Screenshot](https://via.placeholder.com/800x400?text=Medical+Explainer+AI+Preview)

## 🌟 Key Features

*   **Dual-Mode Explanations**:
    *   **Patient Mode**: Breaks down complex terms into everyday language, explains implications, and suggests questions for doctors.
    *   **Clinician Mode**: Provides a concise, technical bullet-point summary with key findings and critical values.
*   **Fully Local AI**: Uses the **Phi-3 Mini** model (via GPT4All) for high-speed, efficient, and offline inference.
*   **Smart Extraction**: Parses PDF and Text files to identify findings, impressions, and abnormal values.
*   **Citation System**: Automatically links medical terms to trustworthy sources (e.g., NIH, Mayo Clinic).
*   **Accessible Design**: High-contrast UI, screen-reader friendly (ARIA support), and keyboard navigable.

## 🛠️ Tech Stack

*   **Backend**: Python, FastAPI
*   **AI Engine**: GPT4All (Phi-3 Mini 4K Instruct)
*   **Frontend**: HTML5, CSS3, JavaScript (Vanilla)
*   **PDF Processing**: PDF.js (Client-side extraction)

## 📋 Prerequisites

*   **Python 3.10** or higher.
*   **RAM**: At least 4GB (8GB recommended for optimal performance).
*   **Disk Space**: ~2.5GB free space (for the AI model file).
*   **Optional**: A GPU (NVIDIA/AMD) for accelerated inference (Vulkan support is automatic).

## 🚀 Installation & Setup

### 1. Clone the Repository
```bash
git clone https://github.com/abhishekpoyyeri/Healthcare-Report-Explainer.git
cd Healthcare-Report-Explainer
```

### 2. Install Dependencies
It is recommended to use a virtual environment.
```bash
# Create virtual env
python -m venv venv

# Activate (Windows)
venv\Scripts\activate

# Activate (Mac/Linux)
source venv/bin/activate

# Install requirements
pip install -r backend/requirements.txt
```

## 🏃‍♂️ How to Run

### 1. Start the Backend Server
Run the following command from the project root:

```bash
python -m uvicorn backend.main:app --port 8000
```

> **⚠️ Important First-Run Note**:
> When you run this for the first time, the application will automatically download the AI model file (`Phi-3-mini-4k-instruct.Q4_0.gguf`, approx. 2.4 GB).
>
> **Please wait** until you see the message: `Application startup complete`.

### 2. Access the Application
Open your web browser and navigate to:
**http://localhost:8000**

## 📖 Usage Guide

1.  **Upload a Report**:
    *   Click **"Select File"** to upload a PDF or TXT medical report.
    *   OR paste text directly into the text area.
    *   *Sample reports are available in the `backend/sample_reports/` folder.*
2.  **Analyze**:
    *   Click the **"Explain Report"** button.
    *   *Note: With Phi-3, analysis is significantly faster (typically <10 seconds on modern hardware).*
3.  **View Results**:
    *   Toggle between **"Patient Mode"** and **"Clinician Mode"** tabs to see different perspectives.
    *   Check the "Trusted Sources" section for definitions of medical terms.

## 📂 Project Structure

```
├── backend/
│   ├── main.py              # FastAPI entry point
│   ├── local_ai_engine.py   # GPT4All wrapper & model loader (Optimized for Phi-3)
│   ├── pipeline.py          # Orchestrates Extraction -> Formatting
│   ├── extractor.py         # Structured data extraction logic
│   ├── formatter.py         # Generation of explanations
│   ├── knowledge_base.py    # Dictionary of medical terms & citations
│   ├── requirements.txt     # Python dependencies
│   └── sample_reports/      # Synthetic test data
├── frontend/
│   ├── index.html           # Main UI
│   ├── style.css            # Styling & Accessibility
│   └── script.js            # Frontend logic & API calls
├── test_demo.py             # CLI script for testing without browser
└── README.md                # Project documentation
```

## ⚠️ Disclaimer
**This tool is for educational and informational purposes only.**
It does **NOT** provide medical advice or diagnosis. Always consult a qualified healthcare professional for medical concerns. The AI may occasionally produce incorrect information (hallucinations).
