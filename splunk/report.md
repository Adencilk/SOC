#  SOC Incident Analysis: [Insert Attack Name, e.g., Windows Brute Force Detection]

*   **Author:** Aden_cilk
*   **Date:** October 2026
*   **Platform:** Splunk Enterprise / TryHackMe Lab [Choose your platform]
*   **Category:** Authentication Security / Initial Access

---

##  1. Objective & Scenario
Provide a brief 2-3 sentence overview of what this lab simulates.
> **Example:** This lab simulates an attacker attempting to gain unauthorized access to a corporate Windows Workstation via Brute Force over Remote Desktop Protocol (RDP). The objective is to identify the malicious activity, determine the scope of the attempt, and extract key indicators of compromise (IOCs).

---

##  2. Log Sources & Ingestion
List the raw data inputs you used to track down the activity.
*   **Index:** `win_logs` *(or whatever your search index is)*
*   **Source Type:** `WinEventLog:Security`
*   **Key Event IDs Tracked:** `4625` (An account failed to log on)

---

##  3. The Investigative Query (SPL)
Paste the exact Splunk Processing Language (SPL) search you engineered or used.

```splunk
index=win_logs EventCode=4625 
| stats count by src_ip, user 
| where count > 10 
| sort - count
```

**Query Breakdown:**
*   `EventCode=4625`: Filters exclusively for failed login attempts.
*   `| stats count by src_ip, user`: Aggregates the total failures per unique IP address and targeted username.
*   `| where count > 10`: Drops baseline noise to focus only on high-frequency, aggressive brute force activity.

---

##  4. Visual Evidence & Analysis
*This is where you explain your findings and drop your screenshots.*

### Finding A: Aggressive Targeted Accounts
The attacker targeted multiple generic usernames over a compressed timeframe.
![Failed Logins Timeline](screenshots/failed_logins_timeline.png)

### Finding B: Attacker Source Attribution
The majority of the malicious traffic originated from the following IP address: `192.168.1.X`.

---

##  5. Analyst Takeaway & Mitigation
Summarize what a SOC team should do based on this data.
1.  **Immediate Action:** Block the offending source IP (`192.168.1.X`) at the perimeter firewall.
2.  **Account Hygiene:** Implement an account lockout policy after 5 failed attempts to render automated brute-forcing ineffective.
3.  **Alerting Setup:** Convert this SPL query into a real-time Splunk alert to notify the on-call analyst if any single IP triggers more than 20 failures in a 5-minute window.
