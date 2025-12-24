---
I first had to boot from the Proxmox ISO image, and once it booted, I started making configuration changes. I was using NAT networking via VMware, so I used the virtual IP address of my host computer as the gateway.
---
---

![1](./assets/image1.png)

---
Installing sudo here for root privileges.
---
---
  
![2](./assets/image2.png)

---
Adding a local user.
---
---

![3](./assets/image3.png)

---
Accessing Proxmox via the web. Also, I made an admin group in Proxmox to make it easier to delegate permissions.
---
---

![4](./assets/image4.png)
![5](./assets/image5.png)

---
Adding the local user to the admin group.
---
---

![6](./assets/image6.png)

---
Making an SSH folder, to store keys.
---
---

![7](./assets/image7.png)

---
Using the Secure Copy Protocol to move my host key to the Proxmox VM, so I can SSH into the Proxmox VM via my host.
---
---

![8](./assets/image8.png)

---
Adding a DMZ (Demilitarized Zone) VNet. This will be for the public facing VMs I will put in that subnet.
---
---

![9](./assets/image9.png)

---
Using the bridge device (vmbr0) to be able to connect VLANs.
---
---

![10](./assets/image10.png)

---
Adding an internal VNet. This will be for the VMs that are not public facing.
---
---

![11](./assets/image11.png)

---
Creating the first VM. It will be a 2019 version of Windows.
---
---

![12](./assets/image12.png)
![13](./assets/image13.png)
![14](./assets/image14.png)
![15](./assets/image15.png)
![16](./assets/image16.png)
![17](./assets/image17.png)

---
Making sure to use the VirtIO driver for better performance.
---
---

![18](./assets/image18.png)

---
Creating the second VM. This will be an OPNsense firewall.
---
---

![19](./assets/image19.png)
![20](./assets/image20.png)
![21](./assets/image21.png)
![22](./assets/image22.png)
![23](./assets/image23.png)
![24](./assets/image24.png)
![25](./assets/image25.png)

---
Adding paravirtualized network devices for both the VNets; that way, there will be higher throughput and lower latency as compared to an emulated NIC.
---
---

![26](./assets/image26.png)
![27](./assets/image27.png)

---
Accessing OPNsense via the web interface (via the 'wks' VM).
---
---

![29](./assets/image29.png)

---
Setting the DNS server to be my host (in the VMware NATwork).
---
---

![30](./assets/image30.png)

---
Setting IP address and gateway for the WAN interface of the firewall.
---
---

![31](./assets/image31.png)

---
Setting IP address for the LAN interface of the firewall.
---
---

![33](./assets/image33.png)

---
Setting IP address for the optional interface (the DMZ interface) of the firewall. 
---
---

![35](./assets/image35.png)
![36](./assets/image36.png)

---
Creating a firewall rule to allow IPv4 traffic outbound from the DMZ.
---
---

![37](./assets/image37.png)

---
Creating a firewall rule to reject IPv4 traffic outbound from the DMZ to the LAN. (IMPORTANT: Put the reject rule before the allow rule, so that the allow rule doesn't allow unwanted traffic to the LAN before it even sees the reject rule)
---
---

![39](./assets/image39.png)
![40](./assets/image40.png)
![41](./assets/image41.png)

---
Using the Linux container framework (LXC) to save some resources, as opposed to another VM. This container will be a web server. 
---
---

![42](./assets/image42.png)
![43](./assets/image43.png)
![44](./assets/image44.png)
![45](./assets/image45.png)
![46](./assets/image46.png)

---
Setting IP address and gateway; gateway must be DMZ interface of firewall.
---
---

![47](./assets/image47.png)

---
Adding a local user to the web server.
---
---

![49](./assets/image49.png)

---
Implementing the web server using NGINX. 
---
---

![50](./assets/image50.png)
![51](./assets/image51.png)
![52](./assets/image52.png)

---
Here, I am defining a port forward to allow users outside the network to access the web server. It is created on the WAN interface of the firewall, and maps all HTTP traffic to the web server's IP address. This way, by going to the WAN interface of the firewall via the web, it will show the web server page.
---
---

![53](./assets/image53.png)
![54](./assets/image54.png)
