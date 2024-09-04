## Setting up Virtual Networks:

In order to adhere to the ranges provided for subnets, I used the following information:

### IP Ranges Given:
- **VNet 1**: 10.10.10.0/24
- **VNet 2**: 10.20.20.0/24

Each `/24` subnet provides 256 IP addresses, ranging from `.0` to `.255`. However, certain IP addresses are reserved and cannot be used:

1. **Network Address**: The first IP address (e.g., `10.10.10.0`).
2. **Broadcast Address**: The last IP address (e.g., `10.10.10.255`).
3. **Azure Reserved Addresses**: The first three IP addresses after the network address (e.g., `10.10.10.1`, `10.10.10.2`, and `10.10.10.3`).

### Breakdown for VNet 1 (10.10.10.0/24):

#### Subnet 1:
- **Subnet Range**: Let's assume you need a subnet with 128 addresses (e.g., `/25`).
  - **Subnet Address Range**: `10.10.10.0/25`
  - **Total IPs**: 128 (from `10.10.10.0` to `10.10.10.127`)
  - **Usable IPs**: `10.10.10.4` to `10.10.10.126` (the first 3 and last 1 IPs are reserved)

#### Subnet 2:
- **Subnet Range**: Let's assign the remaining IP range in VNet 1 to Subnet 2 (also `/25`).
  - **Subnet Address Range**: `10.10.10.128/25`
  - **Total IPs**: 128 (from `10.10.10.128` to `10.10.10.255`)
  - **Usable IPs**: `10.10.10.132` to `10.10.10.254` (the first 3 and last 1 IPs are reserved)

### Breakdown for VNet 2 (10.20.20.0/24):

#### Subnet 1:
- **Subnet Range**: Similarly, let's divide VNet 2 into two subnets with 128 addresses each.
  - **Subnet Address Range**: `10.20.20.0/25`
  - **Total IPs**: 128 (from `10.20.20.0` to `10.20.20.127`)
  - **Usable IPs**: `10.20.20.4` to `10.20.20.126` (the first 3 and last 1 IPs are reserved)

#### Subnet 2:
- **Subnet Range**: The remaining IP range in VNet 2 can be allocated to Subnet 2.
  - **Subnet Address Range**: `10.20.20.128/25`
  - **Total IPs**: 128 (from `10.20.20.128` to `10.20.20.255`)
  - **Usable IPs**: `10.20.20.132` to `10.20.20.254` (the first 3 and last 1 IPs are reserved)

### Summary:

- **VNet 1: 10.10.10.0/24**
  - **Subnet 1: 10.10.10.0/25** 
    - Usable IPs: `10.10.10.4` to `10.10.10.126`
  - **Subnet 2: 10.10.10.128/25** 
    - Usable IPs: `10.10.10.132` to `10.10.10.254`

- **VNet 2: 10.20.20.0/24**
  - **Subnet 1: 10.20.20.0/25** 
    - Usable IPs: `10.20.20.4` to `10.20.20.126`
  - **Subnet 2: 10.20.20.128/25** 
    - Usable IPs: `10.20.20.132` to `10.20.20.254`

This breakdown ensures that each subnet has an adequate number of IP addresses and adheres to Azure's reserved address requirements.
