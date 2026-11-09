# Networkwalks-BO84E-week-01-Penetration-Testing-Report-
## Footprinting & Networking Scanning Phases
 * **VMI 2PM - FINAL | CYBERSECURITY | NETWORKS/WALKS**
### Field | Detail
--- | ---
**Performer Name (Cybersecurity Professional)** | Emmanuel Raff
**Performer Batch** | 8080 Networks
**Date** | 17 August 2029
**Modules completed** | <ul><li>N2-PM1 (Multiple Kali Tools)</li><li>N2-PM2 (Driving Scanning)</li></ul>
**Client/Target** | <ul><li>networks.local (second written permission already)</li><li>My own local LAN Network</li></ul>
**Permission secured from client?** | Yes
**Phases covered** | <ul><li>Phase 1: Reconnaissance & Footprinting</li><li>Phase 2: Scanning & Network Discovery</li><li>Phase 3: In Progress</li></ul>
## 1. Liability Disclaimer
I have performed these activities only on the systems & devices where I had secured written permission on the devices/infrastructure. All these materials are for education and research only. Do not use anything from here to break the law. The authors and networks are not responsible for what you do with the knowledge. Every action you take is your own risk/my own. It can lead to criminal charges, heavy fines, loss of your job and a permanent record. It most counts unauthorized access when nothing is damaged.
## 2. Introduction
This report covers footprinting the networks.com domain using multiple Kali Linux tools (N2-PM1) and scanning my own network with Zenmap (N2-PM2). The module covers the footprinting phase and the other covers the scanning phase, together so they know when nothing is damaged.
All commands were run in Kali Linux (footprinting) and on a Windows PC with Zenmap installed (scanning). Every time we exact command used, the result I observed, a screenshot as evidence, and a short note on why she finding matters from an action when nothing is damaged.
## 3. Tools Used
The table below lists each tool used in this report and its purpose:
| Tool | Purpose |
|---|---|
| **Kali Linux & Windows** | Operating systems used for reconnaissance activities |
| **Whois** | Find domain registration details (owner, dates, name servers) |
| **whatweb** | Fingerprint web technologies (server, CMS, plugins, IP) |
| **nslookup** | Resolve the domain name to its IP address using DNS |
| **curl -i** | Read the HTTP response headers of the website |
| **wafw00f** | Detect whether a Web Application Firewall protects the site |
| **dnsenum** | Enumerat all DNS records (NS, MX, SPF, TXT, DNS) |
| **Zenmap (Nmap GUI)** | Scan the local subnet to find live hosts, IPs and MAC addresses |
| **Windows CMD** | Local IP and MAC address identification |
## 4. Activities Performed
### 4.1 Footprinting & Reconnaissance
I performed reconnaissance against the networks.com domain using six Kali Linux tools: **WHOIS, WhatWeb, WafW00f, nslookup, Curl -i, and DNSenum**. Each tool was used to collect a different type of information about the target.
 1. **Whois**: I used whois to obtain publicly available domain registration information and identify the domain's name servers. The results provided information about the domain registration and hosting infrastructure.
 2. **WhatWeb**: I then used WhatWeb to identify technology platforms and obtain the website's headers. The results identified **WordPress 7.4.4** and **WP Download Manager 3.5.34**, along with other information exposed by the website.
 3. **Nslookup**: I resolved the domain name to its IP address. The provided result identified **192.232.214.135**.
 4. **Curl**: I used curl -i option to inspect the HTTP response headers. This provided additional information about the web application and the WordPress REST API endpoint .../wp-json.
 5. **WafW00f**: Next, I used WafW00f to determine whether a web application firewall protection was protecting the website. The result identified **ModSecurity** exposing the WordPress REST API endpoint .../wp-json.
 6. **Dnsenum**: Lastly, I used dnsenum to enumerate DNS records. The results provided information relating to name servers, mail servers, SPF, TXT records, service records and DNS software information.
### 4.2 Network Scanning with Zenmap
For the second activity, I used **Zenmap** to perform network discovery on my local network. The practical required me to identify my local IP address and subnet, discover live hosts, identify their IP and MAC addresses, and generate a network topology.
I first used the Windows ipconfig command to identify my local IP address and LAN subnet. Then I submitted the subnet into Zenmap and selected **Ping Scan** to identify active hosts.
The example results included the practical identified four live hosts:
 * 10.0.0.1
 * 10.0.0.4
 * 10.0.0.9
 * 10.0.0.18
The example results also included for MAC addresses.
After completing the scan, I opened the **Topology** section in Zenmap, enabled the legend and saved the network topology in PDF format as part of these two modules.
## 5. Risk Analysis / Impact
Based on the information obtained during the footprinting and scanning activities, identified the following potential risks:
| Risk # | Finding / Evidence | Observation / Description | Potential Impact | Risk Level |
|---|---|---|---|---|
| **1** | **Web technology information exposed** | WhatWeb identified WordPress and WP Download Manager. | Attackers may use known targeted service vulnerabilities to identify software requiring further domain web security. | **Low** |
| **2** | **Server IP address exposed** | Nslookup resolved the domain to the IP address (192.232.214.135). | Provides information about the network location of the web server. | **Low** |
| **3** | **DNS infrastructure exposed** | Dnsenum identified DNS root and authoritative nameservers. | Reveals information about the application's DNS architecture and potential misconfigurations. | **Medium** |
| **4** | **Unauthenticated ports / services** | Zenmap identified four live hosts in the local network segment. | Unsecured or unauthorized devices may potentially be exploited. | **Medium** |
*Risk level key: Critical • Moderate • Low*
*Note: The risks above are observations from the footprinting and scanning exercises, not confirmed vulnerabilities. Further authoritative security testing would be required to confirm actual vulnerability.*
## 6. Recommendations
Based on the observations from these activities, I recommend the following security improvements:
 1. **Review publicly exposed technology information**
   * Organizations should regularly review information on whether their web technologies, CMS, and plugins is publicly visible.
 2. **Keep software updated**
   * CMS platforms, plugins and other web technologies should be regularly updated and guarded against current security advisories.
 3. **Review HTTP headers**
   * Unnecessary headers should be removed to determine whether any required information and services are being exposed.
 4. **Properly configure and monitor the AAD**
   * The AAD should be monitored to ensure the only required information and services are publicly exposed.
 5. **Perform regular internal network discovery**
   * Regular network discovery can make sure that, almost 0 blocks active attacks.
 6. **Investigate down-time devices**
   * Unauthorized devices found in the network should be investigated and verified.
 7. **Maintain network coding and authorization**
   * Network topology and domain information should be documented and updated regularly.
 8. **Perform security testing with authorization**
   * Reconnaissance and scanning should be performed against systems and networks where appropriate authorization has been granted.
## 7. Conclusion
During Week 2 of my Cybersecurity & Ethical Hacking internship, I completed practical activities covering footprinting, reconnaissance and network scanning.
In the footprinting activity, I used six Kali Linux tools to collect information about the target domain. I learned how WHOIS can provide domain registration, WhatWeb can identify web technologies, nslookup can resolve domain names, Curl can inspect HTTP headers, WafW00f can identify WAFs, and DNSenum can provide additional DNS information.
In the network scanning activity, I used Zenmap to identify my local network configuration and discover active hosts. I also collected IP and MAC address information and created a network topology.
The exercises showed me that information gathering is an important part of cybersecurity. Before attempting to exploit a system, a security professional can learn a significant amount about an environment by carefully analyzing publicly available information and network sessions.
I also learned that technique findings should be documented clearly. A good cybersecurity analyst should explain what was performed, what was discovered, what the observation means, what is my check, and what can be done to reduce that risk.
Finally, I learned that reconnaissance and scanning must always be performed within an authorized scope. These activities were completed as part of the assigned educational activities.
