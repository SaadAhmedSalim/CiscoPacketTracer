# CiscoPacketTracer
All Cisco Project will be uploaded here with description


# The Process
### **_Select three 1941 router, 2 switch-pt, 1 DHCP server, 1 DNS server and 3 PC._**

## For router setup:

Module :

We have to add HWIC-2T for the serial port. **_usually they don't have a port._** We have to click **on** the port status on always.

I am showing **router 2** of my picture you will have to add others. My network address is 192.168.16.0

       GigabitEthernet0/0 -> on

       Ip config: 192.168.16.1 (for the switch)

       Subnet mask: 255.255.255.0

       GigabitEthernet0/1 -> off (as no switch)

       Serialport0/0-> on

       ip conf: 192.168.100.1 (path is router 2 to router 1)

       subnet mask: 255.255.255.252

       clock rate : 2000000

       Serialport0/1-> on

       ip conf: 12.0.0.1 (path is router 2 to router 3)

       subnet mask: 255.255.255.252

       clock rate : 2000000


## RIP settings :

      network address :

      12.0.0.0

      192.168.16.0
      
      192.168.100.0

**_reason is you have to add those path which will go through this router. My addresses are these so I added them into it._**

**As I use DHCP server so all my PCs have dynamic address. But I have to know the DHCP address to succeed this operation. So,  go to any router, select attributes, it will show a command prompt, write**  

        ip helper-address 192.168.16.10

that Ip address is mine so put yours. So routers setup is completed. No matter how many router in your project, follow this instructions and keep track the serial port because it is important which path you have selected. Other important thing is you have to write those path addresses in your RIP configuration.



## For DHCP setup:

      select Desktop option

      select ip configuration

      select static
 
      ip address: 192.168.16.10 (any address in your 192.168.16.0)

      subnet mask: 255.255.255.0

      Default gateway: 192.168.16.1 (always have to the routers ip address)

      DNS server: 20.16.0.10 (if you don't have a DNS just ignore it)

I am using my DNS server address.Put yours.

          Then go the Services,

          select DHCP

          service-> on

There is two types of Pool. One is default and other is customed. As we have three path so our services will be ensured three pools.

      Pool Name: pool192 (it's easy to remember which network you are pooling so pick any name)

      Default gateway: 192.168.16.1 (Mine was router 2 so this is my router address)

Note: Strictly use the routers ip address otherwise it won't work. 

      DNS server : 20.16.0.10 (Mine DNS, put yours if you have)
 
      Start Ip : 192.168.16.11 (You can start 192.168.16.2)

Note: Don't start from 192.168.16.1 because that's our default gateway. Of course subnet mask must be similar to routers mask. Otherwise, it won;t work.

      Subnet mask: 255.255.255.0

      Maximum number of Users: 30 ( depends on you )

Complete others network addresses in your pool. then 
          select serverPool

_which was default, we have to modified it._

          default gateway: 0.0.0.0
          DNS server: 20.16.0.10
          start Ip: 0.0.0.0
          Subnet: 0.0.0.0

**Note: Remember this method, otherwise it won't work.**


## For DNS server:

      select Desktop

      select ip configuration

      select static

      ip address: 20.16.0.10 (put yours)

      subnet mask: 255.255.255.0

      default gateway: 20.16.0.1

**It was router 3 ip address make sure you put yours correctly.**

      DNS: 0.0.0.0

            then go to Services,

            select DNS

      DNS service-> on

                resource records name : www.localhost.com

                Type: A record

                Address: 192.168.16.10

               select add

**Note: Address depends on you so put any name. So question is how can I detect my DNS is working or not? Solution is in PCs setup.**

Your DNS server is created.

### PCs Setup:

Select any pc, I am selecting PC 2.

Go to Desktop then select ip configuration.

      select DHCP

_**It will give you addresses which you programmed in DHCP. Sometimes it delays and shows DHCP fails. Don't worry, again select DHCP it will show successful.**_

### For DNS checking:

      go to Desktop

      select Web browser

put your address name in URL.

      it will show Cisco Packet Tracer page.

So, all setup is completed.

**Wish you a good luck in your project.**

If you feel any inquiry,

Feel free to contact me.

Email: saad.salim@northsouth.edu

Phone: +8801521215397

Linkedin: https://www.linkedin.com/in/saad-salim-a566b9160/






