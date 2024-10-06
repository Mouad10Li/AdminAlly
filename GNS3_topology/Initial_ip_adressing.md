# IP Address Assignments for Routers

This document details the IP address configuration for each router in the network topology. Each router is assigned a unique IP address within the `192.168.122.0/24` subnet. The configuration commands activate the router interfaces and ensure connectivity between devices. The basic process includes assigning the IP address, enabling the interface, and saving the configuration.

### Command Explanation

- **`ip address X.X.X.X 255.255.255.0`**: Assigns a specific IP address to the router’s `g0/0` interface.
- **`no shutdown`**: Ensures the interface is activated, allowing it to communicate with other devices.
- **`write memory`**: Saves the changes permanently to the router’s memory.

### Router1 Configuration

- **IP Address**: `192.168.122.4 /24`

```bash
conf t
interface g0/0
 ip address 192.168.122.4 255.255.255.0
 no shutdown
exit
write memory
```

### Router2 Configuration

- **IP Address**: `192.168.122.2 /24`

```bash
conf t
interface g0/0
 ip address 192.168.122.2 255.255.255.0
 no shutdown
exit
write memory
```

### Router3 Configuration

- **IP Address**: `192.168.122.3 /24`

```bash
conf t
interface g0/0
 ip address 192.168.122.3 255.255.255.0
 no shutdown
exit
write memory
```

### Note

If you want the routers to have internet access, configure the `g0/0` interfaces to use DHCP instead of static IP addresses. Be aware that using DHCP will assign dynamic IPs, so you will need to update your hosts file with the new addresses.
