const express = require("express");
const jwt = require("jsonwebtoken");
const bodyParser = require("body-parser");

const app = express();
const PORT = 5000;

// Secret key for JWT
const JWT_SECRET = "your_jwt_secret_key";

// Middleware to parse JSON requests
app.use(bodyParser.json());

// Sample users with roles
const users = [
  { username: "admin", password: "admin123", role: "Admin" },
  { username: "moderator", password: "mod123", role: "Moderator" },
  { username: "user", password: "user123", role: "User" },
];

// ------------------- Login Route -------------------
app.post("/login", (req, res) => {
  const { username, password } = req.body;

  const user = users.find(
    (u) => u.username === username && u.password === password
  );

  if (!user) {
    return res.status(401).json({ message: "Invalid username or password" });
  }

  // Generate JWT including the role in the payload
  const token = jwt.sign(
    { username: user.username, role: user.role },
    JWT_SECRET,
    { expiresIn: "1h" }
  );

  res.json({ message: "Login successful", token });
});

// ------------------- JWT Authentication Middleware -------------------
function authenticateToken(req, res, next) {
  const authHeader = req.headers["authorization"];
  const token = authHeader && authHeader.split(" ")[1];

  if (!token)
    return res.status(401).json({ message: "Access token missing" });

  jwt.verify(token, JWT_SECRET, (err, user) => {
    if (err) return res.status(403).json({ message: "Invalid or expired token" });
    req.user = user; // Attach decoded token to request
    next();
  });
}

// ------------------- Role Authorization Middleware -------------------
function authorizeRoles(...allowedRoles) {
  return (req, res, next) => {
    if (!req.user) return res.status(401).json({ message: "Unauthorized" });

    if (!allowedRoles.includes(req.user.role)) {
      return res
        .status(403)
        .json({ message: `Access denied for role: ${req.user.role}` });
    }

    next();
  };
}

// ------------------- Protected Routes -------------------

// Admin-only route
app.get(
  "/admin-dashboard",
  authenticateToken,
  authorizeRoles("Admin"),
  (req, res) => {
    res.json({ message: `Welcome Admin ${req.user.username}!` });
  }
);

// Moderator-only route
app.get(
  "/moderator-panel",
  authenticateToken,
  authorizeRoles("Moderator"),
  (req, res) => {
    res.json({ message: `Welcome Moderator ${req.user.username}!` });
  }
);

// General User route (accessible to User, Admin, Moderator)
app.get(
  "/profile",
  authenticateToken,
  authorizeRoles("User", "Admin", "Moderator"),
  (req, res) => {
    res.json({ message: `Hello ${req.user.username}, your role is ${req.user.role}` });
  }
);

// Public route
app.get("/", (req, res) => {
  res.send("Welcome! Use /login to obtain a token, then access role-based routes.");
});

app.listen(PORT, () => {
  console.log(`Server running on http://localhost:${PORT}`);
});
