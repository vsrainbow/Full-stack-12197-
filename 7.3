{
  "name": "realtime-chat-backend",
  "version": "1.0.0",
  "main": "server.js",
  "scripts": {
    "start": "node server.js",
    "dev": "nodemon server.js"
  },
  "dependencies": {
    "express": "^4.19.2",
    "socket.io": "^4.7.2",
    "cors": "^2.8.5"
  },
  "devDependencies": {
    "nodemon": "^3.1.0"
  }
}
const express = require('express');
const http = require('http');
const cors = require('cors');
const { Server } = require('socket.io');

const app = express();
app.use(cors());

const server = http.createServer(app);
const io = new Server(server, {
  cors: { origin: "*" }
});

const PORT = 5000;

// Simple endpoint
app.get('/', (req, res) => {
  res.send('Real-Time Chat Server is running');
});

// Socket.io connection
io.on('connection', (socket) => {
  console.log(`User connected: ${socket.id}`);

  // Broadcast message event
  socket.on('chatMessage', (msg) => {
    io.emit('chatMessage', msg); // broadcast to all connected clients
  });

  socket.on('disconnect', () => {
    console.log(`User disconnected: ${socket.id}`);
  });
});

server.listen(PORT, () => {
  console.log(`✅ Server running on http://localhost:${PORT}`);
});
import React, { useEffect, useState } from "react";
import { io } from "socket.io-client";

const socket = io("http://localhost:5000"); // backend URL

const Chat = () => {
  const [name, setName] = useState("");
  const [message, setMessage] = useState("");
  const [messages, setMessages] = useState([]);
  const [joined, setJoined] = useState(false);

  useEffect(() => {
    // Listen for incoming messages
    socket.on("chatMessage", (msg) => {
      setMessages((prev) => [...prev, msg]);
    });

    return () => {
      socket.off("chatMessage");
    };
  }, []);

  const handleJoin = () => {
    if (name.trim()) setJoined(true);
  };

  const sendMessage = () => {
    if (message.trim()) {
      const msg = { name, text: message, time: new Date().toLocaleTimeString() };
      socket.emit("chatMessage", msg);
      setMessage("");
    }
  };

  const handleKeyPress = (e) => {
    if (e.key === "Enter") sendMessage();
  };

  if (!joined) {
    return (
      <div style={{ textAlign: "center", marginTop: "50px" }}>
        <h2>Enter your name to join the chat</h2>
        <input
          type="text"
          value={name}
          onChange={(e) => setName(e.target.value)}
          placeholder="Your name"
        />
        <button onClick={handleJoin} style={{ marginLeft: "10px" }}>Join</button>
      </div>
    );
  }

  return (
    <div style={{ maxWidth: "600px", margin: "20px auto", fontFamily: "Arial, sans-serif" }}>
      <h2>Chat Room</h2>
      <div
        style={{
          border: "1px solid #ccc",
          padding: "10px",
          height: "400px",
          overflowY: "scroll",
          marginBottom: "10px"
        }}
      >
        {messages.map((msg, idx) => (
          <div key={idx} style={{ marginBottom: "5px" }}>
            <strong>{msg.name}</strong> [{msg.time}]: {msg.text}
          </div>
        ))}
      </div>
      <input
        type="text"
        value={message}
        placeholder="Type a message..."
        onChange={(e) => setMessage(e.target.value)}
        onKeyPress={handleKeyPress}
        style={{ width: "80%", padding: "5px" }}
      />
      <button onClick={sendMessage} style={{ width: "18%", padding: "5px", marginLeft: "2%" }}>
        Send
      </button>
    </div>
  );
};

export default Chat;
import React from "react";
import Chat from "./components/Chat";

function App() {
  return (
    <div>
      <Chat />
    </div>
  );
}

export default App;
import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App";

const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(<App />);
