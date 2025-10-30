const express = require("express");
const jwt = require("jsonwebtoken");
const bodyParser = require("body-parser");

const app = express();
const PORT = 5000;

// Secret key for JWT signing
const JWT_SECRET = "your_jwt_secret_key";

// Middleware to parse JSON bodies
app.use(bodyParser.json());

// Hardcoded sample user
const sampleUser = {
  username: "testuser",
  password: "password123", // In real apps, never store plain passwords!
};

// Login route
app.post("/login", (req, res) => {
  const { username, password } = req.body;

  // Check credentials
  if (username === sampleUser.username && password === sampleUser.password) {
    // Generate JWT
    const token = jwt.sign({ username }, JWT_SECRET, { expiresIn: "1h" });
    return res.json({ message: "Login successful", token });
  }

  res.status(401).json({ message: "Invalid username or password" });
});

// Middleware to verify JWT
function authenticateToken(req, res, next) {
  const authHeader = req.headers["authorization"];
  const token = authHeader && authHeader.split(" ")[1]; // Expect "Bearer TOKEN"

  if (!token) return res.status(401).json({ message: "Access token missing" });

  jwt.verify(token, JWT_SECRET, (err, user) => {
    if (err) return res.status(403).json({ message: "Invalid or expired token" });
    req.user = user; // attach user info to request
    next();
  });
}

// Protected route
app.get("/protected", authenticateToken, (req, res) => {
  res.json({ message: `Hello ${req.user.username}, you have accessed a protected route!` });
});

// Public route
app.get("/", (req, res) => {
  res.send("Welcome! Go to /login to get a token, then access /protected");
});

app.listen(PORT, () => {
  console.log(`Server running on http://localhost:${PORT}`);
});
