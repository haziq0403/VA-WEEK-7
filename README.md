# 🔐 Vulnerability Analysis – Lab Week 7

## 📌 Course Information
- **Course:** IKB21403 – Vulnerability Analysis  
- **Programme:** Bachelor of IT (Hons) in Computer System Security  
- **Student Name:** Haziq Danial Bin Nor Azan  

---

## Project Overview
This lab focuses on analysing network traffic and identifying vulnerabilities using tools such as Wireshark, Nmap, and Nessus. The objective is to extract hidden information and understand security weaknesses in a system.

---

# Question 1: Analyse packet1.pcap and find the flag.

## Steps:
1. Open the .pcap file
   
- Launch Wireshark
- Open packet1.pcap
  
2. Look for suspicious traffic
   
- Most packets are ICMP (ping)
  
3. Follow the ICMP stream
   
- In Wireshark:
1. Click any ICMP packet
2. Right-click → Follow → ICMP Stream 

<p align="center">
  <img src="screenshoots/wireshark_icmp.png" width="600">
</p>


## Result: SUCTF2023{ai_is_cool}


---

# Question 2: Packet Analysis (FTP)

## Steps:
1. Open `packet2.pcap` in Wireshark  
2. Follow **TCP Stream**  
3. Identify FTP commands:
   - USER  
   - PASS  
   - RETR global_thermonuclear_war.gamerules.txt  

4. Go to: File → Export Objects → FTP-DATA

5. Save the file  
6. Open file → find TinyURL  
7. Decode using **Tic-Tac-Toe Cipher (dCode)**  

## Evidence
![TCP Stream](screenshots/tcp_stream.png)
![FTP Export](screenshots/ftp_export.png)
![Cipher Decode](screenshots/cipher_decode.png)

## Result: EXMACHINAAVA


---

# Question 3: Nmap Analysis

## Steps:
1. Review Nmap output  
2. Identify open ports:
   - 21 (FTP)  
   - 22 (SSH)  
   - 80 (HTTP)  
   - 139 (NetBIOS)  
   - 445 (SMB)  

3. Analyse vulnerabilities  
4. Identify highest risk port  

## Evidence
![Nmap Result](screenshots/nmap_result.png)

## Key Finding:
- **Highest Risk:** Port 445 (SMB)  
- **Reason:** Remote Code Execution (EternalBlue)

---

# Question 4: OS Fingerprinting (TTL)

## Steps:
1. Observe TTL values in packets  

## Analysis:
- TTL = 64 → Linux / Unix  
- TTL = 128 → Windows  
- TTL = 255 → Router / Network Device  

## Evidence
![TTL Analysis](screenshots/ttl_analysis.png)

---

# Question 5: Nessus Analysis

## Steps:
1. Start Nessus:
2. Open browser:
3. Login  
4. Import:
5. Go to:
   - My Basic Network Scan  
   - Vulnerabilities  
   - Search: Tomcat  

## Evidence
![Nessus Scan](screenshots/nessus_scan.png)

## Findings:
- **Vulnerability:** Ghostcat  
- **CVSS Score:** 9.8 (Critical)  
- **Port:** 8009  
- **Protocol:** AJP  

## CVE:
- CVE-2020-1938  
- CVE-2020-1745  

---

# Tools Used
- Wireshark  
- Nmap  
- Nessus  
- CyberChef  
- dCode  
