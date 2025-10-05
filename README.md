# Unified Hazard Reporter

Unified Hazard Reporter is a full-stack web application designed for detecting and reporting hazards. The frontend provides a user-friendly interface for manual incident reporting and live hazard detection, while the backend leverages the Google Gemini API for comprehensive multimodal analysis.

---

## ✨ Features

### Frontend (Client-Side)
**Single-Page Application**: Switch seamlessly between the Image Analyzer and Live Hazard Detection Stream.

#### Image Analyzer
- **Manual Reporting**: Submit detailed reports including title, description, and contact information.
- **Multimodal Input**: Capture images from the camera or upload local files.
- **Geolocation**: Automatically captures the user's latitude and longitude.

#### Live Hazard Detection Stream
- **Real-Time Video**: Access device camera for a live feed.
- **Chunked Recording**: Video recorded in small clips sent automatically to the backend.
- **Real-Time Alerts**: "Hazard detected" badge appears based on backend analysis.
- **Controls**: Start/stop recording, switch cameras, mute, download/upload clips manually.

---

## ⚙️ Technology Stack

**Frontend:** HTML, CSS, JavaScript, Single-Page Application (SPA)  
**Backend:** Node.js, Express.js, Google Gemini API, Mongoose, MongoDB  
**Other:** dotenv for environment variable management

---

## 🌐 Deployment

- **Frontend:** [https://parth-gupta05.github.io/AI-video-Analyzer/](https://parth-gupta05.github.io/AI-video-Analyzer/)  
- **Backend:** [https://model-forge-idfe.onrender.com](https://model-forge-idfe.onrender.com)

### GitHub Repositories
- **Frontend:** [https://github.com/Parth-Gupta05/AI-video-Analyzer.git](https://github.com/Parth-Gupta05/AI-video-Analyzer.git)  
- **Backend:** [https://github.com/Shreevathsa05/Ai-based-Hazard-Analyzer.git](https://github.com/Shreevathsa05/Ai-based-Hazard-Analyzer.git)

---

## ⚙️ API Routes

The frontend interacts with the backend using the following endpoints:

| Method | Route               | Description |
|--------|-------------------|-------------|
| POST   | `/api/report`       | Submit image-based hazard report. Accepts base64 image with title, description, contact info. Returns JSON with threat level, required services, and incident description. |
| POST   | `/api/detect`       | Send video clips for hazard detection. Accepts base64 video. Returns JSON with hazard status and required emergency services. |
| GET    | `/api/reports`      | Fetch all manually submitted reports. |
| GET    | `/api/detections`   | Fetch all automated hazard detection logs from video analysis. |
| GET    | `/api/alerts`       | Fetch local alert messages. |
| POST   | `/api/alerts`       | Create a new local alert message. |
| DELETE | `/api/alerts/:id`   | Delete a specific local alert message by ID. |

> **Note:** All requests are automatically routed to the deployed backend URL (`https://model-forge-idfe.onrender.com`) from the frontend.

---

## 🚀 Running the Frontend Locally

1. Clone the frontend repository:
```bash
git clone https://github.com/Parth-Gupta05/AI-video-Analyzer.git
cd AI-video-Analyzer
