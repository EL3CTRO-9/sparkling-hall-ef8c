---
title: "Raspberry Pi Honey Pot"
description: "Lorem ipsum dolor sit amet"
pubDate: "April 01 2025"
heroImage: "/blog1.jpg"
---

# Setting Up a Raspberry Pi Honeypot for Network Threat Monitoring

## Why I Set Up the Honeypot

As part of my **SANS Internet Storm Center Internship**, I wanted to explore real-world cyber threats by deploying a honeypot. This would allow me to collect attack data, analyze malicious activity, and understand how attackers interact with exposed systems. 

By setting up a honeypot, I aimed to:
- Monitor malicious activity targeting my network.
- Identify common attack vectors used against IoT and home networks.
- Gain hands-on experience in setting up a **DShield sensor** and integrating it with a **SIEM**.

---

## Requirements

To deploy the honeypot, I used:

- **Raspberry Pi 4**
- **Cooling Fan** (for heat management)
- **Ethernet Cable** (for stable network connection)
- **SD Card** (to load the operating system)

---

## Setup Process

### 1. Installing the Raspberry Pi OS
1. Used **Raspberry Pi Imager** to download **64-bit Raspberry Pi OS** onto the SD card.
2. Configured SSH access, Wi-Fi, and hostname before flashing the OS.

### 2. Configuring SSH & Network Access
1. Used **PuTTY Key Generator** to create a private key and saved the **public key**.
2. Added the **Wi-Fi SSID & password** (if connecting via Wi-Fi).
3. After flashing the SD card, ejected and inserted it into the Raspberry Pi.

### 3. Hardware Assembly
1. Attached the **cooling block and fan** onto the RPi module.
2. Connected **Ethernet cable** from the RPi to my router.
3. Powered the RPi using an **old phone charger**.

### 4. SSH Connection & Honeypot Setup
1. Established an **SSH connection** using PuTTY on port **22**.
2. Cloned the **DShield Honeypot repository** and followed the official installation guide:
   - 📌 [Installation Instructions](https://github.com/DShield-ISC/dshield/blob/main/docs/install-instructions/Raspbian.md)
3. Checked for updates and verified the logs.

### 5. Exposing the Honeypot for Web Logs
- Initially, the honeypot did **not collect web logs** because it was not properly exposed.
- The **Raspberry Pi did not have a routable IP address**, preventing external traffic from reaching it.
- To resolve this:
  1. Logged into the **router configuration page**.
  2. Placed the **Raspberry Pi in the DMZ** to expose it directly to incoming connections.
  3. Ran `status.sh` again to confirm it was working.

### 6. Verifying Data Collection
- After these changes, the honeypot successfully logged attack data.
- The setup now **monitors malicious activity targeting my home network**.
- Next step: **Integrating with a SIEM for deeper analysis**.

---

## Challenges Faced

🔹 **Setting Up SSH & Public Key Authentication**
- It was my **first time configuring SSH keys**, and I initially struggled with how private/public key authentication worked.
- After watching a few tutorials and consulting my mentors, I was able to set it up correctly.

🔹 **Missing Web Logs Issue**
- Despite placing the RPi in the **DMZ**, the `status.sh` script still showed **missing web logs**.
- After investigating, I found that the logs were actually **being collected**, but the script failed to detect them properly. This was likely a minor bug in the script.

---

## What Can Be Achieved?

🚀 **Real-time Threat Intelligence**
- The honeypot captures **brute-force attacks, port scans, and exploit attempts**.
- Data can be shared with **threat intelligence platforms** for further analysis.

📊 **SIEM Integration**
- Logs can be **ingested into a Security Information and Event Management (SIEM) system**.
- Visualizing the attacks helps understand **who is targeting the network and how**.

🔍 **Learning & Research**
- By analyzing the data, I can study **common attack patterns**.
- It provides valuable **hands-on experience in network security** and cyber threat monitoring.

---

## GitHub Repository

You can find the setup guide and configurations in my GitHub repository:

🔗 [GitHub - My Honeypot Setup](https://github.com/DShield-ISC/dshield)

---

## Conclusion

Setting up a **Raspberry Pi honeypot** was a great learning experience. It gave me insight into **real-world cyber threats** and how attackers interact with exposed systems. This setup is now an essential part of my **home lab for cybersecurity research**.


