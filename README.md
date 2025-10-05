# Unified Hazard Reporter

Unified Hazard Reporter is a full-stack web application designed for detecting and reporting hazards. The frontend provides a user-friendly interface for manual incident reporting and live hazard detection, while the backend leverages the Google Gemini API for comprehensive multimodal analysis.

---

## ✨ Features

### Frontend (Client-Side)
**Single-Page Application**: A unified interface with tabs to switch seamlessly between the Image Analyzer and the Live Hazard Detection Stream.

#### Image Analyzer
- **Manual Reporting**: Users can submit detailed incident reports including title, description, and contact information.
- **Multimodal Input**: Capture images directly from the device camera or upload from local files.
- **Geolocation**: Automatically captures and displays the user's location (latitude and longitude).

#### Live Hazard Detection Stream
- **Real-Time Video**: Accesses the device's camera to provide a live video feed.
- **Chunked Recording**: Video is recorded in small clips and automatically sent to the backend for processing.
- **Real-Time Alerts**: A "Hazard detected" badge is displayed based on backend analysis.
- **Controls**: Start/stop recording, switch between front and rear cameras, mute video, and manually download/upload clips.

---

## ⚙️ Backend Logic & Technology Stack

The backend is built with Node.js and Express, acting as a secure intermediary between the frontend and the Google Gemini API.

### Core Technologies
- **Node.js & Express**: Server-side environment and web framework.
- **Google Gemini API**: Multimodal AI model for image and video analysis.
- **Mongoose**: ODM for MongoDB with schema-based data modeling.
- **MongoDB**: NoSQL database for storing reports and detection logs.
- **dotenv**: Manages environment variables, keeping sensitive information secure.

### Backend Functionality
- **Request Handling**: Express server handles POST requests with base64-encoded images or video clips.
- **Gemini API Integration**:
  - **Image Analysis (`/api/report`)**: `ReportAnalyzer` in `OtherAiModels.js` sends image and text data to `gemini-2.5-flash`. Returns a JSON object detailing threat level, required services, and incident description.
  - **Video Analysis (`/api/detect`)**: `getRes` in `GeminiVideoAnalyzer.js` sends video clips for hazard detection. Response includes hazard status and emergency services required.
- **Database Operations**: CRUD endpoints for MongoDB collections.
  - **ReportModel**: Stores detailed image analyzer reports.
  - **HazardDetectionResponseModel**: Logs automated video detection responses.
  - **LocalAlerts**: Separate collection for local alert messages.
- **Data Security**: Google API key is stored securely in a `.env` file and never exposed on the client-side.

---

## 🚀 How to Run

### Prerequisites
- **Node.js**: Version 18 or later
- **MongoDB**: Local or cloud-hosted instance (e.g., MongoDB Atlas)
- **Google AI Platform Account**: Access to the Gemini API with an API key

### Setup Steps
1. **Clone the repository**
```bash
git clone [[repository-url](https://github.com/Shreevathsa05/Ai-based-Hazard-Analyzer.git)]
cd backend
```

2. **Install dependencies**
```bash
npm install
```

Configure environment variables

Create a .env file in the root directory:
```
MONGO_URL="your_mongodb_connection_string"
GOOGLE_API_KEY="your_gemini_api_key"
PORT=3000
```

Run the backend server
```
node index.js
```

Run the frontend

Open index.html in a modern web browser.

The frontend will automatically connect to the backend server.
