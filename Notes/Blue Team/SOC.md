A SOC (Security Operations Center) is a dedicated facility operated by specialized security team. This team monitors an organizations network and resources to identify suspicious activity.

The main focus of the SOC team is to keep Detection and Response intact.
## Detection
- Detect vulnerabilities
- Detect unauthorized activity
- Detect policy violations
- Detect intrusions
## Response
- Support with the incident response

There are three pillars of a SOC.
- People
- Process
- Technology
## People
![](SOC_team.png)
- **SOC Analyst (Level 1):** First responders to any detection
- **SOC Analyst (Level 2):** Helps level 1 with deeper investigations and correlates data from multiple sources
- **SOC Analyst (Level 3):** Look for any threat indicators and support in the incident response activities
- **Security Engineer:** Deploy and configure security solutions to ensure smooth operation
- **Detection Engineer:** Create security rules
- **SOC Manager:** Manages the processes the SOC team follows and provides support

## Process
#### Alert Triage
- Basis of the SOC team
- First response to any alert is to perform the triage
- Triage is focused on analyzing the specific alert
- Alert triage is about answering the 5 Ws
	- What
	- When
	- Where
	- Who
	- Why
#### Reporting
The detected harmful alerts need to be escalated to higher-level analyst for a timely response and resolution. These alerts are escalated as tickets and assigned to relevant people. The report should discuss all the 5 Ws along with a thorough analysis, and screenshots should be used as evidence. 
#### Incident Response and Forensics
Sometimes the reported detections point to highly malicious activities that are critical. In these scenarios high-level teams initiate an incident response.

## Technology
The technology portion in the SOC pillars refers to the security solutions.
These security solutions minimize the SOC team's manual effort to detect and respond to threats.

Security Solutions centralize all the information of the devices or applications present in the network and automate the detection and response capabilities.
#### Security Solutions:
- **SIEM:** Security Information and Event Management (SIEM) is a popular tool used in almost every SOC environment. Collects logs from network devices and detection rules are configured in the SIEM solution.
- **EDR:** Endpoint Detection and Response (EDR) provides the SOC team with detailed real-time and historical visibility of the devices activites.
- **Firewall:** Functions purely for network security and acts as a barrier between your internal and external networks.
- **IDS:** Intrusion Detection System (IDS) monitors your networks for malicious activity or policy violations and creates alerts based on so.
- **IPS:** Intrusion Protection System (IPS) does the same as a IDS but blocks malicious traffic.
