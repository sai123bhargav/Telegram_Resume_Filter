# 🤖 Telegram → PDF → AI Screening → Google Sheets → Gmail Automation (n8n Workflow)

This repository contains an advanced **n8n automation workflow** that processes Telegram messages, extracts data from PDF resumes, evaluates candidates using an AI Agent, and updates Google Sheets while sending automated Gmail notifications based on the evaluation.

---

## 📌 **Workflow Overview**

This automation connects multiple systems to create a fully automated recruitment/document-processing pipeline.  
It performs:

- 📥 **Telegram message & file intake**  
- 🗂️ **ZIP/PDF extraction**  
- 🔍 **AI-based resume/document screening**  
- 📊 **Google Sheets row insertion (Accepted / Rejected / Review)**  
- 📧 **Automated Gmail reply messages**  
- 🔄 **Merge, conditions, wait flows**

---

## 🖼️ **Workflow Diagram**

Below is the full workflow structure:

![Workflow Diagram]("C:\Users\bharg\OneDrive\Pictures\Screenshots\Screenshot 2025-11-21 165424.png")

---

## 🧩 **Main Components**

### **1️⃣ Telegram Trigger**
- Listens for incoming messages/files.
- Detects text, PDFs, ZIP files.
- Sends an initial confirmation message.

### **2️⃣ File Handling**
- Decompresses ZIP files (if uploaded).
- Splits multiple files.
- Loops through all items for processing.

### **3️⃣ PDF Extraction**
- Extracts text from PDF using n8n’s **Extract from File** node.

### **4️⃣ AI Agent Processing**
- Sends extracted text to an **OpenAI Chat Model**.
- AI evaluates content (example: resume ATR score, job match, etc.).
- A Python node performs cleanup & formatting.
- Fields are edited before decision-making.

### **5️⃣ Decision Logic (IF Nodes)**
Based on AI output:

- **Accepted** → Adds row to Sheet 1 + sends acceptance email  
- **Rejected** → Adds row to Sheet 2 + sends rejection email  
- **Manual Review** → Adds row to Sheet 3 + sends review-required email  

### **6️⃣ Google Sheets Automation**
- Automatically writes candidate details, extracted info, ATR scores, etc.
- Organized into 3 separate sheets.

### **7️⃣ Gmail Notifications**
Sends different messages depending on the AI decision:

- ✔ Acceptance Email  
- ❌ Rejection Email  
- 🔎 Manual Review Email  

### **8️⃣ Merge & Wait**
- All branches merge back into a single flow.
- Wait node controls execution timing.

---

## 📁 **Suggested Repository St
