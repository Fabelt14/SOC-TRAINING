# WEEK 01 - SOC FUNDAMENTALS (BOOTCAMP)

## OBJECTIVE
Learn how SOC analysts think and how logs become investigations.

---

## LAB SETUP
Linux VM or any terminal environment

---

## STEP 1: CREATE WORKSPACE
mkdir soc-week1
cd soc-week1

---

## STEP 2: CREATE LOG FILE
Create auth.log and add:

Jan 10 10:00:01 failed login user root ip 192.168.1.10
Jan 10 10:00:05 failed login user root ip 192.168.1.10
Jan 10 10:00:09 failed login user root ip 192.168.1.10
Jan 10 10:00:15 success login user root ip 192.168.1.10

---

## STEP 3: ANALYZE LOGS
grep failed auth.log
count failed attempts
extract ip address

---

## STEP 4: BUILD TIMELINE
Identify first attack time
Identify success time
Measure attack duration

---

## STEP 5: WRITE REPORT
Create report.md with:
- summary
- evidence
- conclusion

---

## OUTCOME
Understand brute force behavior and basic SOC workflow