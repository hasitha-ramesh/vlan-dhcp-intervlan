\# 🌐 VLAN + DHCP Inter-VLAN Routing Project



\## 📌 Description



This project demonstrates VLAN configuration, inter-VLAN communication, and automatic IP address assignment using \*\*DHCP\*\* in Cisco Packet Tracer.



The network is segmented using VLANs, and a router is configured with \*\*Router-on-a-Stick\*\* to enable communication between VLANs while also acting as a \*\*DHCP server\*\*.



\---



\## 🧩 Topology



\* 1 Switch (Cisco 2960)

\* 1 Router

\* 2 PCs

\* Trunk link between Switch and Router



\---



\## 🏷️ VLAN Configuration



| VLAN ID | Name | Device |

| ------- | ---- | ------ |

| 10      | IT   | PC0    |

| 20      | HR   | PC1    |



\---



\## 🌐 IP Addressing (DHCP)



| VLAN | Network Address | Default Gateway |

| ---- | --------------- | --------------- |

| 10   | 192.168.10.0/24 | 192.168.10.1    |

| 20   | 192.168.20.0/24 | 192.168.20.1    |



👉 IP addresses are assigned automatically using DHCP.



\---



\## ⚙️ Switch Configuration



```

enable

configure terminal



vlan 10

name IT



vlan 20

name HR



interface fa0/1

switchport mode access

switchport access vlan 10



interface fa0/2

switchport mode access

switchport access vlan 20



interface fa0/24

switchport mode trunk

```



\---



\## ⚙️ Router Configuration



```

enable

configure terminal



interface g0/0

no shutdown



interface g0/0.10

encapsulation dot1Q 10

ip address 192.168.10.1 255.255.255.0



interface g0/0.20

encapsulation dot1Q 20

ip address 192.168.20.1 255.255.255.0



ip dhcp excluded-address 192.168.10.1

ip dhcp excluded-address 192.168.20.1



ip dhcp pool VLAN10

network 192.168.10.0 255.255.255.0

default-router 192.168.10.1



ip dhcp pool VLAN20

network 192.168.20.0 255.255.255.0

default-router 192.168.20.1

```



\---



\## 🖥️ PC Configuration



\* Set both PCs to \*\*DHCP mode\*\*

\* IP addresses will be assigned automatically



\---



\## 🔌 Trunk Explanation



A trunk port allows multiple VLANs to pass through a single link between devices (Switch ↔ Router) using \*\*802.1Q tagging\*\*.



\---



\## 🧪 Test Results



\### 🔹 IP Assignment (DHCP)



```

PC> ipconfig

IP Address: 192.168.10.x

Default Gateway: 192.168.10.1

```



\### 🔹 Inter-VLAN Ping Test



```

PC0> ping 192.168.20.x



Reply from 192.168.20.x: bytes=32 time<1ms TTL=128

```



✔ Successful communication between VLANs



\---



\## 📸 Screenshots



\### 🔹 Network Topology



!\[Topology](images/topology.png)



\### 🔹 DHCP IP Assignment



!\[DHCP](images/dhcp.png)



\### 🔹 Ping Success



!\[Ping](images/ping-success.png)



\---



\## 📁 Project Files



\* vlan-dhcp-intervlan.pkt

\* README.md

\* /images (screenshots)



\---



\## 🚀 Key Features



\* VLAN segmentation

\* Trunk configuration

\* Inter-VLAN routing

\* DHCP automatic IP assignment



\---



\## 🧠 Learning Outcomes



\* Configure VLANs on a switch

\* Set up trunk links

\* Implement Router-on-a-Stick

\* Configure DHCP on a router

\* Verify connectivity using ping



\---



\## 👨‍💻 Author



Hasitha Ramesh

GitHub: https://github.com/hasitha-ramesh



