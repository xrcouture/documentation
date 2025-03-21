# Abhushan Mahal - Project Documentation

## 🎯 Project Overview

**Abhushan Mahal** is an immersive 3D virtual walkthrough of a majestic palace in **Butati, Rajasthan**, designed to promote the **Butati Dham Temple**. It offers a rich, interactive experience where users can explore the palace's different sections and interact with an AI guide.

---

## 🏰 Key Sections

1️⃣ **Exterior:**

- Showcases the grandeur of the palace.
- Auto-rotates to provide a 360° panoramic view of the surroundings.

2️⃣ **Residential Area:**

- The living quarters where the **Owner and family** reside.
- Fully explorable, room-by-room walkthrough.

3️⃣ **Dharamsala:**

- A guesthouse-like area where **temple visitors** can stay.
- Includes dormitories, shared rooms, and common halls.

---

## 🎮 Interactive Gameplay

- **Third-person 3D Character:** Users control a character to walk, run, jump, and explore every corner of the palace.
- **Actions:** Includes stair climbing, room transitions, lift interactions, and other realistic movements.
- **Gaming-like experience:** Built to make exploration feel like an adventure.

---

## 🧠 AI Bot - Araham

- **Araham:** A male AI bot that acts as a virtual guide.
- **Handles questions about the palace and Butati Dham temple.**
- **Supports both text and voice interactions** for a more intuitive experience.
- **Lipsync enabled** using **AWS Polly**, giving Araham a lifelike speaking animation.

---

## 🌐 Cross-Platform Compatibility

- **Unity WebGL** ensures the experience runs smoothly on both **mobile** and **desktop browsers**.
- **React Unity WebGL** bridges the frontend ReactJS app with the Unity WebGL experience.
- Supports **real-time input control** and **3D rendering** directly in the browser.

---

## 🔧 Technology Stack

| Component          | Technology                                                      |
| ------------------ | --------------------------------------------------------------- |
| **Frontend**       | ReactJS                                                         |
| **Backend**        | Node.js, Express.js, MongoDB                                    |
| **3D Experience**  | Unity WebGL                                                     |
| **AI Bot**         | Google Cloud STT, TTS, OpenAI GPT-4.0 Mini, AWS Polly (Lipsync) |
| **Static Content** | AWS S3, CloudFront (Videos/Images)                              |

---

## 🛠️ Infrastructure Breakdown

### 🎬 Static Content Loading

- **AWS S3** stores static content like initial loading videos, images, and room transition visuals.
- **CloudFront CDN** ensures faster loading speeds across different regions.

### 🔥 Unity WebGL Integration

- **React-Unity-WebGL** library connects the Unity game build with the ReactJS frontend.
- Supports **real-time character control** and **in-game events**.

### 💡 Backend Management

- **Node.js & ExpressJS** handle requests, user sessions, and interactions with the AI bot.
- **MongoDB** stores data, including user behavior tracking and frequently asked questions for analysis.

### 🔥 AI Bot Setup

- **Google Speech-to-Text** (STT) processes user voice inputs.
- **Google Text-to-Speech** (TTS) and **AWS Polly** convert responses to voice, enhancing immersion.
- **OpenAI GPT-4.0 Mini** powers Araham's conversational abilities, providing dynamic, context-aware responses.
- **AWS Polly Lipsync** syncs the AI bot’s mouth movements with the generated speech for a lifelike effect.

---

## 🔥 User Journey Workflow

1️⃣ **User accesses the experience through a browser (desktop/mobile).**

2️⃣ **Frontend ReactJS loads the Unity WebGL environment.**

3️⃣ **Loading videos/images** from AWS S3/CloudFront play while the palace loads.

4️⃣ **User controls the third-person character** to explore the exterior, residential, and Dharamsala sections.

5️⃣ **Araham AI guide** engages with the user — responding to text/speech queries.

6️⃣ **Backend tracks the user’s journey**, stores data, and maintains session stability.

---

## 🚀 Future Enhancements

- **Multiplayer Mode** to explore the palace with friends.
- **Language Support** for multiple Indian languages.
- **VR Support** for a more immersive tour.

---
