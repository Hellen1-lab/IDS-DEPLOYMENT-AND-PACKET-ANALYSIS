# IDS-DEPLOYMENT-AND-PACKET-ANALYSIS

IDS Deployment & Packet Analysis with Snort


A project demonstrating deployment of an open-source Intrusion Detection System (Snort), custom rule-writing, and packet-level traffic analysis using Wireshark.


Overview


This project simulates a SOC analyst workflow: 

1. Deploy a detection tool.

 2. Configure it for a specific network.

 3. Teach it what to look for.
  
 4. validate it against real (simulated) attacker traffic.
   
 5. confirm findings at the packet level.

    
Tools Used


Snort++ 3.12.2.0 — open-source network intrusion detection system.


Kali Linux — IDS host (VM)


Nmap, used to simulate a network reconnaissance (port scan) attack.


Wireshark, for packet capture and analysis.


What Was Done


1. Deployed Snort on a Kali Linux VM and configured HOME_NET to match the lab network (192.168.10.0/24).
<img width="1366" height="681" alt="Screenshot 2026-09-25 195950" src="https://github.com/user-attachments/assets/208df9ff-a9ad-4326-a61e-858921f4a33c" />

 <img width="1349" height="690" alt="Screenshot 2026-09-27 073259" src="https://github.com/user-attachments/assets/1dd7e660-bd37-4918-91da-ae4d25c069c6" />



2. Wrote custom detection rules:


i. Detect ICMP (ping) traffic

   
ii. Detect TCP SYN-only packets, the signature of a port scan.

   
3. Simulated an attack using Nmap's intense scan against the Kali host from a separate machine on the network.

   
4. Confirmed detection. Snort raised a real-time alert matching the custom rule.

   
5. Captured and analyzed the same traffic in Wireshark, confirming the packet-level pattern (single source, multiple destination ports, SYN-only flags) matched a TCP SYN scan.

   
6. Mapped the finding to MITRE ATT&CK: T1046 — Network Service Scanning.

   
7. wrote an IDS-incident report.

   
Key Takeaway


This project demonstrates the full detect → investigate → confirm loop that sits at the center of SOC analyst work: an alert is only the starting point, packet-level evidence is what confirms and explains what actually happened.
