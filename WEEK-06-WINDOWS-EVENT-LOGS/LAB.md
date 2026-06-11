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
You are a SOC analyst. A workstation is showing repeated login failures followed by a successful login from the same source. Possible brute-force attack.

---

## STEP 1: COLLECT SECURITY LOGS
```powershell
Get-WinEvent -LogName Security -MaxEvents 1000
```

---

## STEP 2: FILTER FAILED LOGINS (BRUTE FORCE)
```powershell
Get-WinEvent -FilterHashtable @{LogName='Security'; Id=4625}
```

---

## STEP 3: FILTER SUCCESSFUL LOGINS
```powershell
Get-WinEvent -FilterHashtable @{LogName='Security'; Id=4624}
```

---

## STEP 4: ANALYZE PATTERN
Look for:
- Same IP repeating 4625 events
- Followed by 4624 success event
- Short time window between attempts

---

## SIMULATED ATTACK PATTERN
```
4625 -> 4625 -> 4625 -> 4624
```

---

## STEP 5: BUILD TIMELINE
Create a timeline of:
- First failed attempt
- Peak brute-force window
- Successful login moment

---

## INVESTIGATION OUTPUT
You must document:
- Source IP address
- Target username
- Time window of attack
- Whether compromise is confirmed

---

## SOC ANALYST REPORT (EXPECTED)
- Incident summary
- Attack classification (Brute Force / Credential Stuffing)
- Evidence (Event IDs)
- Recommended action (account lock, IP block)

---

## SKILL GAINED
- Windows log interpretation
- Authentication attack detection
- Timeline reconstruction