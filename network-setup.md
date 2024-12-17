Router0 - 1941 Router
Switch0 - 2960-24TT Switch 
Switch1 - 2960-24TT Switch
Server0 - Server-PT / IP Address: 168.90.0.4
PC0 - PC-PT / IP Address: 168.90.0.3
PC1 - PC-PT / IP Address: 168.90.0.2
Laptop0 - Laptop-PT / IP Address: 168.90.0.5
Server1 - Server-PT / IP Address: 210.3.14.2
Server2 - Server-PT / IP Address: 210.3.14.3
PC2- PC-PT / IP Address: 210.3.14.4
PC3 - PC-PT / IP Address: 168.90.0.6
PC4 - PC-PT / IP Address: 210.3.14.5
---------------------------------------------------
---DHCP Steps---
1. Click on the router and go to CLI 
2. Type enable
        conf t  (This command enables us to configure the terminal).
3. Type int g0/0 (We specify which interface we want configure, in our case g0/0 refers to Switch0 interface).
4. Type ip address 168.90.0.1 255.255.0.0 (We assign the default IP address for that interface and the subnet mask).
5. Type no shutdown (This command enables an interface, it's activing it so the data can be transmitted).
6. Type ip dhcp pool switch0 (By typing this, we created a DHCP pool that's named switch0).
7. Type network 168.90.0.0 255.255.0.0 (We specify the network address and subnet mask. This tells the router to allocate IP addresses from 168.90.0.1 to 168.90.255.255).
8. Type default-router 168.90.0.1 (This command specifies the default gateway so the devices can communicate with other devices outside its local network.)
9. Type dns-server 8.8.8.8 (We specified the DNS server, which will resolve domain names into IP addresses).
10. Type exit (Exiting from DHCP pool configuration mode).
11. Type ip dhcp excluded-address 168.90.0.1 (This command excludes the router's IP address from the DHCP pool).
12. Type exit (Return from configuration mode to normal mode).
13. Type int g0/1 (Specify the Switch1 interface).
14. Type ip address 210.3.14.1 255.255.255.0 
15. Type no shutdown
16. Type ip dhcp pool switch1 (Create another DHCP pool named Switch1 that refers to the g0/1 interface).
17. Type network 210.3.14.0 255.255.255.0 (Range from 210.3.14.0 to 210.3.14.255).
18. Type default-router 210.3.14.1 
19. Type dns-server 8.8.8.8
20. Type exit
21. Type ip dhcp excluded-address 210.3.14.1
22. Type exit