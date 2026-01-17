Security Information and Event Management system (SIEM) 
# Log Sources
Devices continuously generate logs of the activities that occur within them. We can call these devices log sources. These logs are split into two categories:

1. **Host-Centric Log Sources**: Capture events that occurred within or related to the host.
2. **Network-Centric Log Sources**: Network-related logs generated when the host communicates with another host or device.

# Why SIEM
Hosts generate thousands of logs all having different formats, and residing on different hosts.

SIEM is a security solution that collects logs from various types of log sources, standardizes theur format into a consistent one, correlates them and detect malicious actives using detection rules.

## Features of SIEM
- **Centralized Log Collection**: SIEM collects logs from all sources (endpoints, servers, firewalls, etc.) and centralizes them in one place.   
- **Normalization of Logs**: Since a SIEM solution centralizes these logs in one place, it also ensures that all the logs are broken down into different fields and presented in one consistent format.    
- **Correlation of Logs**: Individual logs are not very useful. SIEM correlates the logs of different sources and finds any relationship between them.
- **Real-time Alerting**: SIEM detects malicious activities based on the rules it contains. 
- **Dashboards and Reporting**: SIEM presents the data for analysis after being normalized and ingested. 
# Log Ingestion
 Each SIEM solution has its own way of ingesting the logs. Some common methods used are:
 1. Agent / Forwarder  
    These SIEM solutions provide a lightweight tool called an agent (forwarder by Splunk) that gets installed on the Endpoint. It is configured to capture and send all the important logs to the SIEM server.
2. **Syslog**  
    Syslog is a widely used protocol to collect data from various systems like web servers, databases, etc., and send real-time data to the centralized destination.
3. **Manual Upload**  
    Some SIEM solutions, like Splunk, ELK, etc., allow users to ingest offline data for quick analysis. Once the data is ingested, it is normalized and made available for analysis.
4. **Port-Forwarding**  
    SIEM solutions can also be configured to listen on a certain port, and then the endpoints forward the data to the SIEM instance on the listening port.
