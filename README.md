# AgriNova AI

**An AI-assisted agriculture information and advisory prototype for farmers in Rwanda.**

AgriNova AI is a Kinyarwanda-first web application that helps farmers describe crop problems, ask practical agriculture questions, and optionally share a crop photo for preliminary visual analysis.

- **Live application:** https://agrinova-ai-9hzv.onrender.com
- **Source code:** https://github.com/it-mula/agrinova-ai
- **Hackathon track:** NISR Big Data Hackathon 2026 — Track 1: Agricultural Productivity
- **Team:** AgriNova Rwanda
- **Team members:** Innocent BIZIMANA and GAD Tuyisege

## The problem
Farmers may have difficulty getting timely, understandable agricultural information, especially when crop symptoms appear or they need guidance on the next step. AgriNova AI provides a simple Kinyarwanda interface through which a farmer can ask questions and share a crop image.

## Current prototype features
- Kinyarwanda-oriented chat interface.
- Crop selection and optional district/sector field.
- Crop photo upload for preliminary AI-assisted visual observations.
- Curated agriculture knowledge file with references to RAB resources.
- Safety instructions to distinguish visible symptoms from possible causes and avoid unsupported pesticide/fertilizer dosages.
- Conversation history during the current session.

## Technology
Python, Gradio, Google Gemini API (google-genai), Pillow, and a JSON knowledge base.

## Run locally
1. Install Python 3.10 or later.
2. Clone this repository:
   ```bash
   git clone https://github.com/it-mula/agrinova-ai.git
   cd agrinova-ai
   ```
3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
4. Set your Gemini API key as an environment variable named GEMINI_API_KEY. Never commit API keys to GitHub.
5. Start the application:
   ```bash
   python app.py
   ```
6. Open the local URL shown in the terminal (usually http://127.0.0.1:10000).

## Repository structure
- app.py — Gradio web application and AI interaction logic.
- knowledge_base.json — agriculture reference notes, source links, and safety rules.
- requirements.txt — Python dependencies.
- DOCUMENTATION.md — project, methodology, limitations, and usage documentation.

## Data and reference sources
The knowledge base links to public agriculture resources from the Rwanda Agriculture and Animal Resources Development Board (RAB), including:
- [RAB Crop Innovation and Technology Transfer](https://www.rab.gov.rw/agriculture-development/crop-innovation-tech-transfer)
- [RAB Cereals Program](https://www.rab.gov.rw/rw/amakuru-1/cereals-program)
- [RAB Crop Protection Program](https://www.rab.gov.rw/1-1/news/crop-protection-program)
- [Rwanda Digital Soil Information System (RwaSIS)](https://rwasis.rab.gov.rw/)
- [Agenda Agricole 2023](https://www.rab.gov.rw/fileadmin/user_upload/RAB/Publications/Policies_and_strategies/Agenda_Agricole_2023.pdf)
- [RAB Annual Report 2023–2024](https://www.rab.gov.rw/fileadmin/user_upload/RAB/Publications/Reports/RAB_Annual_2023-24.pdf)

The current prototype includes NISR figures in its web interface and RAB reference material in its knowledge base. It does not claim that every AI response is statistically validated by NISR.

## Important limitations
AgriNova AI is a prototype, not a certified diagnostic system and not a replacement for an agronomist or RAB extension officer. A photo or short description may not be enough to identify a crop disease. AI-generated answers can be wrong. Users should verify important decisions locally, especially before applying fertilizer or pesticides. The prototype does not guarantee live weather, soil-test results, or market prices.

## AI-use disclosure
AI tools were used as development and assistance tools in preparing parts of this prototype and its documentation. The team is responsible for reviewing, testing, and validating all submitted work and references.

## Team
**AgriNova Rwanda** — Innocent BIZIMANA and GAD Tuyisege
