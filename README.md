# Research Copy of Check – RPA Automation

This project automates the **“Research Copy of Check”** process in the Accounts Payable department of **ACME Systems Inc.**  
Using **UiPath**, the robot processes client requests for check copies by retrieving request details, searching across internal systems, and delivering the requested check image.

---

## 📌 Project Overview
The automation handles client requests (WI2 items) for check copies by:
- Retrieving and validating client requests in **System 1**.
- Extracting **Client ID** and **Check Number** from request PDFs.
- Searching check details across **System 1 (Web)** and **System 3 (Desktop)**.
- Downloading and submitting check images.
- Updating the work item’s status (✅ Completed or ❌ Rejected).

---

## ✨ Features
- ⏱ **80% faster processing time** per request.
- 🤖 **Full automation** from input to output.
- 🔄 **Fallback mechanism** between systems (System 1 → System 3).
- 🛡 **Exception handling** for:
  - Invalid credentials  
  - Missing or corrupted PDFs  
  - System unavailability  
- 📊 **Detailed logging & reporting** via UiPath Orchestrator.

---

## 🛠 Tech Stack
- **UiPath Studio 2023.4** – workflow design and automation.
- **UiPath Orchestrator (Cloud)** – scheduling, logging, and credential management.
- **ACME System 1 (Web v2.5)** – main platform for check search and submission.
- **ACME System 3 (Desktop v4.0)** – backup system for client record searches.
- **Microsoft Excel 2016+** – reporting and transaction logging.

---

## ⚙️ Process Flow
### AS-IS (Before Automation)
1. User receives client request (WI2).  
2. Manually logs into System 1 and searches for the check.  
3. If not found, user searches in System 3.  
4. Once found, user submits check copy and updates work item.  

### TO-BE (Automated)
1. Robot retrieves WI2 items from System 1.  
2. Extracts Client ID & Check Number from PDF.  
3. Searches in System 1 → if not found, switches to System 3.  
4. Downloads check image.  
5. Uploads check copy into System 1 and updates status.  
6. Moves to next WI2 item until queue is empty.  

---

## 🚨 Exception Handling
- **Web app not available** → retry + send email notification.  
- **Invalid credentials** → retry once + log error.  
- **No WI2 tasks** → end process gracefully.  
- **PDF unreadable** → reject work item.  
- **Upload failure** → stop execution + notify.  

---

## 📊 Reporting
- **Daily process logs** → total runs, average runtime.  
- **Transaction logs** → WI2 processed (Found vs Rejected).  
- **Error logs** → categorized by login, file, or search errors.  
- **Performance summary** → monthly trends via UiPath Insights.  

---

## 📂 Repository Structure
```

📦 Research-Copy-of-Check
┣ 📁 Documentation
┃ ┗ 📄 PDD\_WI2.pdf
┣ 📁 UiPath\_Workflows
┃ ┗ 📄 Main.xaml
┣ 📁 Logs
┃ ┗ 📄 process\_logs.xlsx
┣ 📁 Samples
┃ ┣ 📄 sample\_WI2\_request.pdf
┃ ┗ 📄 sample\_check\_copy.png
┣ 📄 README.md

````

---

## 🚀 Getting Started
1. Clone this repository:
   ```
   git clone https://github.com/<your-username>/<repo-name>.git```

2. Open the **Main.xaml** file in **UiPath Studio**.
3. Configure Orchestrator assets:
   * Credentials for System 1 & 3.
   * Queue for WI2 items.
4. Run the workflow or publish to Orchestrator for scheduling.

---

## 👨‍💻 Author

* **RÂPA Denis-Andrei**
  [GitHub Profile](https://github.com/adenis033)
