# WEEK 07 - SIEM BASICS (SOC LAB)

## OBJECTIVE
Understand how SIEM systems collect, normalize, and correlate logs for security monitoring.

---

## TOOLS
- Splunk or ELK Stack
- Linux terminal
- Log forwarder (Universal Forwarder / Filebeat)

---

## LAB SCENARIO
Multiple systems are sending authentication logs. You must detect centralized brute-force activity.

---

## STEP 1: INGEST LOGS
Example (Splunk):
```bash
./splunk add monitor /var/log/auth.log
```

---

## STEP 2: VERIFY DATA INGESTION
```spl
index=* | head 20
```

---

## STEP 3: DETECT FAILED LOGINS
```spl
index=main "failed" OR "invalid"
```

---

## STEP 4: GROUP ATTACK SOURCES
```spl
index=main "failed" | stats count by src_ip
```

---

## STEP 5: DETECT BRUTE FORCE PATTERN
- Multiple failures from same IP
- Across multiple users
- Within short time window

---

## OUTPUT
- List of attacking IPs
- Frequency table
- Basic SIEM dashboard

---

## SOC REPORT DELIVERABLE
- Attack summary
- Affected systems
- Detection query used

---

## SKILL OUTCOME
- SIEM ingestion
- Log correlation
- Attack pattern detection