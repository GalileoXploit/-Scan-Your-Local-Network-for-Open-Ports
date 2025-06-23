🛠️ **Tools Used**
Nmap 7.97
Official site: https://nmap.org

✅ **Steps Performed**
Installed Nmap from the official Nmap website.
Identified the local IP range using the following command: ipconfig 
Local subnet: 192.168.56.1/24
Scanned the network using a TCP SYN scan: nmap -sS -oN scan.results.txt 192.168.56.1/24
The -sS flag performs a SYN scan.
The -oN flag saves the results in human-readable text format.
Noted active hosts and open ports:
Only one host was found to be up: 192.168.56.1
The following ports were open:
22/tcp   - SSH
135/tcp  - MSRPC
139/tcp  - NetBIOS-SSN
445/tcp  - Microsoft-DS
1042/tcp - Afrog (ASUS Armoury Crate)
1043/tcp - BOINC (ASUS Armoury Crate)
| Port | Service      | Description                                | Potential Risk                            |
| ---- | ------------ | ------------------------------------------ | ----------------------------------------- |
| 22   | SSH          | Secure shell remote login                  | Brute-force or weak login vulnerabilities |
| 135  | MSRPC        | Windows Remote Procedure Call for DCOM     | Used in many known Windows exploits       |
| 139  | NetBIOS-SSN  | Legacy file/printer sharing                | Exposure risk outside LAN                 |
| 445  | Microsoft-DS | SMB protocol (file sharing)                | SMB-related malware (e.g., EternalBlue)   |
| 1042 | Afrog        | ASUS Armoury Crate internal port           | Can be abused if misconfigured            |
| 1043 | BOINC        | ASUS-related or distributed computing port | Known to be used by some malware          |
Investigated and verified processes for ports 1042 & 1043:
All services were confirmed to be part of ASUS Armoury Crate.
No immediate malware was detected.
Saved scan results as: scan.results.txt

🔐 **Recommendations**
Ensure ports like 135, 139, and 445 are firewalled from public networks
Regularly monitor systems using netstat or Nmap.
Uninstall unused software like ASUS Armoury Crate if those ports are not needed.




