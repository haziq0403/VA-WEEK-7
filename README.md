# 🔐 Vulnerability Analysis – Lab Week 7

## 📌 Course Information
- **Course:** IKB21403 – Vulnerability Analysis  
- **Programme:** Bachelor of IT (Hons) in Computer System Security  
- **Student Name:** Haziq Danial Bin Nor Azan  

---

## Project Overview
This lab focuses on analysing network traffic and identifying vulnerabilities using tools such as Wireshark, Nmap, and Nessus. The objective is to extract hidden information and understand security weaknesses in a system.

---

# Question 1: Packet Analysis (ICMP)

## Steps:
1. Open **Wireshark**  
2. Load `packet1.pcap`  
3. Observe ICMP traffic  
4. Right-click any ICMP packet → **Follow → ICMP Stream**  
5. Check **Payload section**  
6. Identify encoded text  
7. Decode using **CyberChef (Base64)**  

## Evidence
![ICMP Stream](screenshots/wireshark_icmp.png)
![Base64 Decode](screenshots/base64_decode.png)

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
