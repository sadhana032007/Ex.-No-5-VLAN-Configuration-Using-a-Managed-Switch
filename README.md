## Ex. No: 5  VLAN Configuration Using a Managed Switch
Date: 28/10/2026
________________________________________
# Objective
To configure Virtual Local Area Networks (VLANs) on a managed switch and verify that hosts within the same VLAN can communicate while others cannot.
________________________________________
# Apparatus/Tools Required
•	Cisco Packet Tracer<br>
•	1 Managed Switch (e.g., 2960)<br>
•	4 PCs<br>
•	Straight-through Ethernet cables<br>
________________________________________
# Network Topology Diagram
Description:<br>
•	PC0 and PC1 are assigned to VLAN 10.<br>
•	PC2 and PC3 are assigned to VLAN 20.<br>
•	All PCs are connected to different ports on the same switch.<br>
(Insert screenshot of your Packet Tracer setup here)<br>
________________________________________
# IP Addressing Table
Device	VLAN	IP Address	Subnet Mask	Port<br>
PC0	10	192.168.10.1	255.255.255.0	FastEthernet0/1<br>
PC1	10	192.168.10.2	255.255.255.0	FastEthernet0/2<br>
PC2	20	192.168.20.1	255.255.255.0	FastEthernet0/3<br>
PC3	20	192.168.20.2	255.255.255.0	FastEthernet0/4<br>
________________________________________
# Procedure
1.	Open Cisco Packet Tracer and add 4 PCs and 1 Switch.<br>
2.	Connect PC0–PC3 to switch ports FastEthernet0/1 to FastEthernet0/4 respectively.<br>
3.	Assign static IP addresses to each PC as per the IP table.<br>
4.	Enter the Switch CLI and create two VLANs:<br>
o	VLAN 10 for PC0 and PC1<br>
o	VLAN 20 for PC2 and PC3<br>
5.	Assign the respective switch ports to their VLANs.<br>
6.	Use the ping command from PC0 to PC1 (should succeed).<br>
7.	Try pinging from PC0 to PC2 (should fail — different VLANs).<br>
________________________________________
# Commands Used (Switch CLI)
bash<br>
CopyEdit<br>
Switch> enable<br>
Switch# configure terminal<br>

Switch(config)# vlan 10<br>
Switch(config-vlan)# name STAFF<br>
Switch(config-vlan)# exit<br>

Switch(config)# vlan 20<br>
Switch(config-vlan)# name STUDENTS<br>
Switch(config-vlan)# exit<br>

Switch(config)# interface range fastethernet0/1 - 2<br>
Switch(config-if-range)# switchport mode access<br>
Switch(config-if-range)# switchport access vlan 10<br>
Switch(config-if-range)# exit<br>

Switch(config)# interface range fastethernet0/3 - 4<br>
Switch(config-if-range)# switchport mode access<br>
Switch(config-if-range)# switchport access vlan 20<br>
Switch(config-if-range)# exit<br>
________________________________________
# Output (Screenshots)
•	VLAN configuration on switch<br>
<img width="632" height="398" alt="Screenshot 2026-10-28 174654" src="https://github.com/user-attachments/assets/c08bb81a-5dc4-4bbc-91ce-88e5cdfae95f" />

•	PC IP settings<br>
<img width="640" height="376" alt="Screenshot 2026-10-28 174559" src="https://github.com/user-attachments/assets/4c2f83f4-7ef1-46b3-bbca-fb50db319b09" />

•	Successful ping between PCs in the same VLAN<br>
<img width="637" height="376" alt="Screenshot 2026-10-28 174523" src="https://github.com/user-attachments/assets/06d6f7c7-507c-4932-86ee-053f5a77b5bc" />
<img width="637" height="338" alt="Screenshot 2026-10-28 174543" src="https://github.com/user-attachments/assets/af48a1f7-8796-4e92-bc71-aa97d441655e" />


•	Failed ping between PCs in different VLANs<br>
<img width="640" height="376" alt="image" src="https://github.com/user-attachments/assets/404baed7-1b81-4097-b0a6-2e01dcf9d5f0" />

________________________________________
# Result
Successfully created and configured VLANs on a managed switch. Verified that only PCs within the same VLAN could communicate with each other.

