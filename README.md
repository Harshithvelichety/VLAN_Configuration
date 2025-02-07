# VLAN_Configuration
# VLAN Configuration Project

## Overview
This project demonstrates VLAN configuration in a simple network topology using Cisco Packet Tracer. The network consists of multiple PCs connected to switches with VLAN segmentation. The objective is to configure VLANs to control network segmentation and ensure proper communication within VLAN groups.

## Network Topology
The topology consists of:
- **4 PCs** (PC0, PC1, PC2, PC3)
- **2 Switches** (Switch0, Switch1)
- **Trunk Connection** between Switch0 and Switch1

### VLAN Assignments
| VLAN ID | Description | Assigned Ports |
|---------|-------------|----------------|
| 10      | Sales       | PC0 (Fa0/1), PC2 (Fa0/1) |
| 20      | HR          | PC1 (Fa0/2), PC3 (Fa0/2) |
| 30     | Management  | Switch Management Interface |

## Configuration Steps
### 1. Configure VLANs on Switches
```bash
Switch(config)# vlan 10
Switch(config-vlan)# name Sales
Switch(config-vlan)# vlan 20
Switch(config-vlan)# name HR
Switch(config-vlan)# vlan 30
Switch(config-vlan)# name Management
```

### 2. Assign Ports to VLANs
```bash
Switch(config)# interface FastEthernet 0/1
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 10

Switch(config)# interface FastEthernet 0/2
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 20
```


### 3. Configure Trunk Ports
```bash
Switch(config)# interface FastEthernet 1/1
Switch(config-if)# switchport mode trunk
Switch(config-if)# switchport trunk allowed vlan 10,20
```

### 4. Verify VLAN Configuration
```bash
Switch# show vlan brief
Switch# show interfaces trunk
```

## Testing Connectivity
1. Use the `ping` command between PCs in the same VLAN to verify communication.
2. PCs in different VLANs should not communicate unless configured with inter-VLAN routing.

## Notes
- Ensure the trunk link allows required VLANs.

## Author
Harshith
