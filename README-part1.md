I first had to boot from the Proxmox ISO image, and once it booted, I started making configuration changes. I was using NAT networking via VMware, so I used the virtual IP address of my host computer as the gateway.
---

![1](./assets/image1.png)

Installing sudo here for root privileges.
---
  
![2](./assets/image2.png)

Adding a local user.
---

![3](./assets/image3.png)

Accessing Proxmox via the web. Also, I made an admin group in Proxmox to make it easier to delegate permissions.
---

![4](./assets/image4.png)
![5](./assets/image5.png)

Adding the local user to the admin group.
---

![6](./assets/image6.png)

Making an ssh directory, to store keys.
---

![7](./assets/image7.png)

Using the Secure Copy Protocol to move my host key to the Proxmox VM, so I can SSH into the Proxmox VM via my host.
---

![8](./assets/image8.png)

Adding a DMZ (Demilitarized Zone) VLAN. This will be for the public facing VMs I will put in that subnet.
---

![9](./assets/image9.png)
![10](./assets/image10.png)

Adding an internal VLAN. This will be for the VMs that are not public facing.
---

![11](./assets/image11.png)

12
---

![12](./assets/image12.png)

13
---

![13](./assets/image13.png)

14
---

![14](./assets/image14.png)

15
---

![15](./assets/image15.png)

16
---

![16](./assets/image16.png)

17
---

![17](./assets/image17.png)

18
---

![18](./assets/image18.png)

19
---

![19](./assets/image19.png)

20
---

![20](./assets/image20.png)

21
---

![21](./assets/image21.png)

22
---

![22](./assets/image22.png)

23
---

![23](./assets/image23.png)

24
---

![24](./assets/image24.png)

25
---

![25](./assets/image25.png)

26
---

![26](./assets/image26.png)

27
---

![27](./assets/image27.png)

28
---

![28](./assets/image28.png)

29
---

![29](./assets/image29.png)

30
---

![30](./assets/image30.png)

31
---

![31](./assets/image31.png)

32
---

![32](./assets/image32.png)

33
---

![33](./assets/image33.png)

34
---

![34](./assets/image34.png)

35
---

![35](./assets/image35.png)

36
---

![36](./assets/image36.png)

37
---

![37](./assets/image37.png)

38
---

![38](./assets/image38.png)

39
---

![39](./assets/image39.png)

40
---

![40](./assets/image40.png)

41
---

![41](./assets/image41.png)

42
---

![42](./assets/image42.png)

43
---

![43](./assets/image43.png)

44
---

![44](./assets/image44.png)

45
---

![45](./assets/image45.png)

46
---

![46](./assets/image46.png)

47
---

![47](./assets/image47.png)

48
---

![48](./assets/image48.png)

49
---

![49](./assets/image49.png)

50
---

![50](./assets/image50.png)

51
---

![51](./assets/image51.png)

52
---

![52](./assets/image52.png)

53
---

![53](./assets/image53.png)

54
---

![54](./assets/image54.png)
