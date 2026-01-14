Devices have multiple applications running all creating logs. These logs can have something to do with a malicious attack in which case we need a way to know without going through thousands of logs. So we create alerts which alert us if someone abnormal is occurring.

When checking alerts they can either be false positive (alert triggered but nothing needs attention) or true positive (alerts triggered and something needs attention).

# Incident Types
- **Malware Infections**: Malware is a malicious program that can damage a system, network, or application.
- **Security Breaches:** Security Breaches arise when an unauthorized person gets access to confidential data (something we don’t want them to see or have). 
- **Data Leaks:** Data leaks are incidents in which confidential information of an individual or an organization is exposed to unauthorized entities.
- **Insider Attacks:** Incidents from within an organization are known as insider attacks. 
- **Denial Of Service Attacks:** Denial of Service attacks, or DoS attacks, are incidents where the attacker floods a system/network/application with false requests, eventually making it unavailable to legitimate users.

# Incident Response Process
Incident response frameworks help by providing a structured process for incident response. Two commonly used frameworks are SANS and NIST.
## SANS
| Phase           | Explanation                                                                                                                                                                                                                                                                                      | Example                                                                                                                                                                                                        |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Preparation     | This is the first phase. The preparation phase includes building the necessary resources to handle an incident. These resources include developing incident response teams, having a proper incident response plan in place, and deploying necessary security solutions to combat the incidents. | Conducting awareness training for employees on phishing emails. Phishing emails are fraudulent emails sent by malicious attackers that can trick you into performing actions that can lead you to an incident. |
| Identification  | The identification phase refers to looking for any abnormal behavior that may indicate an incident. This involves using various security solutions and techniques to monitor abnormal events.                                                                                                    | The security team notices a huge amount of data being sent out from one of the hosts. Upon analysis, it was found to be compromised after a malicious file was downloaded from a phishing email attachment.    |
| Containment     | Once an incident has been identified, the next step should be to contain it. This means minimizing the impact of the attack. This is usually done by isolating the victim machine, disabling the compromised user accounts, etc.                                                                 | The Security team isolates the host from the network to minimize the impact and not allow the attacker to jump to other systems, leveraging the compromised host.                                              |
| Eradication     | This phase, as its name suggests, involves removing the threat from the attacked environment. The threat may be of any kind. The eradication phase will ensure the subject environment is clean, and now we can move to the recovery phase.                                                      | A deep malware scan was executed on the system to remove the malicious software from the host.                                                                                                                 |
| Recovery        | The recovery phase is very important in this chain. It involves recovering the affected systems from backup or rebuilding them. The recovered systems are then tested and are ready to use.                                                                                                      | The compromised host was re-configured, and the exfiltrated data was restored from the backup.                                                                                                                 |
| Lessons Learned | This is also an important part of the incident response lifecycle. Gaps in the detection and analysis of the incident are identified and documented, helping to improve the overall process in future incidents.                                                                                 | Conducting a post-incident review meeting to analyze the incident's root cause and improve the security to prevent future attacks.                                                                             |

## NIST
![NIST Incident Response phases.](https://tryhackme-images.s3.amazonaws.com/user-uploads/6645aa8c024f7893371eb7ac/room-content/6645aa8c024f7893371eb7ac-1718268206803)

## Comparison
![](https://tryhackme-images.s3.amazonaws.com/user-uploads/6645aa8c024f7893371eb7ac/room-content/6645aa8c024f7893371eb7ac-1723217056943.png)

# Incident Response Techniques
It is very hard to look for abnormal behavior and identify incidents manually. There are multiple security solutions that serve their own unique roles in detecting any incidents. Some even have the capability to respond to the incidents and execute the other phases of life cycle, such as containment and eradication.
- **SIEM:** The Security Information and Event Management Solution (SIEM) collects all important logs in one centralized location and correlates them to identify incidents.
- **AV:** Antivirus (AV) detects known malicious programs in a system and regularly scans your system for these.
- **EDR:** Endpoint Detection and Response (EDR) is deployed on every system, protecting it against some advanced-level threats. This solution can also contain and eradicate the threat.

**Playbooks**: Step-by-step comprehensive guidelines for incident response
**Runbooks**: Step-by-step execution of specific steps during the different incidents.
