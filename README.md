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
  <img src="screnshort/ICMP.png" width="600">
</p>

4. Check packet payload
- In the bottom pane:
- Look at Data / Payload section
- You’ll see something like:
  
```bash
U1VDVEYyMDIze2 FpX2lzX2 Nvb2x9
```

- This is Base64 encoded text

5. Go to website CyberChef and use FROM BASE64
- Paste the encoded text U1VDVEYyMDIze2 FpX2lzX2 Nvb2x9

<p align="center">
  <img src="screnshort/Base64.png" width="600">
</p>

- We get the output is
  
```bash
SUCTF2023{ai_is_cool}
```
- Flag: SUCTF2023{ai_is_cool}
  
---

# Question 2: Packet Analysis (FTP)

1. Identify the protocol
   
- You used Follow TCP Stream
- You see commands like:
   - USER
   - PASS
   - RETR global_thermonuclear_war.gamerules.txt
      
```bash
global_thermonuclear_war.gamerules.txt
```

2. Find transferred file
- Important line:
   - RETR global_thermonuclear_war.gamerules.txt
- A file was downloaded via FTP
- That file likely contains the flag
- Go to File - Export Object – Find FTP-DATA
- You can see global_thermonuclear_war.gamerules.txt and you save.

<p align="center">
  <img src="screnshort/FTP DATA.png" width="600">
</p>

4. Open the file
- You get:

```bash
https://tinyurl.com/yr5zprz4
```

<p align="center">
  <img src="screnshort/URL.png" width="600">
</p>

























