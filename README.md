# mpesa-prompt-code
This project will be used to prompt mpesa numbers to give visual display on the phones.
const express = require("express");
const cors = require("cors");

const app = express();
app.use(cors());
app.use(express.json());

let latestNumber = "";

// Save M-Pesa number
app.post("/submit-number", (req, res) => {
    const { phone } = req.body;
    latestNumber = phone;
    console.log("Received number:", phone);
    res.json({ message: "Number received successfully" });
});

// Get latest number
app.get("/get-number", (req, res) => {
    res.json({ phone: latestNumber });
});

const PORT = 5000;
app.listen(PORT, () => {
    console.log(`Server running on port ${PORT}`);
});

