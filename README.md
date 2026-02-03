# Subnetting-FLSM-
Subnetting using fixed length subnet mask

What is FLSM? (Definition)

FLSM (Fixed Length Subnet Mask) is a subnetting method where all subnets use the same subnet mask, regardless of how many hosts each network actually needs.

Key idea:

Subnet size is decided by the largest host requirement.

Every network gets equal-sized subnets

Simple to design, but causes IP address waste

In FLSM, simplicity is prioritized over efficiency.

<img width="1834" height="878" alt="image" src="https://github.com/user-attachments/assets/686934b3-3230-42a7-9295-a50813531012" />

Host requirement in our topology

From  diagram:

Network	Required Hosts
LAN A	62 hosts
LAN B	45 hosts
LAN C	14 hosts
LAN D	9 hosts

👉 Largest requirement = 62 hosts

So in FLSM, ALL subnets must support at least 62 hosts.

Choosing the Subnet Mask

To support 62 hosts, we need:

2⁶ − 2 = 62 hosts

So the subnet size is:

/26  →  255.255.255.192


Each subnet gives:

64 IPs

62 usable hosts

🔹 Subnetting 192.168.0.0/24 into 4 Equal Subnets (FLSM)

🔸 Subnet Breakdown

Subnet	Network Address	First Usable	Last Usable	Broadcast

LAN-A	192.168.0.0/26	192.168.0.1	192.168.0.62	192.168.0.63

LAN-B	192.168.0.64/26	192.168.0.65	192.168.0.126	192.168.0.127

LAN-C	192.168.0.128/26	192.168.0.129	192.168.0.190	192.168.0.191

LAN-D	192.168.0.192/26	192.168.0.193	192.168.0.254	192.168.0.255
<img width="1831" height="883" alt="image" src="https://github.com/user-attachments/assets/8e70960c-04a7-46fe-b512-e3aae901275c" />


🔹 IP Address Assignment Strategy 

✔️ First usable IP = PC
✔️ Last usable IP = Router interface

🔹 Device IP Assignments

🟧 LAN-A

assigning ip address and gateway to pc0

PC0 → 192.168.0.1 /26
<img width="1330" height="1098" alt="image" src="https://github.com/user-attachments/assets/94d30286-83c3-433a-949a-baf844f5b4f0" />

<img width="1385" height="1219" alt="Screenshot 2026-02-03 123537" src="https://github.com/user-attachments/assets/27add87e-6928-49a6-bb81-c22b9b78da3e" />


Router1 G0/0 → 192.168.0.62 /26
<img width="1312" height="521" alt="image" src="https://github.com/user-attachments/assets/ecee7007-80bd-493f-ac82-456d40ba3750" />



🟩 LAN-B

PC2 → 192.168.0.65 /26
<img width="1362" height="1155" alt="image" src="https://github.com/user-attachments/assets/283b0a26-cff0-49fc-8a60-780c9f0fb6f6" />
<img width="1330" height="1020" alt="image" src="https://github.com/user-attachments/assets/c376b389-bff0-4c8b-83be-6bd7e4b94d1b" />



Router2 G0/2 → 192.168.0.126 /26
<img width="2007" height="707" alt="image" src="https://github.com/user-attachments/assets/61762458-4324-4554-9d2b-c94d5ad9ea1e" />


🟨 LAN-C

PC1 → 192.168.0.129 /26
<img width="1341" height="985" alt="image" src="https://github.com/user-attachments/assets/ec1d641d-b0ab-4d3d-ae20-d3ea6dd6d585" />
<img width="1336" height="955" alt="image" src="https://github.com/user-attachments/assets/8a6e674c-48dc-4fb7-a5bf-8ee8612e188e" />


Router2 G0/1 → 192.168.0.190 /26

<img width="1662" height="366" alt="image" src="https://github.com/user-attachments/assets/d77b6fbf-f326-4a3d-b38e-957656f254ce" />



🟪 LAN-D (Router-to-Router)

Router1 G0/1 → 192.168.0.193 /26
<img width="1289" height="389" alt="image" src="https://github.com/user-attachments/assets/c6d9ee42-e33f-440c-b6a2-98dba4774ee9" />



Router2 G0/0 → 192.168.0.194 /26
<img width="1276" height="956" alt="image" src="https://github.com/user-attachments/assets/9a6bb49b-1906-4d79-813a-8ebb21d40085" />



🔹 Static Routing Configuration

On Router1

ip route 192.168.0.64 255.255.255.192 192.168.0.194

ip route 192.168.0.128 255.255.255.192 192.168.0.194

<img width="2550" height="1316" alt="image" src="https://github.com/user-attachments/assets/f02faf0e-501f-4bcf-8227-c3cb688b592c" />


On Router2

ip route 192.168.0.0 255.255.255.192 192.168.0.193
<img width="2145" height="1348" alt="image" src="https://github.com/user-attachments/assets/90636ac5-f5a1-4837-830a-17887cca38f9" />

Now we need to ping all the pc-1,2 from pc -0 to check the connectivity
<img width="2542" height="1685" alt="image" src="https://github.com/user-attachments/assets/5ab8bb90-b3c3-486c-9f26-30a2c1883e8b" />

🔹 Final Result

✅ All PCs can ping each other

✅ Equal subnet size using FLSM

✅ Clear demonstration of IPs simplicity




