Topology, Lab S01:

This document explains the topology of the lab, developed for the first class of the NIS 2026/2027 course.
The lab consists of two Virtual Machines (VMs), a Gateway and a Server, as well as three network segments. Virtual Machine Manager was used to create the lab and the host system is a Ubuntu 24.04 system. The VMs are configured as follows:
Gateway - 1GB RAM, 1 CPU core and 20GB of disk space
Server - 4GB RAm, 2 CPU cores and 20GB of disk space
The core idea of lab is that the server is isolated from the outside world and all of it's data communication is facilited through the gateway, which can monitor and regulate all the server's traffic. To enable such a configuration, these two virtual machines are connected by three internal network segments, LAN1 and 2 and a WAN.
The network segments are:
LAN1 - The internal network, connecting the gateway and the server. This network has the address 67.67.67.0/24 (254 Hosts) and DHCP has been disabled.
LAN2 - Reserved for future use, this network segment is connceted only to the gateway. This network has the address 69.69.69.0/24 (254 Hosts) and DHCP has also been disabled.
WAN - The external network segment, connecting the gateway to the host machine and providing it with access to the outside world.
The whole idea is that all the data packets that the server generates and receives, are passed through the gateway, which can act as a type of filter and can also block other of types of trafic, like virus attacks and other malicious content. Also it can act as a fire wall, preventing attacks on the server system. 
The LAN and the WAN segments are generated within the virtual machine manager and are configured as follows:
LAN1: Network address - 67.67.67.0/24, host range 67.67.67.1-255. DHCP is disabled. The network is isolated
LAN2: Network address - 69.69.69.0/24, host range 69.69.69.1-255. DHCP is disabled. The network is isolated
WAN: Network address - 192.168.122.0/24, host range 192.168.122.2 - 192.168.122.254. DHCP is enabled, DHCP server address - 192.168.122.1. Forwarding - NAT.

The Gateway has three configured virtual NIC's (Network interface Card), connected to each of the network segments:
-enp1s0 - Connected to the WAN network segment, configured as a Bridge. This allows it to get an IP address from the host machine - 192.168.122.196/24
-enp7s0 - Connected to the LAN1 network segment. This virtual NIC has a manually configured static IP address - 67.67.67.1/24, no default gateway is set.
-enp8s0 - Connected to the LAN2 network segment. This virtual NIC has a manually configured static IP address - 69.69.69.1/24, no default gateway is set.

The Server has only one configured virtual NIC and it's connected to the LAN1 segment
-enp1s0 - Connected to the LAN1 segment. This virtual NIC also has a manually configured static IP address - 67.67.67.2/24, and the default gateway is set to the address of the Gateway VM in this network segment - 67.67.67.1.

The "interfaces" config file has been used on both VMs for configuring the NICs. This file is located in /etc/network and holds the settings for the network interfaces of each machine. Using this file, each interface on each machine had it's ip address set. Each interafce was also configured to start up automatically on boot and also DHCP was not enabled (exept on enp1s0 on the Gateway VM, as this interface expects it's address to come from the host machine), as to not confuse the machine's settings.

Finally, to comleate the task, ip forwarding should be enabled on the Gateway VM. This was accomplished by creating a new config file in /etc called sysctl.conf. On some instalations this file already exists but it's empty. However my instalation did not come with it already generated, so it was necessary for me to create it. The only command needed to configure this feature is net.ipv4.ip_forward=1. To check if ip forwarding works we can call the sudo sysctl -p and see if it returns a 1.

