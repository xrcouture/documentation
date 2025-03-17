# 🔥 Microservices Breakdown - Jains Aadhya Project

## 📲 WhatsApp Follow-Up Microservice

### 🎯 Purpose

This microservice handles follow-up communication with users over WhatsApp to keep leads engaged and ensure timely reminders for site visits and other interactions.

### 🔧 Architecture Overview

- **Trigger:** AWS EventBridge initiates the process.
- **Queue:** AWS SQS ensures reliable message delivery.
- **Processing:** AWS Lambda processes the message.
- **LLM Integration:** Uses OpenAI API to personalize responses.
- **WhatsApp API:** Sends messages via a WhatsApp Business API.

### ⚙️ Workflow Breakdown

1. **Event Trigger:**

   - EventBridge watches for reminders (e.g., scheduled site visit, cost sheet inquiry).
   - When an event matches a rule, it pushes a message to SQS.

2. **SQS Queue:**

   - SQS ensures no message is lost and retries on failure.

3. **Lambda Processor:**

   - AWS Lambda consumes the message from SQS.
   - It fetches user data from MongoDB (e.g., name, inquiry type, preferences).
   - Calls OpenAI API to craft a personalized WhatsApp message.

4. **WhatsApp API Integration:**

   - Sends the crafted message to the user.
   - Supports both text and multimedia (images/videos).

5. **Error Handling & Retry:**
   - If WhatsApp API fails (e.g., user offline), retries are managed through SQS's backoff strategy.
   - Lambda logs errors to CloudWatch for monitoring.

### 🔍 Example Use Case

- User schedules a site visit for **3 PM, March 20**.
- EventBridge triggers a reminder at **2:45 PM**.
- SQS queues the event.
- Lambda fetches user details and crafts a reminder:  
  _"Hey [User's Name], just a reminder — your site visit is at 3 PM today! Looking forward to seeing you there. 🚀"_
- WhatsApp API sends the message.

---

## 📊 Report Generation Microservice

### 🎯 Purpose

Generates detailed reports consolidating user interaction data. It produces two types of reports:

1. **Consolidated Report:** Captures all user interactions.
2. **Session-Wise Report:** Breaks data down per user session.

### 🔧 Architecture Overview

- **Trigger:** Scheduled via AWS EventBridge (hourly from 9 AM to 9 PM).
- **Data Source:** Pulls data from MongoDB.
- **Processing:** Node.js backend processes and organizes data.
- **Output:** Generates two Google Sheets (using Google Sheets API).

### ⚙️ Workflow Breakdown

1. **Event Trigger:**

   - AWS EventBridge runs the service every hour.

2. **Data Extraction:**

   - Pulls user data from MongoDB.
   - Extracts fields: `name`, `mobile number`, `preferred configurations`, `chat history`, `ranking`, `session timestamps`.

3. **Data Processing:**

   - Node.js backend processes raw data.
   - **Session-wise report:** Groups data by user session.
   - **Consolidated report:** Combines all sessions into one sheet.

4. **Google Sheets API:**

   - Generates two sheets.
   - Formats columns for easy analysis.
   - Shares with the sales team.

5. **Error Handling:**
   - Retries on Google API failure.
   - Logs errors to CloudWatch.

### 🔍 Example Output

- **Consolidated Report:**
  | Name | Mobile | Config | Rank | Chat History | Visit Scheduled |
  |----------|-----------|--------|------|--------------|-----------------|
  | John Doe | 9876543210 | 3BHK | High | Yes | Yes |

- **Session-wise Report:**
  | Name | Session Start | Session End | Chat Length | Intent Detected |
  |----------|---------------|-------------|-------------|-----------------|
  | John Doe | 9:10 AM | 9:35 AM | 25 mins | Site Visit |

---

✨ **These microservices ensure smooth follow-ups, personalized interactions, and data-backed insights — empowering sales teams with automation and intelligence.**
