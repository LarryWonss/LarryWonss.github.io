# My first attempt with PVE running OpenWrt, Windows, Linux etc all in one mini PC



>  I used to use ESXi Server on my mini PC, I am now trying PVE due to:
>
> - PVE can show CPU, NICs temperature with a few settings;
> - The NICs order will not chaotic under PVE
>
> - PVE is base on Debian, and i am familiar with a few linux cammand



#### 1. Making a bootable USB flash drive

> First of all , we need to make a bootable USB flash drive with [BalenaEtcher](https://www.balena.io/etcher/) (please don't use rufus). Download the [PVE ISO](https://pve.proxmox.com/wiki/Downloads) from [PVE Downloads](https://pve.proxmox.com/wiki/Downloads) .

1. Open the BalenaEtcher after installation
   ![img](https://s2.loli.net/2022/06/02/mogT5OjpbRHyvAc.png)

2. Choose the right ISO image & USB Drive

   ![img](https://s2.loli.net/2022/06/02/HfkoZqzeTOpgXDb.png)

3. Click the Flash botton and waiting for being done.
   ![img](https://s2.loli.net/2022/06/02/WJm24lSUhAdEZ6M.png)

That's all, relly simply for making a bootable USB drive.

#### 2. Flash PVE into SSD with bootable USB drive

> We have made a bootable USB drive, then insert into the mini PC, and link to a keyboard and mouse before power on.

1. Power on the mini PC(*just plug in the power, it'll autostart*) , and press F12 or delete botton, choose the right source to start;
   ![img](https://s2.loli.net/2022/06/02/GjMN4ICiOgYy53P.jpg)

2. Agree with all the terms;
   ![img](https://s2.loli.net/2022/06/02/YuIZ5hpSxNe2R7k.jpg)

3. Choose the right target harddisk and next
   ![img](https://s2.loli.net/2022/06/02/AFt4DIpy1VzdNkC.jpg)

4. Setting your country , timezone and keyboard layout;
   ![img](https://s2.loli.net/2022/06/02/JIyAEUDv7qK9gXd.jpg)

5. Setting the password and email address for PVE server (please remember the password and email cann't be blank)
   ![img](https://s2.loli.net/2022/06/02/p5lhiK4oLjDYW1S.jpg)

6. Setting the details for the PVE Server:
   **Be careful: these information is important**

   - Management Interface: recommanded the first NIC (judge by the Mac address)
   - Hostname: i7-1165G7.iswott.com
   - IP address (CIDR): the login address for PVE server
   - Gateway: 192.168.1.2/24
   - DNS:192.168.1.1

   ![img](https://s2.loli.net/2022/06/02/XENcSY6v3gJt4bm.jpg)

7. Click Next, and it'll be install the PVE on harddisk automatically.
   ![img](https://s2.loli.net/2022/06/02/6ZpKkPeyu29WcS5.jpg)

After installation, the system will auto reboot. As far, the PVE virtual machine system is successfully installed. And

- Login address: [https:192.168.1.2:8006](https:192.168.1.2:8006) (must with https and 8006 port in the address)
- Login username: root
- Password: the password you set on step 5

Enjoy!