{
  "name": "middleware-auth-app",
  "version": "1.0.0",
  "description": "Middleware Implementation for Logging and Bearer Token Authentication",
  "main": "server.js",
  "scripts": {
    "start": "node server.js",
    "dev": "nodemon server.js"
  },
  "keywords": ["express", "middleware", "logging", "authentication", "nodejs"],
  "author": "Your Name",
  "license": "ISC",
  "dependencies": {
    "dotenv": "^16.4.5",
    "express": "^4.19.2"
  },
  "devDependencies": {
    "nodemon": "^3.1.0"
  }
}

// Logger middleware - logs HTTP method, URL, and timestamp
const logger = (req, res, next) => {
  const currentTime = new Date().toISOString();
  console.log(`[${currentTime}] ${req.method} ${req.originalUrl}`);
  next(); // pass control to next middleware or route handler
};

module.exports = logger;
require('dotenv').config();

// Authentication middleware - verifies Bearer token
const authenticateToken = (req, res, next) => {
  const authHeader = req.headers['authorization']; // Get header
  if (!authHeader) {
    return res.status(401).json({ error: 'Missing Authorization header' });
  }

  // Check Bearer token format
  const token = authHeader.split(' ')[1];
  if (!token) {
    return res.status(400).json({ error: 'Invalid Authorization format' });
  }

  // Validate token
  if (token !== process.env.SECRET_TOKEN) {
    return res.status(403).json({ error: 'Invalid or expired token' });
  }

  // Token valid -> continue
  next();
};

module.exports = authenticateToken;
const express = require('express');
const router = express.Router();
const authenticateToken = require('../middlewares/auth');

// Public route (no authentication required)
router.get('/public', (req, res) => {
  res.json({
    message: 'This is a public route. Accessible without authentication.',
  });
});

// Protected route (requires Bearer token)
router.get('/protected', authenticateToken, (req, res) => {
  res.json({
    message: 'Access granted! You are viewing a protected route.',
    user: 'Authorized User',
  });
});

module.exports = router;
const express = require('express');
const dotenv = require('dotenv');
const logger = require('./middlewares/logger');
const apiRoutes = require('./routes/apiRoutes');

dotenv.config();
const app = express();

// Apply global middleware for logging
app.use(logger);

// Parse JSON requests
app.use(express.json());

// Mount routes
app.use('/api', apiRoutes);

// Root route
app.get('/', (req, res) => {
  res.send('Welcome to the Middleware Authentication API!');
});

// Start the server
const PORT = process.env.PORT || 5000;
app.listen(PORT, () =>
  console.log(` Server running on http://localhost:${PORT}`)
);
