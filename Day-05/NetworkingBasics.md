### **IP Address**

An IP address (Internet Protocol address) is a unique identifier assigned to each device connected to a computer network that uses the Internet Protocol for communication. There are two standards for IP addresses: IPv4 and IPv6.

**IPv4 addresses** are 32 bits long, divided into four octets, separated by dots (e.g., 192.168.1.1). Due to the limited number of IPv4 addresses, IPv6 was introduced.

**IPv6 addresses** are 128 bits long, written in hexadecimal, and separated by colons (e.g., 2001:0db8:85a3:0000:0000:8a2e:0370:7334), significantly increasing the number of available addresses.

### **Subnetting**
Subnetting is the practice of dividing a network into two or more smaller networks. It allows for more efficient use of IP addresses and can improve network security and performance by isolating traffic. In subnetting, a network is divided using a subnet mask.

**Subnet Mask:** A subnet mask is used to specify which portion of an IP address is the network portion and which part is available for host devices. For instance, a subnet mask of 255.255.255.0 for an IPv4 address indicates that the first three octets are the network part, and the last octet is for individual host addresses within that network.

### **CIDR (Classless Inter-Domain Routing)**
CIDR was introduced as a method to slow the rate of exhaustion of IPv4 addresses and to make routing more efficient. It replaced the older system based on classes (A, B, C, and so on) with a more flexible system.

CIDR uses a notation system to indicate the subnet mask associated with an IP address, represented by a slash and a number (e.g., 192.168.1.0/24). This /24 notation indicates that the first 24 bits of the IP address are used to identify the unique network, leaving the remaining bits for host addresses within that network.

### **Example:**

Given below is the example of subnetting, focusing on dividing a network into smaller subnets to illustrate how this process works in practice.

### Scenario:
Imagine you have been given an IP address block of `192.168.10.0/24` for your organization's network. This notation means that you have 256 IP addresses available (from `192.168.10.0` to `192.168.10.255`), and you need to create 4 subnets to separate departments within your organization for better management and security.

### Understanding the `/24`:
The `/24` at the end of your IP address block (`192.168.10.0/24`) is your subnet mask in CIDR notation, indicating that the first 24 bits of the 32-bit IP address are used to identify the network portion, leaving the last 8 bits for host addresses within that network.

### Step 1: Determine Subnet Requirements
You want to create 4 subnets, which means you need to figure out how many bits you need to borrow from the host portion of your IP address to do so. The formula to calculate the number of subnets is \(2^n\), where \(n\) is the number of bits borrowed. In this case, \(2^n = 4\), so \(n = 2\). 

### Step 2: Calculate the New Subnet Mask
Since you're borrowing 2 bits, add these 2 bits to the original 24-bit subnet mask. Therefore, your new subnet mask is `/26` (`24 original bits + 2 borrowed bits = 26 bits for the network`).

This gives us a subnet mask of `255.255.255.192` in decimal notation, where:
- `255.255.255` corresponds to the first 24 bits (the original network portion),
- `.192` represents the next 2 bits for subnetting (11000000 in binary).

### Step 3: Determine Subnet Address Ranges
With a `/26` subnet mask, each subnet has \(2^{6}\) = 64 IP addresses because we have 6 bits left for host addresses (32 total bits - 26 bits for network and subnet = 6 bits for hosts).

The IP address ranges for the 4 subnets are as follows:
- **Subnet 1**: `192.168.10.0` to `192.168.10.63`
  - Usable IP addresses: `192.168.10.1` to `192.168.10.62`
  - Network address: `192.168.10.0`
  - Broadcast address: `192.168.10.63`
- **Subnet 2**: `192.168.10.64` to `192.168.10.127`
  - Usable IP addresses: `192.168.10.65` to `192.168.10.126`
  - Network address: `192.168.10.64`
  - Broadcast address: `192.168.10.127`
- **Subnet 3**: `192.168.10.128` to `192.168.10.191`
  - Usable IP addresses: `192.168.10.129` to `192.168.10.190`
  - Network address: `192.168.10.128`
  - Broadcast address: `192.168.10.191`
- **Subnet 4**: `192.168.10.192` to `192.168.10.255`
  - Usable IP addresses: `192.168.10.193` to `192.168.10.254`
  - Network address: `192.168.10.192`
  - Broadcast address: `192.168.10.255`

### Conclusion:
By subnetting the original `192.168.10.0/24` network into four `/26` subnets, we've effectively segmented the network into smaller, manageable parts, each supporting up to 62 devices (64 total addresses minus 1 for the network address and 1 for the broadcast address in each subnet). This setup enhances network management, security, and can help in reducing broadcast traffic within each subnet.
