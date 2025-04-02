<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

# Exploring Network Security Groups and Traffic Between Azure VMs

This guide shows you how to monitor network traffic flowing to and from Azure Virtual Machines using Wireshark, and how to control it with Network Security Groups.

## Tools and Environments

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Command-Line Tools
- Network Protocols (SSH, RDP, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

## Operating Systems

- Windows 10 (21H2)
- Ubuntu Server 20.04

## High-Level Steps

- Step 1: Set up two VMs (one Windows, one Linux) on the same network
- Step 2: Install Wireshark and examine ICMP, SSH, RDP, DHCP, and DNS traffic
- Step 3: Set up a Network Security Group firewall

## Lab Prerequisites
<p>
 <img width="944" alt="image" src="https://github.com/user-attachments/assets/dab2f04e-b9c4-48aa-82c3-ad2cd3a89ba7" />
<img width="849" alt="image" src="https://github.com/user-attachments/assets/af763d83-8846-435d-bafa-280312109acf" />
</p>

- Both VMs must be in the same resource group
- Both VMs must share the same virtual network
- Note: Use RDP to connect to Windows, SSH for Linux

## Steps and Observations

<p>
<img width="918" alt="image" src="https://github.com/user-attachments/assets/4fed5d3f-ed49-4cad-8691-ac2bb71d7c78" />
<img width="847" alt="image" src="https://github.com/user-attachments/assets/b6a83238-afee-41f0-9fc9-ee104cb7abf1" />
<img width="948" alt="image" src="https://github.com/user-attachments/assets/d67d6dd3-4014-4750-881d-68879e6fb698" />
</p>

- First, download Wireshark for Windows from Wireshark.org, keeping all default settings during installation
- Open Wireshark on the Windows VM and select the Ethernet interface
- Wireshark will start capturing traffic - use the search bar to filter for specific protocols like ICMP, DNS, DHCP, etc.

<p>
<img width="958" alt="image" src="https://github.com/user-attachments/assets/153285ed-ff0b-4f7a-805c-eb6945fd59ad" />
<img width="945" alt="image" src="https://github.com/user-attachments/assets/e284f2f5-1aa7-4a92-99dd-6a6e793513d5" />
<img width="959" alt="image" src="https://github.com/user-attachments/assets/47c68b2e-93ab-4def-927e-a92b0f8d727a" />
</p>

- Filter for ICMP in Wireshark - no traffic will show up yet
- Get the Linux VM's private IP, then ping it from the Windows VM - you'll see ICMP request and reply packets
- Try pinging a website too - a "0% loss" response confirms the connection

<p>
<img width="946" alt="image" src="https://github.com/user-attachments/assets/d7ad0903-5bc2-44dd-b85d-bd3746dbd386" />
<img width="932" alt="image" src="https://github.com/user-attachments/assets/51b12f83-0d82-4e42-ab18-69507e881edc" />
<img width="928" alt="image" src="https://github.com/user-attachments/assets/61619c52-3452-4ed6-ad1d-b92cc2f9ada0" />
<img width="694" alt="image" src="https://github.com/user-attachments/assets/741542ef-6df1-4093-98b9-12d6100e82e3" />
</p>

- You can observe other protocols too, like SSH, DHCP, DNS, and RDP, as shown in the screenshots
- For SSH, connect to the Linux VM with: `ssh username@privateipaddress`
- RDP traffic appears continuously since the remote desktop connection to Windows is active
</P>
<br />
