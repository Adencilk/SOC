#  Splunk SIEM Analytics & SOC Lab

Welcome to my Splunk documentation repository. This section serves as a practical portfolio of my experience as a Security Operations Center (SOC) Analyst. Here, I document how I ingest log sources, construct Splunk Processing Language (SPL) queries, build operational dashboards, and analyze security events.

##  Projects & Lab Write-ups

*   **[Project 1 Title: e.g., Windows RDP Brute Force Detection](report.md)**  
    *   **Objective:** Detected and analyzed brute-force authentication attempts using Windows Event Logs.
    *   **Log Sources:** `WinEventLog:Security` (Event ID 4625).
    *   **Core Concepts:** SPL aggregation, threshold alerting, and geo-ip mapping.
*   **[Project 2 Title: e.g., Investigating Phishing Indicators]** *(Coming Soon)*  
    *   **Objective:** Analyzing web proxy and email gateway logs to trace malicious attachment execution.

---

##  Environment & Tools

*   **SIEM Platform:** Splunk Enterprise / Splunk Cloud
*   **Operating Systems:** Linux (Ubuntu), Windows Server
*   **Data Parsers & Forwarders:** Splunk Universal Forwarder, Sysmon
*   **Lab Platforms:** [e.g., TryHackMe / HackTheBox / Local VirtualBox Environment]

---

##  Repository Structure

```text
splunk/
├── dashboards/          # XML source code for custom SOC dashboards
├── queries/             # Saved SPL hunting and detection queries (.spl)
├── screenshots/         # Visual evidence of alerts, dashboards, and ingest paths
├── README.md            # Directory overview and portfolio index
└── report.md            # Detailed lab walkthroughs and incident analysis
```

---

## 🔍 Core SPL Skills Demonstrated

Throughout these labs, I actively utilize and demonstrate proficiency in:
*   **Data Transformation:** `eval`, `rex` (Regular Expressions), `lookup` tables.
*   **Statistical Analysis:** `stats`, `chart`, `timechart`, `top`.
*   **Search Optimization:** Filtering early, macro utilization, and managing index structures.

---

## 📈 Featured Dashboard Preview

*(Tip: Place a high-quality screenshot of your best custom Splunk dashboard right here!)*
![SOC Dashboard Preview](screenshots/your_best_dashboard_preview.png)
