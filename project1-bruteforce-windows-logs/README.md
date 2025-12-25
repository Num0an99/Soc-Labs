# Project 1 – Brute Force Detection Using Windows Security Logs

## Objective

The objective of this project was to simulate a basic brute-force login scenario on a Windows system and detect it using Windows Security Event Logs, similar to how a Junior SOC Analyst would investigate repeated authentication failures.

## Environment

- Operating System: Windows 11
- Log Source: Windows Security Event Log  
- Tools Used: Event Viewer  
- Test Account: Local user account created for lab purposes  

## Scenario Overview

In this lab, multiple failed login attempts were intentionally generated against a local Windows user account, followed by a successful login. The goal was to identify and analyze the authentication events recorded by Windows and determine whether the activity could indicate a brute-force attempt.

## Steps Performed

1. Created a local Windows user account to safely simulate authentication attempts.
2. Generated multiple failed login attempts by repeatedly entering an incorrect password for the test account.
3. Successfully logged in after the failed attempts to generate a corresponding successful logon event.
4. Opened Event Viewer and navigated to:
   - Windows Logs → Security
5. Filtered Security logs for Event ID 4625 to identify failed logon attempts.
6. Observed multiple failed authentication events occurring within a short time window.
7. Filtered Security logs for Event ID 4624 to identify the successful logon event following the failures.

## Key Findings

- Event ID 4625 records failed logon attempts, including details such as account name and failure reason.
- Multiple Event ID 4625 entries for the same account within a short timeframe may indicate:
  - User error (forgotten password), or
  - A potential brute-force attack attempt.
- Event ID 4624 records successful logon events and can be correlated with failed attempts to understand the full authentication sequence.

## SOC Analyst Perspective

From a SOC perspective, this activity would be triaged by:

- Reviewing the volume and frequency of failed logon attempts.
- Determining whether the activity is consistent with normal user behavior or suspicious activity.
- Correlating failed logons with a subsequent successful login.
- Escalating the incident if thresholds are exceeded (e.g., excessive failures, unusual source, or repeated behavior).
- Implementing controls such as account lockout, alerting rules, or further monitoring.

## What I Learned

- How Windows records authentication activity in the Security Event Log.
- How to identify failed and successful logon events using Event IDs.
- How brute-force behavior appears from a log analysis perspective.
- How a SOC analyst approaches authentication-related alerts using evidence and context rather than assumptions.
