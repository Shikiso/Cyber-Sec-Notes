The act of investigating digital devices thoroughly after a crime to find and analyze evidence for legal action.

NIST (Nation Institute of Standard and Technology) defines a general process for every case.
1. **Collection**: Collecting data and devices that can be useful
2. **Examination**: Filter data and extract data of interest
3. **Analysis**: Analyze the data by correlating with with multiple pieces of evidence to draw a conclusion
4. **Reporting**: Create a report that contains the investigations methodology and detailed findings from collected evidence.

Various pieces of evidence can be found at a crime scene. Analyzing multiple categories of evidence requires various tools and techniques. There are different types of digital forensics, all with their own collection and analysis methodologies. Some commons ones are:
- **Computer forensics:** The most common type of digital forensics is computer forensics, which concerns investigating computers, the devices most commonly used in crimes.
- **Mobile forensics:** Mobile forensics involves investigating mobile devices and extracting evidence such as call records, text messages, GPS locations, and more.
- **Network forensics:** This area of forensics covers investigation beyond individual devices. It includes the whole network. The majority of the evidence found in networks is the network traffic logs.
- **Database forensics:** Many critical data is stored in dedicated databases. Database forensics investigates any intrusion into these databases that results in data modification or exfiltration.
- **Cloud forensics:** Cloud forensics is the type of forensics that involves investigating data stored on cloud infrastructure. This type of forensics sometimes gets tricky for the investigators as there is little evidence on cloud infrastructures.
- **Email forensics:** Email, the most common communication method between professionals, has become an important part of digital forensics. Emails are investigated to determine whether they are part of phishing or fraudulent campaigns.

# Evident Acquisition   
The forensics team should obtain authorization from the relevant authorities before collecting any data. 
Evidence collected before authorization may be deemed inadmissible in court.

## Chain of Custody
A chain of custody document is used to keep track of who uses what evidence so that in the case evidence has been altered someone is held responsible.
The document will have key details such as:
- Description of evidence
- Name of individuals who collected the evidence
- Data and time of evidence collection
- Storage location of each piece of evidence
- Access times and the individual record who accessed the evidence

## Write Blockers
Write blockers are a tool used for collecting evidence of a hard drive. If one was the do this normally the computer may change the date of when a file is accessed, altering the evidence. A write blocker blocks any attempt to write the the drive.

# Windows Forensics
The most common types of evidence collected from crime scenes are desktop computers and laptops. Which can have different operating systems running on them such as windows which is a very common operating system.

As part of the data collection phase, forensic images of the Windows operating system are taken. These images are bit-by-bit copies of the whole operating system.
Two different categories of the forensic image are taken:
- **Disk image**: Disk image contains all the data present on the storage device of the system, (non-volatile) .
- **Memory Image**: The memory image contains the data inside the operating systems RAM (volatile). This is collected first.