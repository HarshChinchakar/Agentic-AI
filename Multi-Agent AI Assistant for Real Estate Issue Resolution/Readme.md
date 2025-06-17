# Multi-Agent Real Estate Assistant

Multiple times the preview option isnt available on git, The project is fully functional. Either download the file/ or check out the colab link
---
**Demo Link:** [https://drive.google.com/file/d/1ypPHc3rEhmYfkQ7WVRGY4yPLpTIaJ30H/view?usp=sharing]  
**Colab Link:** [https://colab.research.google.com/drive/1MChbqCnrY-6Jq49gf5qB7r_rzjZ7yxDr?usp=sharing]  

---

## Project Overview

The **Multi-Agent Real Estate Assistant** is a modular, AI-powered, real-estate-focused chatbot system with visual, audio, and text-based interaction capabilities. Designed as a production-ready solution for property issue diagnosis, reporting, and automation, the system routes user input to the right agent using a query classifier and enables follow-up actions like automated email generation, contractor recommendations, and structured report output.

The system is divided into microservices and features a **dual memory architecture**, **meta-agent control**, and seamless **mid-conversation switching** with context-awareness.

---

## System Architecture

The system follows a clean modular architecture separated into agents, routing modules, memory systems, and output services.

### 🔁 Meta-Agent Control System
- **Routing Layer** decides whether to invoke Agent 1 (visual & legal assistant) or Agent 2 (general assistant).
- Integrated **fallback control** to reassign unresolved queries to alternate agent pipelines.
- Enables **mid-conversation agent switching** without losing context.

![Meta Agent Architecture]("Multi-Agent AI Assistant for Real Estate Issue Resolution/assets/agent_architecture.png")

---

## Feature Set (Implemented)

### 1. Dual Memory System
- **Short-Term Memory (Chat)**: Maintains a thread of current conversation.
- **Long-Term Memory (Case Log)**: Stores contextually rich entries for reuse in future sessions or for documentation.

![Chat + Case Memory](assets/chat_output.png)

---

### 2. Multi-Modal Input Support
- **Agent 1**: Accepts image + voice/text input.
- **Agent 2**: Accepts voice or text input.

Text from voice is parsed using **Whisper** and routed accordingly.

![Audio Processing](assets/audio_processing.png)

---

### 3. Visual Processing & Labeling
- **Image Captioning** via BLIP model.
- **OCR** for document detection.
- **YOLO/Segformer**-based issue localization.
- Uses **overlapping segmentation** to retain context across image slices.

![Visual Labeling](assets/image_issue_highlighting.png)

---

### 4. Emotion-Aware Dialogue
- Implements **sentiment analysis** (VADER/TextBlob) to adapt tone/responses.
- Applies especially in Agent 2 to simulate empathetic dialogue.

---

### 5. Contractor Recommendation Engine
- Based on detected **location** and **issue type**, retrieves relevant contractor information.
- Includes name, contact info, and brief reference.

---

### 6. Automated Authority Email Generation
- Structured email generation based on chat logs.
- Tailors authority contact based on location and issue type.
- Includes dynamic attachments like PDFs.

![Authority Email](assets/authority_email.png)

---

### 7. Summary Document Generator
- Converts chat logs and memory into structured documents.
- Sections include: **Issue Faced**, **Recommendations**, **Troubleshooting**, **Response Summary**.
- Used for professional reporting.

![Generated Document](assets/generated_doc.png)

---

### 8. Audio/Text Output
- Option for audio output using TTS.
- Default response in text with optional voice rendering.

---

### 9. Location-Based Personalization
- Uses IP-derived or manually entered location.
- Adapts both response and contractor search accordingly.

---

### 10. Proactive Alert System *(Planned)*
- Future enhancement for weather-based reminders.
- Sends proactive emails to users based on forecast or recurring damage patterns.

---

## Microservice Architecture

System is composed of independent modules:

![Microservices](assets/microservices_module.png)

| Module | Function |
|--------|----------|
| Routing Module | Classifies and redirects queries |
| Audio Processor | Handles voice input & output |
| PDF Generator | Builds technical summary documents |
| Email Handler | Sends structured emails with attachments |
| Contractor Finder | Suggests nearby services based on issue |
| Visual Annotator | Image processing pipeline |

---

## Models Used

| Task | Model |
|------|-------|
| Voice-to-Text | Whisper Tiny/Medium |
| Image Captioning | BLIP |
| OCR | Tesseract/PaddleOCR |
| Visual Labeling | YOLOv8/Segformer |
| NER + Sentiment | spaCy, VADER, TextBlob |
| Text Generation | GPT-3.5/GPT-4 via API |
| PDF Generation | Groq Model |

---

## Routing Module

- Routes query to relevant agent using zero-shot or rule-based classification.
- Employs fallback to switch if incorrect routing occurs.

![Routing Logic](assets/routing_module.png)

---

## Frontend Interface

- Built on Streamlit.
- Supports chat-based interaction with audio/image input fields.

![UI Sample](assets/ui_sample.png)

---

## Output Snapshot

- Example of chatbot interaction.
- Includes multi-turn queries, agent switches, and visual damage analysis.

![Output Chat](assets/chat_output.png)

---

## Future Improvements

- Add **multi-user support** with user ID-based memory separation.
- Enable **real-time contractor API integrations**.
- Deploy frontend as **Progressive Web App (PWA)**.

---

## Maintainer

**Harsh Chinchakar**  
AI/ML Engineer | Final Year CSE Core  
[LinkedIn/GitHub/Email Info Here]
