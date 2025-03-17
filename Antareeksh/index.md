# Jains Antareeksh - Basic Project Documentation

## 🎯 Project Overview

**Jains Antareeksh** is an AI-powered, interactive 3D real estate walkthrough project located in **Perungudi, Chennai**. The project provides an immersive, high-quality virtual tour experience with an AI-driven agent guiding users through the property.

### 🌟 Core Components:

- **RAI:** An AI-based virtual male real estate agent.
- **Unreal Engine:** Delivers realistic, high-definition 3D visuals.
- **Pixel Streaming:** Enables browser-based access across devices without requiring local installations.

---

## 🌟 Key Features

### 🛠️ Dual Experience Modes

1. **Auto Mode:**

   - Automatically guides the user through each room with voice narration.
   - Supports "skip to next room" functionality.

2. **Manual Mode:**
   - Users have complete control to move freely inside the apartment.
   - Supports zooming in/out and exploration from different angles.

### 💬 AI Chatbot (RAI)

- Accepts both **speech** and **text** inputs.
- Responds conversationally using:
  - **Google Cloud Speech-to-Text** for user speech recognition.
  - **Google Cloud Text-to-Speech** or **Eleven Labs** for generating natural voice responses.
  - **OpenAI GPT-4.0 Mini** for generating intelligent, context-aware responses.

### 🌐 Cross-Platform, Browser-Based Access

- Experience is available directly on desktop and mobile browsers.
- Uses **Pixel Streaming** (via **WebRTC**) to stream the high-end Unreal Engine experience from the cloud to the user’s browser.
- User interactions are sent to the cloud server, and the experience responds in real time.

---

## 🔧 Technology Stack

| Component       | Technology                                                |
| --------------- | --------------------------------------------------------- |
| **Frontend**    | ReactJS                                                   |
| **Backend**     | Node.js, Express                                          |
| **3D Engine**   | Unreal Engine (Pixel Streaming)                           |
| **AI & Bot**    | Google Cloud, OpenAI GPT-4.0 Mini, Eleven Labs (optional) |
| **Cloud Infra** | Amazon EC2 (preloaded instances)                          |
| **Web Server**  | NGINX (Reverse Proxy, SSL)                                |
| **Connections** | WebSocket (Real-time tracking)                            |

---

## 📌 Infrastructure Breakdown

### 🚀 EC2 Server Initialization

- An **Amazon EC2** instance spins up on user connection.
- The server is preloaded with Unreal Engine builds and necessary resources.
- On disconnection, the server waits for a threshold period to check for new users before shutting down.

### 🔥 Loading Components

- **Frontend Loading:** Collects user details and plays a short video while the experience loads.
- **Backend Loading:** Handles server startup, ensuring Pixel Streaming starts smoothly.

### 📶 WebSocket-Based User Queue Management

- **10 concurrent users** supported at a time.
- Extra users are placed in a **queue**.
- Once an active user disconnects, the next user in line is connected automatically.

### 🔒 Secure, Scalable Access

- **NGINX** acts as a **reverse proxy** for SSL termination, ensuring secure, encrypted communication.
- Supports both **HTTP** and **WebSocket** traffic.

---

## 🔥 User Journey Workflow

1️⃣ **User initiates connection through browser (desktop/mobile).**

2️⃣ **Frontend loads user details and triggers the backend to start an EC2 instance.**

3️⃣ **Unreal Engine Pixel Streaming initiates, and the experience streams to the browser via WebRTC.**

4️⃣ **RAI AI assistant engages with the user (text/speech) to guide or answer queries.**

5️⃣ **WebSocket server monitors active users and manages queued users if the limit exceeds.**

6️⃣ **Once the user disconnects, the backend waits for a threshold period before terminating the EC2 server.**

---

## 🛠️ Future Improvements

- **AI Enhancements:** Improve RAI’s conversational abilities and emotional tone.
- **Multi-language support** for broader accessibility.
- **User Analytics** to track user behavior and improve experience flow.
- **Virtual Reality (VR) Support** for more immersive walkthroughs.

---
