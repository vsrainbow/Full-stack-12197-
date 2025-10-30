{
  "name": "account-transfer-system",
  "version": "1.0.0",
  "description": "Account Transfer System with Balance Validation (no DB transactions)",
  "main": "server.js",
  "scripts": {
    "start": "node server.js",
    "dev": "nodemon server.js"
  },
  "dependencies": {
    "dotenv": "^16.4.5",
    "express": "^4.19.2",
    "mongoose": "^8.5.2"
  },
  "devDependencies": {
    "nodemon": "^3.1.0"
  }
}
PORT=5000
MONGO_URI=mongodb://localhost:27017/transferdb
const mongoose = require('mongoose');

const accountSchema = new mongoose.Schema({
  name: { type: String, required: true, trim: true },
  balance: {
    type: Number,
    required: true,
    min: [0, 'Balance cannot be negative'],
    default: 0
  }
}, { timestamps: true });

module.exports = mongoose.model('Account', accountSchema);
const Account = require('../models/Account');

// Create a new account
exports.createAccount = async (req, res) => {
  try {
    const { name, balance } = req.body;
    if (!name) return res.status(400).json({ error: 'Name is required' });
    if (balance != null && balance < 0) return res.status(400).json({ error: 'Balance cannot be negative' });

    const account = new Account({ name, balance: balance ?? 0 });
    await account.save();
    res.status(201).json({ message: 'Account created', account });
  } catch (err) {
    res.status(500).json({ error: err.message });
  }
};

// Get all accounts
exports.getAllAccounts = async (req, res) => {
  try {
    const accounts = await Account.find().sort({ createdAt: -1 });
    res.json(accounts);
  } catch (err) {
    res.status(500).json({ error: err.message });
  }
};

// Get account by id
exports.getAccountById = async (req, res) => {
  try {
    const account = await Account.findById(req.params.id);
    if (!account) return res.status(404).json({ error: 'Account not found' });
    res.json(account);
  } catch (err) {
    res.status(500).json({ error: err.message });
  }
};
const mongoose = require('mongoose');
const Account = require('../models/Account');

/**
 * Transfer money from one account to another WITHOUT DB transactions.
 * Steps:
 *  1) Validate input.
 *  2) Atomically decrement sender balance only if balance >= amount (findOneAndUpdate with filter).
 *  3) Atomically increment receiver balance.
 *  4) If credit fails (receiver not found or other error), attempt to refund sender (best-effort).
 */
exports.transfer = async (req, res) => {
  try {
    const { fromAccountId, toAccountId, amount } = req.body;

    // Basic validation
    if (!fromAccountId || !toAccountId || amount == null) {
      return res.status(400).json({ error: 'fromAccountId, toAccountId and amount are required' });
    }
    if (fromAccountId === toAccountId) {
      return res.status(400).json({ error: 'fromAccountId and toAccountId must be different' });
    }
    const transferAmount = Number(amount);
    if (isNaN(transferAmount) || transferAmount <= 0) {
      return res.status(400).json({ error: 'Amount must be a positive number' });
    }

    // Step 1: Atomically withdraw from sender only if sufficient balance
    const sender = await Account.findOneAndUpdate(
      { _id: fromAccountId, balance: { $gte: transferAmount } },
      { $inc: { balance: -transferAmount } },
      { new: true }
    );

    if (!sender) {
      // Determine reason: does sender exist? or insufficient funds?
      const senderExists = await Account.findById(fromAccountId);
      if (!senderExists) {
        return res.status(404).json({ error: 'Sender account not found' });
      } else {
        return res.status(400).json({ error: 'Insufficient balance in sender account' });
      }
    }

    // Step 2: Credit receiver account
    const receiver = await Account.findOneAndUpdate(
      { _id: toAccountId },
      { $inc: { balance: transferAmount } },
      { new: true }
    );

    if (!receiver) {
      // Receiver not found — attempt to refund sender (best-effort)
      try {
        const refund = await Account.findByIdAndUpdate(
          fromAccountId,
          { $inc: { balance: transferAmount } },
          { new: true }
        );
        // If refund fails, log and inform (system may be inconsistent until manual fix)
        if (!refund) {
          return res.status(500).json({
            error: 'Receiver account not found. Attempted refund failed — MANUAL INTERVENTION REQUIRED'
          });
        } else {
          return res.status(404).json({
            error: 'Receiver account not found. Amount refunded to sender.',
            sender: refund
          });
        }
      } catch (refundErr) {
        return res.status(500).json({
          error: 'Receiver account not found. Refund attempt failed due to error; manual fix needed.',
          details: refundErr.message
        });
      }
    }

    // Success
    return res.json({
      message: 'Transfer successful',
      from: { id: sender._id, name: sender.name, balance: sender.balance },
      to: { id: receiver._id, name: receiver.name, balance: receiver.balance }
    });
  } catch (err) {
    // Catch unexpected errors
    return res.status(500).json({ error: err.message });
  }
};
const express = require('express');
const router = express.Router();
const accountController = require('../controllers/accountController');

router.post('/', accountController.createAccount);        // Create account
router.get('/', accountController.getAllAccounts);        // List accounts
router.get('/:id', accountController.getAccountById);     // Account detail

module.exports = router;
const express = require('express');
const router = express.Router();
const transferController = require('../controllers/transferController');

/**
 * POST /api/transfer
 * Body: { fromAccountId, toAccountId, amount }
 */
router.post('/', transferController.transfer);

module.exports = router;
const express = require('express');
const mongoose = require('mongoose');
const dotenv = require('dotenv');
const accountRoutes = require('./routes/accountRoutes');
const transferRoutes = require('./routes/transferRoutes');

dotenv.config();
const app = express();

app.use(express.json());

// Connect to MongoDB
mongoose.connect(process.env.MONGO_URI)
  .then(() => console.log('✅ MongoDB connected'))
  .catch(err => {
    console.error('❌ MongoDB connection error:', err.message);
    process.exit(1);
  });

// Routes
app.use('/api/accounts', accountRoutes);
app.use('/api/transfer', transferRoutes);

// Root
app.get('/', (req, res) => {
  res.send('Account Transfer System API');
});

// Error handler (basic)
app.use((err, req, res, next) => {
  console.error('Unhandled error:', err);
  res.status(500).json({ error: 'Internal server error' });
});

// Start server
const PORT = process.env.PORT || 5000;
app.listen(PORT, () => console.log(`🚀 Server running on port ${PORT}`));
