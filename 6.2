{
  "name": "jwt-banking-api",
  "version": "1.0.0",
  "description": "JWT Authentication for Secure Banking API Endpoints",
  "main": "server.js",
  "scripts": {
    "start": "node server.js",
    "dev": "nodemon server.js"
  },
  "keywords": ["express", "jwt", "authentication", "banking-api", "security"],
  "author": "Your Name",
  "license": "ISC",
  "dependencies": {
    "dotenv": "^16.4.5",
    "express": "^4.19.2",
    "jsonwebtoken": "^9.0.2"
  },
  "devDependencies": {
    "nodemon": "^3.1.0"
  }
}
const jwt = require('jsonwebtoken');
require('dotenv').config();

// Middleware to verify JWT token
const authenticateToken = (req, res, next) => {
  const authHeader = req.headers['authorization'];

  if (!authHeader)
    return res.status(401).json({ error: 'Authorization header missing' });

  const token = authHeader.split(' ')[1]; // Bearer <token>

  if (!token)
    return res.status(401).json({ error: 'Token not provided' });

  jwt.verify(token, process.env.JWT_SECRET, (err, user) => {
    if (err)
      return res.status(403).json({ error: 'Invalid or expired token' });

    req.user = user; // attach user data to request
    next();
  });
};

module.exports = authenticateToken;
let balance = 1000; // initial balance for demo

// View account balance
exports.getBalance = (req, res) => {
  res.json({
    user: req.user.username,
    balance: `$${balance.toFixed(2)}`
  });
};

// Deposit money
exports.deposit = (req, res) => {
  const { amount } = req.body;
  if (!amount || amount <= 0)
    return res.status(400).json({ error: 'Invalid deposit amount' });

  balance += amount;
  res.json({
    message: `Deposited $${amount.toFixed(2)} successfully`,
    newBalance: `$${balance.toFixed(2)}`
  });
};

// Withdraw money
exports.withdraw = (req, res) => {
  const { amount } = req.body;
  if (!amount || amount <= 0)
    return res.status(400).json({ error: 'Invalid withdrawal amount' });

  if (amount > balance)
    return res.status(400).json({ error: 'Insufficient balance' });

  balance -= amount;
  res.json({
    message: `Withdrew $${amount.toFixed(2)} successfully`,
    newBalance: `$${balance.toFixed(2)}`
  });
};
const express = require('express');
const jwt = require('jsonwebtoken');
const authenticateToken = require('../middlewares/auth');
const bankingController = require('../controllers/bankingController');
require('dotenv').config();

const router = express.Router();

// Hardcoded user credentials for demonstration
const USER = {
  username: 'user1',
  password: 'password123'
};

//  Login Route - generates JWT
router.post('/login', (req, res) => {
  const { username, password } = req.body;

  if (username !== USER.username || password !== USER.password) {
    return res.status(401).json({ error: 'Invalid username or password' });
  }

  // Create JWT payload
  const userPayload = { username: USER.username };

  // Sign JWT
  const token = jwt.sign(userPayload, process.env.JWT_SECRET, { expiresIn: '1h' });

  res.json({
    message: 'Login successful!',
    token
  });
});

//  Protected routes
router.get('/balance', authenticateToken, bankingController.getBalance);
router.post('/deposit', authenticateToken, bankingController.deposit);
router.post('/withdraw', authenticateToken, bankingController.withdraw);

module.exports = router;
const express = require('express');
const dotenv = require('dotenv');
const bankingRoutes = require('./routes/bankingRoutes');

dotenv.config();
const app = express();

// Middleware for parsing JSON
app.use(express.json());

// Default route
app.get('/', (req, res) => {
  res.send('Welcome to the Secure Banking API using JWT Authentication!');
});

// Register routes
app.use('/api', bankingRoutes);

// Start server
const PORT = process.env.PORT || 5000;
app.listen(PORT, () => {
  console.log(`Server running on http://localhost:${PORT}`);
});
