# 📘 Jains Aadhya - AI Real Estate Agent Project Documentation

## 🏗️ Project Overview

**Project Name:** Jains Aadhya\
**Location:** Nookampalayam Road, Chennai\
**Objective:** AI-powered real estate assistant, featuring SIA (a female AI chatbot) designed to assist users in exploring real estate properties interactively.

---

## 🔧 Tech Stack

- **Frontend:** ReactJS
- **Backend:** Node.js, ExpressJS
- **Database:** MongoDB
- **Microservices:** WhatsApp follow-ups, Report Generation
- **Cloud Services:** AWS API Gateway, AWS EventBridge, AWS SQS, AWS Lambda
- **LLM:** OpenAI API (GPT-4o-mini)
- **Speech-to-Text:** Deepgram, Google Cloud
- **Text-to-Speech:** ElevenLabs, AWS Polly, Google Cloud
- **LipSync:** AWS Polly

---

## 🚀 Features

### 🎯 Core AI Features

1. **AI Chatbot (SIA):**

   - Interacts with users via **Speech and Text**.
   - Supports **intent detection** using OpenAI API to guide users (e.g., site visit scheduling, cost sheet calculations).

2. **Multimedia Response:**

   - Displays relevant **images and videos** based on user inquiries.

3. **Speech-to-Text:**

   - **Plug-and-Play** setup supporting **Deepgram** and **Google Cloud** for transcription.

4. **Text-to-Speech:**

   - Supports **ElevenLabs**, **AWS Polly**, and **Google Cloud** for dynamic text-to-voice conversion.

5. **LipSync Animation:**

   - Uses **AWS Polly** to sync chatbot speech with realistic lip movements.

### 🔥 User Engagement Features

1. **Site Visit Scheduling:**

   - Allows users to select preferred **date and time**.

2. **Cost Sheet Calculation:**

   - Users select **floor** and **size** to get a **detailed cost breakdown**.

3. **WhatsApp Follow-Up:**

   - Automated follow-ups via a **dedicated microservice**.
   - AWS EventBridge manages reminders.

4. **Feedback Form:**

   - Captures user **ratings** and **comments**.

5. **User Intent Ranking:**

   - Ranks users based on their engagement and behavior.

---

## 🔧 Backend & Microservices

### 🎯 Backend Overview

- Built with **Node.js** and **ExpressJS**.
- Manages API routes, chatbot responses, multimedia delivery, and user data handling.
- Handles **user intents** and **triggers** actions accordingly (e.g., schedule site visit).

### 🔥 Microservices Breakdown

1. **WhatsApp Follow-Up Service:**

   - Triggered via AWS EventBridge.
   - Uses **AWS SQS** and **Lambda** for message processing.
   - Integrated with **OpenAI** for personalized responses.

2. **Report Generation Service:**

   - Runs every hour from **9 AM to 9 PM**.
   - Generates **Google Sheets** reports:
     - **Consolidated report** with all user interactions.
     - **Session-wise report** per user.
   - Captures user **name**, **mobile number**, **preferred configurations**, **chat history**, and **ranking**.

3. **MongoDB Charts Dashboard:**

   - Visualizes data through charts, showing **engagement insights** and **conversion trends**.

---

## 🚀 Deployment Details

- **Frontend**: Deployed under **xrvizion subdomain** (VPS).
- **Backend** and **Microservices** hosted on the same VPS.
- **AWS services** handle follow-ups, reminders, and reporting.

---

## 📌 Future Enhancements

- **Dynamic floor plan recommendations** based on user preferences.
- **AI-driven property recommendations** (e.g., similar projects in the area).
- **AI-based financial planning tool** (e.g., loan calculations, EMI breakdowns).

---

## 📘 Additional Pages

For more details:

- **[Microservices Breakdown](microservices.md)** — In-depth explanation of each microservice.

---

✨ **Jains Aadhya is revolutionizing real estate sales, one AI conversation at a time.** ✨
