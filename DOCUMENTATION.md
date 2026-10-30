# AgriNova AI — Project Documentation

## 1. Project summary
AgriNova AI is a Kinyarwanda-first, AI-assisted agriculture web application prototype designed to help farmers in Rwanda ask questions about crop production and describe visible crop problems. Users can select a crop, optionally enter their location, type a question, and upload a crop photo for preliminary AI-assisted observations.

- Competition: NISR Big Data Hackathon 2026
- Track: Track 1 — Agricultural Productivity
- Team: AgriNova Rwanda
- Members: Innocent BIZIMANA and GAD Tuyisege
- Live application: https://agrinova-ai-9hzv.onrender.com
- Repository: https://github.com/it-mula/agrinova-ai

## 2. Problem being addressed
Farmers can face delays in accessing understandable agricultural information, particularly when they notice crop symptoms or need to know what to check next. Language and access barriers can make it harder to describe a problem and seek timely guidance.

AgriNova AI aims to provide an accessible first point of information in Kinyarwanda. It is intended to support—not replace—local agronomists, farmer extension services, and official agricultural guidance.

## 3. Proposed solution and users
The solution is a browser-based chat assistant for farmers and other people seeking basic crop-related information. The user can:
1. Select a crop from the available list.
2. Optionally enter a district or sector.
3. Ask an agriculture question in Kinyarwanda.
4. Optionally attach a crop image.
5. Read the AI-generated response and its stated source/uncertainty notes.

## 4. Main features in the current prototype
- Kinyarwanda-oriented conversational interface.
- Crop selection and optional location field.
- Crop photo upload.
- AI-assisted analysis of the photo and user's description.
- Conversation history during the current session.
- Curated JSON knowledge base with links to public RAB resources.
- Prompt safeguards intended to reduce unsupported diagnosis and unsafe chemical advice.
- Publicly deployed web application.

This list describes the current prototype, not unimplemented future capabilities.

## 5. Technical architecture
1. The farmer enters a question and optional crop/location/photo in the Gradio interface.
2. The Python application prepares the prompt and relevant reference notes from knowledge_base.json.
3. The application sends the request to a Google Gemini model through the Google GenAI Python SDK.
4. The model returns a response in Kinyarwanda.
5. The Gradio interface displays the response.

Main components:
- app.py: interface, input handling, prompt rules, model calls, and response display.
- knowledge_base.json: source metadata, agriculture notes, and assistant safety rules.
- requirements.txt: Python package dependencies.
- Render: hosting/deployment platform.
- Google Gemini API: language and image-capable AI service used by the prototype.

## 6. Data and knowledge sources
The knowledge base contains links and selected notes from public RAB materials:
- RAB Crop Innovation and Technology Transfer: https://www.rab.gov.rw/agriculture-development/crop-innovation-tech-transfer
- RAB Cereals Program: https://www.rab.gov.rw/rw/amakuru-1/cereals-program
- RAB Pulses and Oil Crops / crop innovation information: https://www.rab.gov.rw/rw/agriculture-development/crop-innovation-tech-transfer
- RAB Roots and Tubers Program: https://www.rab.gov.rw/rw/amakuru-1?cHash=7f36faa29f0503bf13408e15cb62d418&tx_news_pi1%5Baction%5D=detail&tx_news_pi1%5Bcontroller%5D=News&tx_news_pi1%5Bnews%5D=29254
- RAB Crop Protection Program: https://www.rab.gov.rw/1-1/news/crop-protection-program
- Rwanda Digital Soil Information System (RwaSIS): https://rwasis.rab.gov.rw/
- RAB Annual Report 2023–2024: https://www.rab.gov.rw/fileadmin/user_upload/RAB/Publications/Reports/RAB_Annual_2023-24.pdf
- Agenda Agricole 2023: https://www.rab.gov.rw/fileadmin/user_upload/RAB/Publications/Policies_and_strategies/Agenda_Agricole_2023.pdf
- RAB Annual Report 2019–2020: https://www.rab.gov.rw/fileadmin/user_upload/RAB/Publications/Reports/RAB_annual_2019-2020.pdf

These references provide background and selected facts; they do not verify every answer produced by the AI. The prototype also displays NISR figures, but it does not claim to perform a complete statistical analysis or prediction using all NISR datasets. Further integration and validation with relevant NISR datasets is future work.

## 7. Responsible AI and safety
The application prompt includes safeguards:
- Respond in clear Kinyarwanda.
- Do not invent local soil, weather, yield, or disease information.
- Distinguish visible symptoms from suspected causes.
- Do not confirm a disease from a single photo.
- Do not invent pesticide names, application rates, fertilizer quantities, or planting intervals.
- Ask a clarifying question when information is insufficient.
- Recommend consultation with an agronomist or RAB when the issue is serious or spreading.
- Identify knowledge-base sources only when they actually support the point being made.

## 8. Installation and local execution
Requirements: Python 3.10 or later and a Google Gemini API key.

```bash
git clone https://github.com/it-mula/agrinova-ai.git
cd agrinova-ai
pip install -r requirements.txt
```

Set the environment variable GEMINI_API_KEY securely before starting the app.

Windows PowerShell:
```powershell
$env:GEMINI_API_KEY="YOUR_API_KEY"
python app.py
```

macOS/Linux:
```bash
export GEMINI_API_KEY="YOUR_API_KEY"
python app.py
```

Never put the API key in source code, documentation, screenshots, or public commits. The app uses the local port configured by the environment (default 10000).

## 9. Deployment
The project is deployed on Render: https://agrinova-ai-9hzv.onrender.com

The service installs dependencies from requirements.txt and runs app.py. The Gemini key is configured as a private environment variable in the hosting service and must never be published in the repository.

A free hosting instance may sleep when inactive, so its first request after inactivity can take longer.

## 10. Testing and current limitations
The prototype has been manually tried through its deployed interface, including text questions and crop-photo input. AI response quality and response time depend on model availability, network connectivity, and API limits.

Known limitations:
- AI responses can be inaccurate and require expert verification.
- A single image may not provide enough evidence for disease identification.
- The knowledge base is curated but not exhaustive and may not contain the latest local recommendations.
- Location input is user-provided; the app does not independently verify the farmer's field.
- The prototype does not guarantee real-time weather, soil measurements, market prices, or yield forecasts.
- It is not a substitute for official extension services.

## 11. Future improvements
- Expand validation with agronomists and RAB extension officers.
- Add more verified crop-specific knowledge and local-language guidance.
- Integrate appropriate NISR datasets and clearly document the variables and analysis.
- Add validated weather and market information where reliable public data are available.
- Improve response speed, monitoring, accessibility, and low-bandwidth mobile use.
- Collect structured user feedback to measure usefulness and identify errors.

## 12. Team and AI-use disclosure
Team name: AgriNova Rwanda  
Project: AgriNova AI  
Team members: Innocent BIZIMANA and GAD Tuyisege

AI tools were used as assistants during development and documentation. The team remains responsible for checking the code, testing the application, validating claims and sources, and ensuring that the submitted project accurately represents the work completed by the team.
