# 🏟️ Sportz – Live Commentary WebSocket Service ⚡

A **full-stack real-time sports commentary platform** built using **WebSockets**, **Node.js**, and **PostgreSQL**, delivering instant live updates across multiple clients.

This project demonstrates how modern sports apps (like Cricbuzz / ESPN) stream live commentary to thousands of users in real time.

---

## ✨ Features

- 🔄 **Real-time live commentary** using WebSockets  
- 🧑‍🤝‍🧑 **Multi-client broadcast** (all connected tabs update instantly)
- 📡 **REST + WebSocket hybrid architecture**
- 🗂️ **PostgreSQL (Neon) database**
- 🚦 **Rate limiting & backpressure handling**
- 🧪 **Seeded data for instant testing**
- 🖥️ **Modern frontend with live feed UI**

---

## 🏗️ Tech Stack

### Backend
- Node.js
- Express.js
- WebSocket (ws)
- PostgreSQL (Neon)
- Drizzle ORM
- Arcjet (rate limiting & security)

### Frontend
- Vite
- React
- TypeScript
- WebSocket client
- REST API integration

---

## 📂 Project Structure

```

sportz/
├── sportz-websockets   # Backend (API + WebSocket server)
│   ├── src/
│   ├── meta/           # SQL schema
│   ├── .env
│   └── package.json
│
├── sportz-frontend     # Frontend (Live UI)
│   ├── src/
│   ├── .env
│   ├── .env.local
│   └── package.json

````

---

## 🚀 Getting Started

### Prerequisites
- Node.js
- npm
- PostgreSQL (Neon recommended)
- Git

---

## 🔧 Backend Setup

```bash
cd sportz-websockets
npm install
````

Create `.env`:

```env
DATABASE_URL=postgresql://YOUR_DB_URL
PORT=8000
HOST=0.0.0.0

ARCJET_KEY=YOUR_ARCJET_KEY
ARCJET_ENV=development

API_URL=http://localhost:8000

BROADCAST=1
DELAY_MS=250
MATCH_COUNT=0
```

Run DB schema (once):

* Execute `meta/0000_concerned_celestials.sql` in Neon SQL Editor

Start backend:

```bash
npm run dev
```

Seed database:

```bash
npm run seed
```

---

## 🎨 Frontend Setup

```bash
cd ../sportz-frontend
npm install
```

Create `.env`:

```env
VITE_API_BASE_URL=http://localhost:8000
VITE_WS_BASE_URL=ws://localhost:8000/ws
```

Create `.env.local`:

```env
GEMINI_API_KEY=YOUR_GEMINI_API_KEY
```

Start frontend:

```bash
npm run dev
```

Open in browser:

```
http://localhost:3000
```

---

## 📡 WebSocket Protocol

### Connect

```
ws://localhost:8000/ws
```

### Client → Server

```json
{ "type": "subscribe", "matchId": 1 }
{ "type": "unsubscribe", "matchId": 1 }
{ "type": "ping" }
```

### Server → Client

```json
{ "type": "welcome" }
{ "type": "subscribed", "matchId": 1 }
{ "type": "commentary", "data": { "message": "GOAL!" } }
```

---

## 🧠 Design Notes

* Scores are **not auto-calculated** from commentary
* Commentary and scoring are intentionally decoupled
* Built to focus on **real-time systems & WebSocket architecture**

---

## 🌍 Use Cases

* Live sports commentary apps
* Real-time dashboards
* Event broadcasting systems
* Multiplayer or live-feed applications

---

## 📌 Future Improvements

* 🧮 Auto score calculation
* 🔐 Authentication
* 📊 Match statistics
* ☁️ Redis pub/sub for horizontal scaling

---

## ⭐ If you like this project

Give it a ⭐ on GitHub — it really helps!
