# WEEK 06 - WINDOWS EVENT LOGS (SOC LAB)

## OBJECTIVE
Learn how to investigate authentication attacks and privilege escalation using Windows Event Logs.

---

## TOOLS
- Windows Event Viewer
- PowerShell
- Get-WinEvent

---

## LAB SCENARIO
You are a SOC analyst. A workstation shows repeated login failures followed by a successful login from the same source. Possible brute-force attack.

---

## STEP 1: COLLECT SECURITY LOGS
```powershell
Get-WinEvent -LogName Security -MaxEvents 1000
```

---

## STEP 2: FILTER FAILED LOGINS (4625)
```powershell
Get-WinEvent -FilterHashtable @{LogName='Security'; Id=4625}
```

---

## STEP 3: FILTER SUCCESSFUL LOGINS (4624)
```powershell
Get-WinEvent -FilterHashtable @{LogName='Security'; Id=4624}
```

---

## STEP 4: ANALYZE ATTACK PATTERN
Look for:
- Same IP repeating failed attempts
- Followed by successful authentication
- Short time window between events

Pattern:
4625 → 4625 → 4625 → 4624

---

## STEP 5: TIMELINE CONSTRUCTION
- First failed attempt
- Brute-force peak
- Successful login event

---

## INVESTIGATION OUTPUT
- Source IP
- Target user
- Attack duration
- Compromise confirmation

---

## SOC REPORT DELIVERABLE
- Incident summary
- Attack classification
- Evidence (Event IDs)
- Recommended response actions

---

## SKILL OUTCOME
- Windows log analysis
- Brute-force detection
- Incident timeline reconstruction