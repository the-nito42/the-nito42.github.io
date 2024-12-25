---
layout: post
title: "Setting Up a Raspberry Pi Zero 2W for Pentesting Wireless Network Attacks with Besside-NG and Sn1pern"
date: 2025-01-12
categories: [Wifi, cybersecurity]
tags: [Wifi, cybersecurity]
---


# Setting Up a Raspberry Pi Zero 2W for Pentesting Wireless Network Attacks with Besside-NG and Sn1per

## Introduction

As organizations continue to expand their use of wireless networks, ensuring that these networks are secure becomes an increasingly vital concern. Wireless networks, by their very nature, are more susceptible to attack, often due to improper configurations, weak encryption, or poor monitoring practices. For penetration testers tasked with identifying vulnerabilities in a given network, effective and portable tools are key. The Raspberry Pi Zero 2W stands out as a compact, inexpensive, and capable platform that can be configured to execute a variety of offensive security tasks, including wireless network attacks and post-exploitation scanning.

In this guide, we will delve into the process of setting up a Raspberry Pi Zero 2W for pentesting wireless network penetration using Besside-NG and Sn1per. These tools will allow pentesters to automate wireless attacks, gather data, and perform post-exploitation activities once access to the network is gained. We will focus on theory, configuration, and workflow, while ensuring all tools and techniques are used in an authorized pentesting context. Special thanks to Daniel Dieterle for his contributions to the community and for providing the inspiration for this post.

## Why Use a Raspberry Pi Zero 2W for Wireless Network Pentesting?

The Raspberry Pi Zero 2W offers an ideal balance of size, cost, and functionality. It's equipped with a quad-core CPU, built-in Wi-Fi, and enough processing power to handle tasks such as passive network sniffing, attacking WPA2 encryption, and scanning network vulnerabilities. This low-cost device is easily concealable, which makes it particularly useful for penetration testers who need to operate covertly. Furthermore, the Pi Zero 2W’s compact nature means it’s highly portable—an ideal attribute for professionals who need to quickly deploy and retrieve tools without attracting attention.

Another advantage of using the Raspberry Pi Zero 2W is its flexibility. It supports a wide range of Linux-based penetration testing tools, including Besside-NG and Sn1per, which are both powerful components of a pentester's toolkit.

## Overview of Key Tools

### Besside-NG: Automating Wireless Attacks

Besside-NG is a tool developed to automate wireless network attacks, primarily focusing on capturing WPA and WPA2 handshakes. A handshake is a cryptographic exchange that occurs when a device connects to a secured wireless network. These handshakes contain the information needed to crack the WPA or WPA2 password offline using brute force or dictionary attacks.

Besside-NG works by passively monitoring the airwaves for nearby Wi-Fi networks. It doesn’t interfere with the network traffic but listens in on the wireless communication. When a device connects to a network, the tool automatically captures the handshake, saving it for later analysis. The key feature of Besside-NG is its automation: rather than manually starting and stopping packet captures, it continually operates in the background, capturing and storing handshakes from any WPA/WPA2-encrypted network in range.

Since Wi-Fi networks are constantly broadcasted and vulnerable to deauthentication attacks, Besside-NG can also passively collect data when devices connect to networks, automating the tedious work typically required to capture WPA handshakes.



![Image Description](https://i.imgur.com/pyekQUd.jpg)




### Sn1per: Post-Exploitation Network Scanning

Once access to a target network has been gained (such as through a cracked WPA2 password), the next step is to assess the network for vulnerabilities and further exploitation opportunities. This is where Sn1per comes in.

Sn1per is a comprehensive reconnaissance and vulnerability scanning tool designed to perform detailed network assessments. It automates several tasks critical to post-exploitation work, including scanning for open ports, identifying active services, discovering vulnerabilities, and fingerprinting systems. Once a network has been accessed, Sn1per can be used to enumerate services, scan for common vulnerabilities, and perform a thorough audit of the systems within the target network.

A key feature of Sn1per is its ability to handle network scanning with minimal input from the operator. It automates the process of identifying the most critical vulnerabilities, which is essential for pentesting exercises where time and efficiency are important. Furthermore, Sn1per can also generate detailed reports that help to document the findings for further analysis or remediation recommendations.

## Step-by-Step Process: Setting Up and Using the Tools

### 1. Preparing the Raspberry Pi Zero 2W

The first step in utilizing the Pi Zero 2W for penetration testing is to prepare the device by installing Raspberry Pi OS and configuring it for remote operation. This is essential for scenarios where the device will be used in the field without physical access to a monitor or keyboard. The process involves installing the OS onto an SD card and enabling SSH, which allows remote access.

Once SSH is enabled, the Pi can be connected to the target network via Wi-Fi. It's advisable to configure the Wi-Fi settings using a pre-configured `wpa_supplicant.conf` file, which allows the Pi to automatically connect to the desired network once powered on.

### 2. Installing Besside-NG

Once the Pi is online and accessible, the next step is to install Besside-NG. Besside-NG relies on packet capture and network interface manipulation, so it's important to install dependencies that will allow it to run effectively. This typically involves installing packages like `libpcap` (for packet capture) and ensuring that your Wi-Fi adapter is capable of being put into monitor mode—the mode that allows a network interface to passively listen to Wi-Fi traffic.

[Aircrack-ng GitHub Repository](https://github.com/aircrack-ng/aircrack-ng)


With Besside-NG installed, the tool will continuously monitor for nearby networks. When a client connects to a network, Besside-NG will passively capture the WPA handshake and save it. This data can then be used offline to attempt cracking the password using various methods like dictionary attacks or brute-forcing. It is important to note that the monitor mode of the Wi-Fi adapter is essential for Besside-NG to function correctly, as it allows the adapter to capture all traffic in the air without needing to be directly connected to a network.

### 3. Using Sn1per for Post-Exploitation Network Scanning

Once access to a network is gained (e.g., after cracking the WPA password), the next stage of the engagement involves scanning the network for vulnerabilities. This is where Sn1per is most effective. Sn1per performs a comprehensive vulnerability scan that helps assess the security posture of the network and systems within it.

Using Sn1per, the pentester can quickly identify which systems are online, which services they are running, and whether those services have known vulnerabilities. Sn1per automates the process of scanning, performing tasks such as:

- **Port scanning**: Identifying open ports on devices within the network.
- **Service enumeration**: Detecting the services running on open ports.
- **Vulnerability scanning**: Identifying vulnerabilities in the services and devices running on the network.

[Sn1per GitHub Repository](https://github.com/1N3/Sn1per "Visit Sn1per's GitHub repository")


Sn1per allows pentesters to quickly move from gaining initial access to performing deeper exploitation and reconnaissance. After scanning the target network, it generates a detailed report that outlines any vulnerabilities discovered, which can then be used to strategize further attacks or report the findings for mitigation.


![Image Description](https://i.imgur.com/vE8Tp2G.jpg)




## Ethical Considerations and Best Practices

While the tools and techniques discussed are powerful, it’s crucial to emphasize the importance of responsible pentesting and authorized testing. Penetration testing should always be conducted with explicit permission from the network owner or organization. Unauthorized access to networks, regardless of intent, is illegal and unethical.

Pentesters should operate within clearly defined rules of engagement that outline the scope and boundaries of the testing. This includes defining which systems and networks are in scope, what attack vectors are allowed, and what level of access is permissible.

A pentester's mission is to identify vulnerabilities before malicious actors do, allowing organizations to fix those weaknesses and improve their overall security posture.

## A Special Thanks to Daniel Dieterle

Special thanks to Daniel Dieterle for his innovative ideas and contributions to the cybersecurity community. His work has inspired and empowered penetration testers to continually enhance their methods and tools, including those discussed in this post.

## Conclusion

The Raspberry Pi Zero 2W is a versatile and powerful platform for wireless network penetration testing, combining portability, performance, and low cost. By pairing it with Besside-NG and Sn1per, pentesters can automate the process of capturing WPA handshakes, scanning networks, and identifying vulnerabilities—creating a streamlined and effective testing process.

Pentesters can use these tools to gain deep insights into network security, uncovering vulnerabilities, and ultimately improving the overall security posture of organizations. However, it is crucial that these activities are always performed within the boundaries of the law and ethical guidelines, ensuring that they are beneficial to both the pentesting team and the organization being tested.
