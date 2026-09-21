#Topology, Lab S01
This document explains the topology of the lab, developed for the first class of the NIS 2026/2027 course.
The lab consists of two Virtual Machines (VMs), a Gateway and a Server, as well as three network segments. The VMs are configured as follows:
Gateway - 1GB RAM, 1 CPU core and 20GB of disk space
Server - 4GB RAm, 2 CPU cores and 20GB of disk space
The core idea of lab is that the server is isolated from the outside world and all of it's data communication is facilited
These two virtual machines are connected by three internal network segments, LAN1 and 2 and a WAN.
The network segments are:
LAN1 - The internal network, connecting the gateway and the serveer.
LAN2 - Reserved for future use, this network segment is connceted only to the gateway. 
WAN - The external network segment, connecting the gateway to the host machine and providing it with access to the outside world.
The whole idea is that all the data packets that the server generates, are passed thru the gateway, which can act as a type of filter and can also block other of types of trafic, like virus attacks and other malicious content. Also it can act as a fire wall, preventing attacks on the server system. 
The LAN and the WAN segments are generated within the virtual machine manager for the VM's communication and acrutianls for the system;s operation. 
