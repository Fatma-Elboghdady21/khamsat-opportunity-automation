
# Khamsat Freelance Opportunities Automation 🚀

An **n8n automation workflow** that collects the latest freelance service requests from **Khamsat**, extracts and organizes the available opportunities, and sends new job notifications directly to **Telegram**.

The goal is to reduce manual searching and help freelancers discover relevant opportunities faster.

---

## 📌 Project Overview

Freelancers often spend a lot of time manually browsing freelance platforms looking for new opportunities.

This workflow automates that process by:

- Fetching freelance requests from Khamsat.
- Extracting request titles, URLs, and creation dates.
- Extracting the request ID from the URL.
- Sorting requests from newest to oldest.
- Sending the opportunities to Telegram for quick access.

Instead of repeatedly checking Khamsat manually, the workflow provides the collected opportunities directly through Telegram.

---

## Workflow

This workflow automatically collects freelance opportunities from Khamsat, processes the extracted data, and sends the results to Telegram.

<p align="center">
  <img src="workflow/workflow.png" alt="Khamsat Freelance Opportunities Automation Workflow" width="900">
</p>

```text
Manual Trigger
      ↓
HTTP Request
      ↓
HTML Extraction
      ↓
JavaScript Processing
      ↓
Telegram Notification
```

---

## 🧩 Workflow Components

### 1. Manual Trigger

The workflow starts when the user clicks:

`Execute Workflow`

This allows the workflow to be tested manually.

---

### 2. HTTP Request

The workflow sends an HTTP request to the Khamsat community requests page:

```text
https://khamsat.com/community/requests
```

The page contains the available freelance requests.

---

### 3. HTML Extraction

The HTML node extracts the following information from the page:

- **Title** — the freelance request title.
- **URL** — the link to the request.
- **Created At** — the request creation date.

The extraction is based on CSS selectors targeting the request elements on the page.

---

### 4. JavaScript Data Processing

The JavaScript node transforms the extracted arrays into structured request objects.

Each request contains:

```json
{
  "request_id": "123456",
  "title": "Example freelance request",
  "url": "https://khamsat.com/requests/123456-example",
  "createdAt": "22/10/2026 01:30:00"
}
```

The script also:

- Extracts the request ID from the URL.
- Converts relative URLs into complete Khamsat URLs.
- Parses the request creation date.
- Sorts requests from newest to oldest.

---

### 5. Telegram Notification

After processing the requests, the workflow sends the opportunity information to Telegram.

The notification contains:

- The request title.
- The request URL.

Example:

```text
Hi Fatma, this is a new Khamsat job

[Request Title]

[Request URL]
```

This makes it possible to quickly open the opportunity and decide whether it is relevant.

---

## 🛠️ Technologies

- **n8n** — Workflow automation and orchestration
- **HTTP Requests** — Retrieve Khamsat page data
- **HTML Extraction** — Extract structured information from the page
- **JavaScript** — Data transformation, ID extraction, date parsing, and sorting
- **Telegram Bot** — Opportunity notifications
- **Khamsat** — Source of freelance requests

---

## 🎯 Why I Built This

As a freelancer, manually checking platforms for new opportunities can be repetitive and time-consuming.

This project demonstrates how automation can turn a manual workflow into an automated pipeline:

```text
Manual Search
      ↓
Automated Data Collection
      ↓
Data Processing
      ↓
Instant Notification
```

The idea can be extended to other freelance platforms and more advanced opportunity-monitoring systems.

---

## 🚀 Setup

### 1. Install n8n

You can run n8n locally or use an n8n-hosted instance.

### 2. Import the Workflow

Import the provided workflow JSON file into n8n.

### 3. Configure Telegram

Connect your Telegram Bot credentials and configure the destination chat.

### 4. Execute the Workflow

Run the workflow manually using:

```text
Execute Workflow
```

The workflow will fetch the available Khamsat requests, process them, and send the results to Telegram.

---

## 📂 Project Structure

```text
khamsat-freelance-automation/
│
├── khamsatWorkflow.json
└── README.md
```

---

## 🔮 Future Improvements

Possible improvements for the next version include:

- Automatic scheduled execution.
- Detecting only newly published requests.
- Filtering requests using specific keywords.
- Categorizing opportunities based on freelance skills.
- AI-based opportunity relevance scoring.
- Saving opportunities to Google Sheets or a database.
- Avoiding duplicate Telegram notifications.
- Adding priority levels for high-value opportunities.
- Creating a dashboard to analyze freelance opportunities over time.

---

## 💡 Key Learning Outcomes

This project demonstrates practical experience with:

- Workflow automation
- Web data extraction
- HTML parsing
- JavaScript data transformation
- Data normalization
- Date parsing and sorting
- API/HTTP-based workflows
- Telegram automation
- n8n workflow orchestration

---

## 👩‍💻 Author

**Fatma Elboghdady**

Data Analyst | Data & Automation Enthusiast

This project is part of my practical portfolio exploring automation, data workflows, and tools that can improve freelance opportunity discovery.
