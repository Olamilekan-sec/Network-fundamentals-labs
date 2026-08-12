# NAT and PAT Configuration Commands

## Network Addressing

### R1
- G0/0/0: 192.168.1.1 /24
- G0/0/1: 209.165.200.225 /30

### R2
- G0/0/0: 10.10.10.1 /24
- G0/0/1: 209.165.200.226 /30

### Internal Devices
- PC1: 192.168.1.10 /24
- PC2: 192.168.1.20 /24
- Server: 10.10.10.10 /24

## 1. Configure R1 Inside Interface

```cisco
interface g0/0/0
ip address 192.168.1.1 255.255.255.0
ip nat inside
no shutdown
```

## 2. Configure R1 Outside Interface

```cisco
interface g0/0/1
ip address 209.165.200.225 255.255.255.252
ip nat outside
no shutdown
```

## 3. Configure Static NAT

```cisco
ip nat inside source static 192.168.1.10 209.165.200.230
```

## 4. Configure PAT

```cisco
access-list 1 permit 192.168.1.0 0.0.0.255

ip nat inside source list 1 interface g0/0/1 overload
```

## 5. Verify NAT

```cisco
show ip nat translations
show ip nat statistics
```

## 6. Test Connectivity

```cisco
ping 10.10.10.10
```

## Skills Demonstrated

- Static NAT
- Port Address Translation (PAT)
- Access Control Lists
- IP addressing
- Router interface configuration
- NAT verification
- Network troubleshooting
