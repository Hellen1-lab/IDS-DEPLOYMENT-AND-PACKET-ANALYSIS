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


   <img width="1366" height="554" alt="Screenshot 2026-09-27 143011" src="https://github.com/user-attachments/assets/929fe0a4-316f-45b0-9d10-7885e263dbbe" />

<img width="972" height="198" alt="Screenshot 2026-09-27 142833" src="https://github.com/user-attachments/assets/f6743a8f-6226-4fa2-a628-68c3ea3a43dd" />


i. Detect ICMP (ping) traffic

   
ii. Detect TCP SYN-only packets, the signature of a port scan.

   
3. Simulated an attack using Nmap's intense scan against the Kali host from a separate machine on the network.

   <img width="1210" height="696" alt="Screenshot 2026-09-27 084054" src="https://github.com/user-attachments/assets/2db42750-8667-46cb-971c-c09539fce018" />

<img width="1346" height="723" alt="Screenshot 2026-09-27 084643" src="https://github.com/user-attachments/assets/c5c3a85b-c2b8-41bd-b1a8-0054446259c0" />


4. Confirmed detection. Snort raised a real-time alert matching the custom rule.

<img width="1058" height="279" alt="Screenshot 2026-09-27 075044" src="https://github.com/user-attachments/assets/978ce47a-a2dc-40a5-9915-a157dd9c7e9d" />

<img width="1150" height="646" alt="Screenshot 2026-09-27 084141" src="https://github.com/user-attachments/assets/885c9f96-324f-4c75-9919-15c3415ce8cd" />
<img width="1155" height="577" alt="Screenshot 2026-09-27 090013" src="https://github.com/user-attachments/assets/20a236e6-9b45-41c8-9060-ac5796b9338e" />




5. Captured and analyzed the same traffic in Wireshark, confirming the packet-level pattern (single source, multiple destination ports, SYN-only flags) matched a TCP SYN scan.


   <img width="1360" height="728" alt="Screenshot 2026-09-27 084820" src="https://github.com/user-attachments/assets/4a416d58-a485-4d07-9e68-71a8c9c6bd6d" />

<img width="1289" height="690" alt="Screenshot 2026-09-27 144253" src="https://github.com/user-attachments/assets/cd2476c7-7616-4a6b-8f98-e53fd89a697d" />

   
   <img width="1356" height="629" alt="Screenshot 2026-09-27 125734" src="https://github.com/user-attachments/assets/ce99181f-c09d-4008-a673-37f8a7297a8b" />

   
<img width="1320" height="712" alt="Screenshot 2026-09-27 125859" src="https://github.com/user-attachments/assets/31442ef4-4df7-4c88-a9f2-4355579abfd3" />

<img width="1325" height="645" alt="Screenshot 2026-09-27 144648" src="https://github.com/user-attachments/assets/c5630de5-5c7a-4222-bcb8-1123b60abbca" />

<img width="1266" height="648" alt="Screenshot 2026-09-27 144623" src="https://github.com/user-attachments/assets/5e6b90b0-8266-4041-996b-e65f4d915b0f" />



NB: A source port,58890, has many destination ports. this is not normal and it is what a port scan looks like


6. Mapped the finding to MITRE ATT&CK: T1046 — Network Service Scanning.

   
7. wrote an IDS-incident report.

   
Key Takeaway


This project demonstrates the full detect → investigate → confirm loop that sits at the center of SOC analyst work: an alert is only the starting point, packet-level evidence is what confirms and explains what actually happened.
