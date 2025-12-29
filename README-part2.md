---
Creating the initial domain controller.
---
---

![55](./assets/image55.png)
![56](./assets/image56.png)
![57](./assets/image57.png)
![58](./assets/image58.png)
![59](./assets/image59.png)
![60](./assets/image60.png)
![61](./assets/image61.png)

---
Installing Windows, and using the Desktop Experience for the server.
---
---

![62](./assets/image62.png)
![63](./assets/image63.png)
![64](./assets/image64.png)
![65](./assets/image65.png)

---
Setting static IP address and the gateway.
---
---

![66](./assets/image66.png)

---
Bringing up the domain.
---
---

![68](./assets/image68.png)
![69](./assets/image69.png)
![70](./assets/image70.png)
![71](./assets/image71.png)
![72](./assets/image72.png)
![73](./assets/image73.png)

---
Going through AD configuration settings. The forest represents the entire AD environment.
---
---

![74](./assets/image74.png)
![75](./assets/image75.png)
![76](./assets/image76.png)

---
Since this is a domain controller now, the way to find users and groups is through AD. Here, I am adding a non-admin user account.
---
---

![77](./assets/image77.png)
![78](./assets/image78.png)

---
Creating a specific admin account for the same user. This way, it is easier to see who is doing what, as opposed to users using the general domain admin account when admin rights are needed.
---
---

![81](./assets/image81.png)

---
To make the admin account have administrative privileges, go to the "Member Of" tab in the properties of that account. Then, add the user to the "Domain Admins" and "Enterprise Admins" groups.
---
---

![84](./assets/image84.png)
![85](./assets/image85.png)

---
Right now, there is a forward lookup zone (mapping hostname to IP address), but no reverse lookup zone (mapping IP address to hostname). I am adding it here through the "DNS" AD app (Storing the zone in AD so that it can replicate to the second domain controller that I am going to set up).
---
---

![86](./assets/image86.png)

---
There is only one domain in the forest, so all of these options work the same.
---
---

![87](./assets/image87.png)

---
Choosing an IPv4 Reverse Lookup Zone.
---
---

![88](./assets/image88.png)

---
Entering in the network ID for the subnet (/24 mask, so no need to enter in anything for the fourth octet).
---
---

![89](./assets/image89.png)

---
Allowing only computers on the domain to update DNS records.
---
---

![90](./assets/image90.png)

---
I created reverse lookup zones for the DMZ and WAN subnets as well.
---
---

![91](./assets/image91.png)

---
Creating the secondary domain controller, for failover purposes.
---
---

![92](./assets/image92.png)
![93](./assets/image93.png)
![94](./assets/image94.png)
![95](./assets/image95.png)
![96](./assets/image96.png)
![97](./assets/image97.png)
![98](./assets/image98.png)

---
Setting hostname for the second domain controller.
---
---

![100](./assets/image100.png)

---
Setting static IP address and DNS server (dc1) for dc2.
---
---

![102](./assets/image102.png)

---
Adding dc2 to the domain.
---
---

![103](./assets/image103.png)

---
Adding dc2 to the existing domain.
---
---

![105](./assets/image105.png)
![106](./assets/image106.png)

---
Since both domain controllers will function as DNS servers, they can use the localhost IP (themselves) and the other domain controller's IP as the DNS server addresses.
---
---

![107](./assets/image107.png)

---
After changing the firewall's DNS servers to the domain controllers, the "wks" VM shows them as the DNS servers.
---
---

![110](./assets/image110.png)

---
Joining "wks" to the domain.
---
---

![111](./assets/image111.png)

---
Back on the domain controller, I am creating two forward DNS lookups (and reverse lookups; "PTR record") for both the web server and the gateway (firewall).
---
---

![112](./assets/image112.png)
![113](./assets/image113.png)
![114](./assets/image114.png)

---
Adding a member server (not a domain controller).
---
---

![115](./assets/image115.png)
![116](./assets/image116.png)
![117](./assets/image117.png)
![118](./assets/image118.png)
![119](./assets/image119.png)
![120](./assets/image120.png)
![121](./assets/image121.png)

---
Setting static IP, DNS servers, and adding "srv" to the domain.
---
---

![122](./assets/image122.png)
![123](./assets/image123.png)

---
Creating a Windows Server Core VM. This VM doesn't have a GUI; everything is done via a CLI.
---
---

![124](./assets/image124.png)
![125](./assets/image125.png)
![126](./assets/image126.png)
![127](./assets/image127.png)
![128](./assets/image128.png)
![129](./assets/image129.png)
![130](./assets/image130.png)

---
131
---
---

![131](./assets/image131.png)

---
132
---
---

![132](./assets/image132.png)

---
133
---
---

![133](./assets/image133.png)

---
134
---
---

![134](./assets/image134.png)

---
135
---
---

![135](./assets/image135.png)

---
136
---
---

![136](./assets/image136.png)

---
137
---
---

![137](./assets/image137.png)
