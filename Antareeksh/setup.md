# Jains Antareeksh - Setup Guide

## Prerequisites

Ensure you have the following prerequisites installed and configured:

- **Amazon EC2 account** with appropriate instance types.
- **Unreal Engine** (project built and packaged).
- **Node.js** and **npm** (for backend and frontend setup).
- **NGINX** (for reverse proxy and SSL setup).
- **Google Cloud API credentials** (for Speech-to-Text and Text-to-Speech).
- **OpenAI API key** (for GPT-4.0 Mini integration).
- **Eleven Labs API key** (optional for Text-to-Speech).

---

## 1. Backend Setup

### 1.1. EC2 Server Setup

1. **Launch an EC2 instance:**

   - Choose an instance type with GPU support (e.g., G4dn for pixel streaming).
   - Configure security groups to allow HTTP, HTTPS, and WebSocket ports.

2. **Install necessary packages:**

   ```bash
   sudo apt update
   sudo apt install nginx nodejs npm
   ```

3. **Copy game build to the server:**

   - Upload the Unreal Engine packaged build to the server.
   - Ensure all files, including the `PixelStreaming` server, are present.

4. **Setup WebSocket Server:**

   ```bash
   npm install ws express
   ```

   - Write a WebSocket server to track connections and handle queues.

5. **Configure backend loading component:**
   - Add server initialization scripts.
   - Implement the threshold timeout to keep the server alive for a short period after disconnection.

---

## 2. Frontend Setup

1. **Clone frontend repository:**

   ```bash
   git clone <frontend-repo-url>
   cd frontend
   npm install
   ```

2. **Implement loading screen:**

   - Add a user detail form.
   - Play a video while the experience loads.

3. **Connect frontend to backend:**
   - Point WebRTC connection to backend server IP/domain.
   - Implement API calls for Google Cloud Speech-to-Text, Text-to-Speech, and OpenAI.

---

## 3. NGINX Setup

1. **Install and configure NGINX:**

   ```bash
   sudo apt install nginx
   ```

2. **Set up reverse proxy for SSL termination:**

   ```nginx
   server {
     listen 80;
     server_name your-domain.com;

     location / {
       proxy_pass http://localhost:3000;  # Point to backend
       proxy_set_header Host $host;
       proxy_set_header X-Real-IP $remote_addr;
       proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
       proxy_set_header X-Forwarded-Proto $scheme;
     }
   }
   ```

3. **Enable SSL (optional):**
   ```bash
   sudo apt install certbot python3-certbot-nginx
   sudo certbot --nginx -d your-domain.com
   ```

---

## 4. Pixel Streaming Setup

1. **Run the Pixel Streaming server:**

   ```bash
   ./PixelStreaming/Start_Stream.sh
   ```

2. **Ensure WebRTC signaling server is connected:**

   ```bash
   node ./SignallingWebServer/server.js
   ```

3. **Ensure the frontend connects to the stream:**
   - Verify WebRTC handshake works.
   - Test input response from client to server.

---

## 5. User Queue Management

1. **WebSocket connection tracking:**

   - Track active users.
   - Limit to **10 concurrent users**.
   - Implement a queue for extra users.

2. **Queue release mechanism:**
   - When a user disconnects, the next user in the queue gets access.

---

## 6. Final Testing

1. **Test frontend and backend:**

   - Ensure loading components trigger correctly.
   - Verify Pixel Streaming connects seamlessly.

2. **Simulate user load:**

   - Test with more than **10 users** to confirm queue functionality.

3. **Verify RAI AI responses:**
   - Test both speech and text input responses.

---

Your setup should now be complete. 🎉

Would you like me to extend this with a troubleshooting or maintenance section?
