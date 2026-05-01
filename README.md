# 📊 Credit Card Optimization for Business Growth

> **Challenge:** June 2025 Monthly AI Challenge – AI Toolkit for Professionals 2.0  
> **Company:** BizPro Solutions  
> **Role Simulated:** Peter Pandey, Business Automation Specialist  
> **Submitted By:** Sachin Savkare

---

[![Watch the Project](https://raw.githubusercontent.com/CB-AI-Toolkit-for-Professional/14.-Automation-Challenge-Optimizing-Corporate-Credit-Card-Usage-with-AI-Automation-n8n/main/Thumbnail.png)](https://www.youtube.com/watch?v=1N9d8z_z8SY)

---

## 📌 Overview
BizPro Solutions is struggling with scattered employee credit card usage. With different cards offering unique rewards, annual fees, and late fee penalties, optimizing this system manually is inefficient.

This project presents an **AI-powered automation pipeline** built using **n8n + Google Gemini + Google Docs API** to:

- Extract key financial fields from PDF credit card statements
- Generate credit card usage recommendations using AI
- Merge insights into a structured Google Doc report
- Help CFOs make smarter, reward-maximizing decisions

This README explains the full architecture, setup, prompts, inputs/outputs, and strategic intent.

---

## 🧠 Use Case: From the June 2025 AI Challenge
**Challenge Prompt:** Tony Sharma, CFO of BizPro Solutions, asks Peter Pandey to:

- Analyze employee credit card statements
- Minimize unnecessary annual/late fees
- Maximize card-specific rewards
- Automate the full process from PDF to business insights

> 📄 [Read the Full Challenge Brief (PDF)](https://github.com/SachinSavkare/Automation-Challenge-Optimizing-Corporate-Credit-Card-Usage-with-AI-Automation-n8n/blob/main/June_2025_monthly_challenge.pdf)

---

## 🧱 Architecture
![Workflow Diagram](https://github.com/SachinSavkare/Automation-Challenge-Optimizing-Corporate-Credit-Card-Usage-with-AI-Automation-n8n/blob/main/Workflow%202.png)

| Flow | Name | Purpose |
|------|------|---------|
| 🔶 Flow 1 | Strategic Credit Card Insights Generator | Generates key trends and recommendations for CFOs |
| 🔴 Flow 2 | Credit Card Statement Extractor | Extracts card metadata + transactions from PDF |
| 🟢 Flow 3 | Report Generator | Merges flows and builds Google Doc using batchUpdate API |

---

## ⚙️ Flow-by-Flow Breakdown

### 🔶 Flow 1: Strategic Credit Card Insights Generator
**Tool:** Google Gemini Chat Model + Memory + Parser  
**Goal:** Provide expert recommendations on:
- Card selection by category (Travel, Dining, Office)
- Rewards optimization
- Behavioral improvement

> 🧾 **Prompt Used:**
> ```
> Act as a credit card analyst for business clients. Given employee spend data and industry offers, generate a structured credit card optimization strategy with these sections:
> 1. Executive Summary
> 2. Optimization Recommendations (2.1 Travel, 2.2 Dining, 2.3 Office Supplies)
> 3. Card Strategy Suggestions
> 4. Employee Spend Patterns
> 5. Behavioral Suggestions
> Return in structured JSON.
> ```

**Steps:**
1. Set research context (e.g., company type, card types)
2. Use AI Agent to generate strategic recommendations
3. Output structured JSON for downstream formatting

---

### 🔴 Flow 2: Credit Card Statement Extractor
**Input:** Credit card statement PDFs  
**Tools:** PDF Reader → Gemini Chat → Output Parser

> 🧾 **Prompt Used:**
> ```
> Extract the following details from this credit card statement:
> - Cardholder Name
> - Card Type, Card Name
> - Bank Name, Statement Month
> - Total Spent, Payment Received
> - Annual Fee, Late Fee, Minimum Due
> - Credit Limit, Available Credit, Due Date
> - Rewards Earned
> - All transactions with date, merchant, and amount
> Return as JSON.
> ```

**Steps:**
1. Read binary files & split in batches
2. Extract PDF content
3. Define PDF metadata context (e.g., employee name, bank, month)
4. Send to Gemini AI for field extraction
5. Structure result with parser
6. Output to Google Sheet (summary + transactions)

> 📄 [Sample Input PDF – Aaryahi Hora](https://github.com/SachinSavkare/Automation-Challenge-Optimizing-Corporate-Credit-Card-Usage-with-AI-Automation-n8n/blob/main/Aaryahi_Hora_StandardChartered_Jan2025.pdf)

---

### 🟢 Flow 3: Optimization Report Generator
**Goal:** Combine Flow 1 + Flow 2 into a structured CFO report  
**Tools:** Merge → Strategic Report Generator → Google Docs API (via HTTP request)

> 🧾 **Prompt Used:**
> ```
> Combine industry insights and employee card summary into a Google Docs report with these sections:
> - 1. EXECUTIVE SUMMARY
> - 2. OPTIMIZATION RECOMMENDATIONS (2.1 Travel, etc.)
> - 3. CARD STRATEGY SUGGESTIONS
> - 4. EMPLOYEE SPEND PATTERNS
> - 5. BEHAVIORAL SUGGESTIONS
> - CREDIT CARD SUMMARY (Table Format)
> Return formatted JSON instructions for batchUpdate.
> ```

**Steps:**
1. Merge insights + financials
2. Format report with dynamic section indexes and spacing
3. Use HTTP Request to push JSON to Google Docs API
4. Insert credit card table via Apps Script

---

## 📄 Sample Output Structure

### 1. EXECUTIVE SUMMARY
- BizPro Solutions' current credit card usage lacks category-specific optimization.
- Average reward yield: 1.5% vs industry avg of 2.5%

### 2. OPTIMIZATION RECOMMENDATIONS
**2.1 TRAVEL**
- Use Axis Vistara Infinite for all airfare to earn 10X points

**2.2 DINING**
- Switch dining expenses to HDFC Millennia (5% cashback)

**2.3 OFFICE SUPPLIES**
- Use Standard Chartered Ultimate for 3.3% reward rate

### 3. CARD STRATEGY SUGGESTIONS
- Drop cards with low rewards + high fees
- Consolidate card types to 3 core categories

### 4. EMPLOYEE SPEND PATTERNS
- Aarna Sood spent ₹24,775.44 in Jan 2025 using Standard Chartered Ultimate
- No late fees, low annual fee → good behavior

### 5. CREDIT CARD SUMMARY (Table)
| Employee Name | Bank | Card | Spent | Rewards | Late Fee | Due Date |
|---------------|------|------|-------|---------|----------|----------|
| Aarna Sood    | Standard Chartered | Ultimate | ₹24,775.44 | 247 pts | ₹0 | 10-Jan-2025 |

---

## 🔗 Resources & Guides

- 📄 [📘 Final Report (Sample Output)](https://github.com/SachinSavkare/Automation-Challenge-Optimizing-Corporate-Credit-Card-Usage-with-AI-Automation-n8n/blob/main/Credit%20Card%20Optimization%20Report%20%E2%80%93%202025-08-04T07_21_08.446-04_00.pdf)
- 📘 [🛠️ Project Development Guide (Steps Explained)](https://github.com/SachinSavkare/Automation-Challenge-Optimizing-Corporate-Credit-Card-Usage-with-AI-Automation-n8n/blob/main/Project%20Guide.pdf)
- 📘 [📊 Challenge Prompt (PDF)](https://github.com/SachinSavkare/Automation-Challenge-Optimizing-Corporate-Credit-Card-Usage-with-AI-Automation-n8n/blob/main/Challenge%20Prompt.pdf)
- 🧩 [Project Architecture Image](https://github.com/SachinSavkare/Automation-Challenge-Optimizing-Corporate-Credit-Card-Usage-with-AI-Automation-n8n/blob/main/Workflow%202.png)
- 📘 [🛠️ Word Document JAVA Script](https://github.com/SachinSavkare/Automation-Challenge-Optimizing-Corporate-Credit-Card-Usage-with-AI-Automation-n8n/blob/main/Word%20Document%20Report%20JAVA%20Script.txt)
- 🎞️ [🎥 PPT Presentation & Walkthrough](https://github.com/SachinSavkare/Automation-Challenge-Optimizing-Corporate-Credit-Card-Usage-with-AI-Automation-n8n/blob/main/Presentation.pptx)

---

## 🧰 Tech Stack
- **n8n**: Low-code automation engine
- **Google Gemini**: Advanced AI agent for insights and extraction
- **Google Docs API**: Report generation with batchUpdate formatting
- **Google Apps Script**: Inserts structured tables
- **Google Sheets**: Used for temporary data logging

---

## ▶️ How to Run This Project

1. Clone the repo
2. Import workflows into n8n
3. Add your credentials:
   - Google Docs API
   - Gemini Chat API
   - Google Sheets API
4. Place sample PDF into the designated folder or use email trigger
5. Click **Execute Workflow**
6. Output: Auto-generated Google Doc with insights + table

---

## 🚀 Outcome & Benefits
✅ Automates a repetitive, manual finance task  
✅ Helps CFOs make better decisions using structured insights  
✅ Demonstrates powerful use of AI + n8n + APIs in business finance

---

## 🙌 Like This Project?

If you found this project helpful or inspiring:
- 🌟 Star this GitHub repo
- 🤝 Connect with me on [LinkedIn](https://www.linkedin.com/in/sachin-savkare/)
- 📣 Share your feedback or forks

---

## 👨‍💻 Created By Sachin Savkare

For the June 2025 **Codebasics AI Toolkit Challenge**  
Role: Peter Pandey (Business Automation Specialist)  
Domain: Financial Document Automation

---

> 📌 This README is structured to meet the challenge evaluation:  
> ✅ Accuracy • ✅ Automation • ✅ Creativity • ✅ Presentation • ✅ Depth of Analysis
