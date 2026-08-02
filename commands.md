# Cisco IOS commands
## create VLANs
""" bash
vlan 10
name Sales
vlan 20
name HR
"""
## Assign ports
"""bash
interface f0/1
switchport mode access 
switchport access vlan 10

interface f0/2
switchport mode access
switchport access vlan 20
"""
## Configure Trunk
"""bash
interface f0/24
switchport mode trunk
"""
## Configure Router Subinterfaces
"""bash
interface g0/0.10
encapsulation dot1Q 10
ip address 192.168.10.1 255.255.255.0

interface g0/0.20
encapsulation dot1Q 20
ip address 192.168.20.1 255.255.255.0
## configure port security
"""bash 
switchport port-security
switchport port-security maximum 1
switchport port-security violation restrict
switchport port-security mac-address sticky
"""
