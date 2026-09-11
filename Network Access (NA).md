
<!-- Your monitor number = 41 -->


## IPv6 Subnetting


&nbsp;
---
&nbsp;


### IPv6 Address Compression Rules

~~~
!@cmd
ping fe80:000a:000b:000c:0000:0000:0000:a123
~~~

<br>

1. All leading zeroes are dropped

   :000a:  >   :a:
   
<br>

2. Consecutive group of zeroes become :: This happens only ONCE!  
   Other Consecutive Zeroes become :0:

   :0000:0000:0000:000a:0000:   >  ::a:0:
   
<br>

3. The most consecutive zeroes become ::

   :0000:0000:0000:000a:0000:0000:  >  ::a:0:0:

<br>

4. If the number of consecutive zeroes are the same, 
then the first group from left to right becomes :: 

   :0000:0000:0000:000a:0000:0000:0000:  > ::a:0:0:0:


&nbsp;
---
&nbsp;


### 🎯 Exercise 01: Compress IPv6 Addresses

1. 2001:0db8:0000:0000:0000:0000:0000:0000 /64

2. 0000:0000:0000:0000:0000:0000:0000:0000 /0
      
3. fe80:0000:0000:0000:000a:0000:0000:000f /10

4. fd00:0000:0000:3000:0000:0000:0000:0000 /64

5. 0000:0000:0000:0000:0000:0000:0000:0001 /128
     
6. ff00:0000:0000:beef:a00a:0aa0:0000:0000 /12


&nbsp;
---
&nbsp;


| Decimal | Binary   | Hexadecimal |
| ---     | ---      | ---         |
| 0       | 0 0 0 0  | 0           |
| 1       | 0 0 0 1  | 1           |
| 2       | 0 0 1 0  | 2           | 
| 3       | 0 0 1 1  | 3           |
| 4       | 0 1 0 0  | 4           |
| 5       | 0 1 0 1  | 5           |
| 6       | 0 1 1 0  | 6           |
| 7       | 0 1 1 1  | 7           |
| 8       | 1 0 0 0  | 8           |
| 9       | 1 0 0 1  | 9           |
| 10      | 1 0 1 0  | A           |
| 11      | 1 0 1 1  | B           |
| 12      | 1 1 0 0  | C           |
| 13      | 1 1 0 1  | D           |
| 14      | 1 1 1 0  | E           |
| 15      | 1 1 1 1  | F           |


&nbsp;
---
&nbsp;


| Prefix | Hextet | Hexadecimal | i   |
| ---    | ---    | ---         | --- |
| /32    |        |             |     |
| /41    |        |             |     |         
| /70    |        |             |     |
| /7     |        |             |     |
| /111   |        |             |     |
| /124   |        |             |     |


<br>
<br>

---
&nbsp;


### 🎯 Exercise 02: Subnet for 8 offices using the network address fd00:1::/64

<br>

### CAI Method

<br>

__CONVERT *(Bit Value. NOT Length)*__  



<br>


__ADD__  

  
  
<br>


__INSERT(*IPASOK Many Times*)__  


<br>


1. Office: 
2. Office: 
3. Office: 
4. Office: 
5. Office: 
6. Office: 
7. Office: 
8. Office: 


<br>
<br>

---
&nbsp;


### 🎯 Exercise 03: Subnet for 4 offices using the network address fd00:2::/88

__CONVERT__  
 


<br>


__ADD__  
 
  
  
<br>


__INSERT(*IPASOK Many Times*)__  



<br>


1. Office: 
2. Office: 
3. Office:
4. Office:


<br>
<br>

---
&nbsp;


### 🎯 Exercise 04: Subnet for 52 offices using the network address fd00:3:0:33::/112  Determine the 6th subnet.


__CONVERT__  


<br>


__ADD__  

  
  
<br>


__INSERT(*IPASOK Many Times*)__  




<br>


1. Office: 
2. Office: 
3. Office: 
4. Office: 
5. Office: 
6. Office: 


<br>
<br>

|         | IP Address             |
| ---     | ---                    | 
| Network |                        |
| 1st IP  |                        |
| Last IP |                        |
|         |                        |
| Not Net |                        |


<br>

__Reserved Anycast__

|             | IP Address             |
| ---         | ---                    | 
| Network ANY |                        |
| 1st IP      |                        |
| Last IP     |                        |
|             |                        |
| 1st ANY     |                        |
| Last ANY    |                        |
|             |                        |
| Not Net     |                        |


<br>
<br>

---
&nbsp;


### Find IPv6 Values & Implementation

|             | IP Address             |
| ---         | ---                    | 
| Network ANY | fd00::8728        /126 |
| 1st IP      |                        |
| Last IP     |                        |
|             |                        |
| Not Net     |                        |

<br>

~~~
!@R3
conf t
 ipv6 unicast-routing
 int e0/2
  no shut
  ipv6 add 
  end
~~~

<br>

~~~
!@R2
conf t
 ipv6 unicast-routing
 int e0/2
  no shut
  ipv6 add 
  end
~~~


&nbsp;
---
&nbsp;


### Find IPv6 Values & Implementation

|             | IP Address             |
| ---         | ---                    | 
| Network ANY | fd00::9060        /123 |
| 1st IP      |                        |
| Last IP     |                        |
|             |                        |
| Not Net     |                        |

<br>

~~~
!@R2
conf t
 ipv6 unicast-routing
 int e0/3
  no shut
  ipv6 add
  end
~~~

<br>

~~~
!@R1
conf t
 ipv6 unicast-routing
 int e0/3
  no shut
  ipv6 add
  end
~~~


<br>
<br>

---
&nbsp;


### IPv6 Static Routing

__R4 - R2__
~~~
!@R4
conf t
 ipv6 route 
 end
~~~

<br>

~~~
!@R2
conf t
 ipv6 route
 end
~~~


&nbsp;
---
&nbsp;


__R3 - R1__
~~~
!@R3
conf t
 ipv6 route 
 end
~~~

<br>

~~~
!@R1
conf t
 ipv6 route 
 end
~~~


<br>
<br>

---
&nbsp;


## In-house vs MSP

~~~
!@CoreTAAS
conf t
 hostname CoreTAAS-41
 enable secret pass
 service password-encryption
 no ip domain lookup
 no logging cons
 line cons 0 
  password pass
  login
  exec-timeout 0 0
 line vty 0 14
  password pass
  login
  exec-timeout 0 0
 int vlan 1
  ip add 10.41.1.2 255.255.255.0
  no shut
  end
~~~

<br>

~~~
!@CoreBABA
conf t
 hostname CoreBABA-41
 enable secret pass
 service password-encryption
 no ip domain lookup
 no logging cons
 line cons 0 
  password pass
  login
  exec-timeout 0 0
 line vty 0 14
  password pass
  login
  exec-timeout 0 0
 int vlan 1
  ip add 10.41.1.4 255.255.255.0
  no shut
  end
~~~


&nbsp;
---
&nbsp;


### Remote Access

~~~
!@cmd
ping 10.41.1.2
ping 10.41.1.4

nmap -v 10.41.1.2
nmap -v 10.41.1.4
~~~

Telnet the following
- 10.41.1.2
- 10.41.1.4


<br>
<br>

---
&nbsp;


## DISCOVERY PROTOCOL (CDP & LLDP 802.1AB) 

<br>

Discover:
1. MAC Address
2. Port
3. OS
4. Capabilitites


&nbsp;
---
&nbsp;


### 🎯 Exercise 05: Identify port connections between switches.
~~~
!@Switches
clear cdp counter
clear cdp table
show cdp neighbor
~~~

<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>

<br>
<br>

---
&nbsp;


## Master the five superheroes of switching
- QPid
- Darna
- Wonderwoman
- Superman


&nbsp;
---
&nbsp;


### 1. QPID (802.1Q)
*Access vs Trunk*

__Access vs Trunk Links__
~~~
!@CoreTAAS & CoreBABA
conf t
 default int fa0/10-12
 int range fa0/10-12
  switchport trunk encapsulation dot1q
  switchport mode trunk
  switchport trunk allowed vlan all
  switchport trunk native vlan 1
  no shut
  end
show int trunk
~~~


<br>
<br>

---
&nbsp;


### 🎯 Exercise 06: Configure Trunk links between C1,C2,A1,A2

<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>


<br>
<br>

---
&nbsp;


### Master Switching

1. __Mode Button__
- STAT: Link Status (Green = Link up, Amber = Fault/Blocked, Off = No link)
- SPEED: Port Speed (Green = 1 Gbps, Amber = 10/100 Mbps, Off = 10 Mbps)
- DPLX: Duplex Status (Green = Full, Amber = Half, Off = No connection)
- POE: PoE Status (Green = Supplying power, Amber = Fault/Disabled)

<br>

2. __Password Recovery__
- ROMMON

~~~
!@CoreTAAS (ROMMON)
flash_init


dir flash:
delete flash:config.txt

boot
~~~


<br>

3. __Factory Reset__
- Hold until All AMBER


<br>
<br>

---
&nbsp;


### L2 Switching vs L3 Routing

~~~
!@CoreTAAS
conf t
 hostname coreTaas-41
 enable secret pass
 service password-encryption
 no logging console
 no ip domain-lookup
 line cons 0
  password pass
  login
  exec-timeout 0 0
 line vty 0 14
  password pass
  login
  exec-timeout 0 0
 int vlan 1
  no shut
  ip add 10.41.1.2 255.255.255.0
  desc DEFAULT-VLAN
 int vlan 10
  no shut
  ip add 10.41.10.2 255.255.255.0
  desc WIFI-VLAN
 int vlan 50
  no shut
  ip add 10.41.50.2 255.255.255.0
  desc CCTV-VLAN
 int vlan 100
  no shut
  ip add 10.41.100.2 255.255.255.0
  desc VOICE-VLAN
 end
~~~

<br>

~~~
!@CoreBABA
conf t
 hostname coreBaba-41
 enable secret pass
 service password-encryption
 no logging console
 no ip domain-lookup
 line cons 0
  password pass
  login
  exec-timeout 0 0
 line vty 0 14
  password pass
  login
  exec-timeout 0 0
 int gi 0/1
  no shut
  no switchport
  ip add 10.41.41.4 255.255.255.0
 int vlan 1
  no shut
  ip add 10.41.1.4 255.255.255.0
  desc DEFAULT-VLAN
 int vlan 10
  no shut
  ip add 10.41.10.4 255.255.255.0
  desc WIFI-VLAN
 int vlan 50
  no shut
  ip add 10.41.50.4 255.255.255.0
  desc CCTV-VLAN
 int vlan 100
  no shut
  ip add 10.41.100.4 255.255.255.0
  desc VOICE-VLAN
 end

!@dhcp
conf t
 ip dhcp excluded-add 10.41.1.1 10.41.1.100
 ip dhcp excluded-add 10.41.10.1 10.41.10.100
 ip dhcp excluded-add 10.41.50.1 10.41.50.100
 ip dhcp excluded-add 10.41.100.1 10.41.100.100

 ip dhcp pool POOLDATA
  network 10.41.1.0 255.255.255.0
  default-router 10.41.1.4
  domain-name MGMTDATA.COM
  dns-server 10.41.1.10
 ip dhcp pool POOLWIFI
  network 10.41.10.0 255.255.255.0
  default-router 10.41.10.4
  domain-name WIFIDATA.COM
  dns-server 10.41.1.10
  option 43 ip 10.41.10.41
 ip dhcp pool POOLCCTV
  network 10.41.50.0 255.255.255.0
  default-router 10.41.50.4
  domain-name CCTVDATA.COM
  dns-server 10.41.1.10
 ip dhcp pool POOLVOICE
  network 10.41.100.0 255.255.255.0
  default-router 10.41.100.4
  domain-name VOICEDATA.COM
  dns-server 10.41.1.10
  option 150 ip 10.41.100.8
 end

!@switchport
conf t
 vlan 10
  name WIFIVLAN
 vlan 50
  name CCTVVLAN
 vlan 100
  name VOICEVLAN
 int fa 0/2
  switchport mode access
  switchport access vlan 10
 int fa 0/4
  switchport mode access
  switchport access vlan 10
 int fa 0/6
  switchport mode access
  switchport access vlan 50
 int fa 0/8
  switchport mode access
  switchport access vlan 50
 int fa 0/3
  switchport mode access
  switchport access vlan 100
 int fa 0/5
  switchport mode access
  switchport voice vlan 100
  switchport access vlan 1
  mls qos trust device cisco-phone
 int fa 0/7
  switchport mode access
  switchport voice vlan 100
  switchport access vlan 1
  mls qos trust device cisco-phone
 end
 
!@ospf routing corebaba
 conf t
  router ospf 1
   router-id 10.41.41.4
   network 10.41.0.0 0.0.255.255 area 0
  int gi 0/1
   ip ospf network point-to-point
   end
~~~

<br>

~~~
!@CUCM
conf t
 hostname CUCM-41
 enable secret pass
 service password-encryption
 no logging console
 no ip domain-lookup
 line cons 0
  password pass
  login
  exec-timeout 0 0
 line vty 0 14
  password pass
  login
  exec-timeout 0 0
 int fa 0/0
  no shut
  ip add 10.41.100.8 255.255.255.0
 end

!@ospf routing CUCM
conf t
 router ospf 1
  router-id 10.41.100.8
  network 10.41.100.0 0.0.0.255 area 0
  end
~~~

<br>

~~~
!@EDGE
conf t
 hostname EDGE-41
 enable secret pass
 service password-encryption
 no logging console
 no ip domain-lookup
 line cons 0
  password pass
  login
  exec-timeout 0 0
 line vty 0 14
  password pass
  login
  exec-timeout 0 0
 int gi 0/0/0
  no shut
  ip add 10.41.41.1 255.255.255.0
  desc INSIDE
 int gi 0/0/1
  no shut
  ip add 200.0.0.41 255.255.255.0
  desc OUTSIDE
 int loopback 0
  ip add 41.0.0.1 255.255.255.255
  desc VIRTUALIP
 end

!@ospf routing EDGE
conf t
 router ospf 1
  router-id 41.0.0.1
  network 200.0.0.0 0.0.0.255 area 0
  network 10.41.41.0 0.0.0.255 area 0
  network 41.0.0.1 0.0.0.0 area 0
 int gi 0/0/0
  ip ospf network point-to-point
  end
~~~

<br>

~~~
!@P1
conf t
 int e0/0
  no shut
  ip add 10.2.1.101 255.255.255.0
 ip route 0.0.0.0 0.0.0.0 10.2.1.1
  end
~~~

<br>

~~~
!@P2
conf t
 int e1/0
  no shut
  ip add 10.2.1.102 255.255.255.0
 ip route 0.0.0.0 0.0.0.0 10.2.1.2
  end
~~~

<br>

~~~
!@A1
conf t
 int e0/0
  switchport mode access
  switchport access vlan 10
  end
~~~

<br>

~~~
!@A2
conf t
 int e1/0
  switchport mode access
  switchport access vlan 10
  end
~~~

<br>

~~~
!@C1
conf t
 router eigrp 100
  no auto-summary
  network 10.2.1.0 0.0.0.255
  network 10.2.2.0 0.0.0.255
  network 192.168.1.128 0.0.0.31
  network 10.1.4.4 0.0.0.3
  end
~~~

<br>

~~~
!@C2
conf t
 router eigrp 100
  no auto-summary
  network 10.2.1.0 0.0.0.255
  network 10.2.2.0 0.0.0.255
  network 192.168.1.128 0.0.0.31
  network 10.1.4.8 0.0.0.3
  end
~~~

<br>

~~~
!@R4
conf t
 router eigrp 100
  no auto-summary
  network 10.1.4.4 0.0.0.3
  network 10.1.4.8 0.0.0.3
  network 4.4.4.4 0.0.0.0
  end
sh ip route eigrp
~~~


<br>
<br>

---
&nbsp;


### What to look for in a switch.
1. Mac Address Learning
2. Mac Address Filtering
3. Mac Address Forwarding
4. Loop Avoidance
5. VLAN Feature


<br>
<br>

---
&nbsp;


### 2. DARNA (802.1D)

__How to get fired!__
~~~
!@CoreTAAS & CoreBABA
conf t
 no spanning-tree vlan 1-999
 end
~~~


<br>


__Save your network__
~~~
!@CoreTAAS & CoreBABA
conf t
 spanning-tree vlan 1-999
 end
~~~


&nbsp;
---
&nbsp;


### `32768  vs  24576  vs  28672`

Properly configure the switch

~~~
!@CoreTAAS & C2
conf t
 spanning-tree mode pvst
 spanning-tree vlan 1-999 root primary
 end
show spanning-tree vlan 1
~~~

<br>

~~~
!@CoreBABA & C1
conf t
 spanning-tree mode pvst
 spanning-tree vlan 1-999 root secondary
 end
show spanning-tree vlan 1
~~~




&nbsp;
---
&nbsp;


### Map out the L2 Topology : Port Roles
- Designated
- Root
- Alternate
- Back


&nbsp;
---
&nbsp;


### Steps & Tie Breakers:
1. Identify the Root Bridge
    - Determine the Lowest Root Bridge ID (Priority & MAC) among all switches

2. Identify Port Roles
    - RP (Root Port) - 1 per Non-Root Bridge
    - DP (Designated Port) - 1 per link
    - AP (Alternate Port)

3. Tie Breakers
    - Lowest Path Cost to Root
    - Lowest Bridge ID 
    - Lowest port ID (Priority + Port Number) of the Other Switch(Sender)
    - Lowest local port ID (Priority + Port Number)


<br>
<br>

---
&nbsp;


### 🎯 Exercise 07: Determine Port Roles

<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>

&nbsp;
---
&nbsp;


### How to determine Port Cost
Short Path Cost Method (IEEE 802.1D)

| Link Speed | Default Cost |
| ---        | ---          |
| 10 Mbps    | 100          |
| 100 Mbps   | 19           |
| 1 Gbps     | 4            |
| 10 Gbps    | 2            |

<br>

~~~
!@A1
conf t
 int e0/1
  spanning-tree cost 19
  end
~~~

<br>

~~~
!@C1
conf t
 int e1/3
  spanning-tree cost 19
  end
~~~


<br>
<br>

---
&nbsp;


### 🎯 Exercise 08: Identify port roles.

<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>

---
&nbsp;


### Who is __DARNA__ (__802.1D__)

| BLK | LIS | LRN | FWD   |
| --- | --- | --- | ---   |
|     | 15s | 15s | = 30s |

<br>

1. Blocking (BLK) - Listens for BPDUs, does not forward data
2. Listening (LIS) - Listens for BPDUs, starts topology change timer
3. Learning (LRN) - Builds MAC address table but does not forward traffic
4. Forwarding (FWD) - Forwards user traffic and BPDUs


&nbsp;
---
&nbsp;


### Switch Vulnerabilities: CDP, LLDP, DTP, & STP
~~~
!@C1
conf t
 int e3/3
  no shut
  switchport
  end
~~~


<br>
<br>

---
&nbsp;


### 3. ⚡ WONDERWOMAN (802.1W)
~~~
!@CoreTAAS & CoreBABA, C1,C2,A1,A2
conf t
 spanning-tree mode rapid-pvst
 end
show spanning-tree vlan 1
~~~

1. Discarding (DIS) - Not forwarding user frames; discards traffic. Listens for BPDUs
2. Learning (LRN) - Builds MAC address table but does not forward user traffic
3. Forwarding (FWD) - Forwards user traffic and BPDUs

<br>

__STP Features__
1. Portfast - Skips all STP negotiation and go straight to forwarding.
   - EDGE Port - Non-Switch link
   - NETWORK Port - Switch to Switch link
2. BPDU Guard - Shuts down a port that receives a BPDU.
3. LOOP Guard - When BPDUs is no longer recieved on Designated ports, keep the port blocked. | Blocking
4. Root Guard - Stops a port from accepting superior BPDUs. | Blocking
5. BPDUFilter - Will not send BPDUs until received.
6. UplinkFast - Recover quickly from uplink failure.
7. BackboneFast - Skips to Listening State

<br>

~~~
!@CoreTAAS
conf t
 spanning-tree backbonefast    !unnecessary for rstp (has built-in convergence)
 spanning-tree portfast bpdufilter default
 spanning-tree portfast bpduguard default
 int range fa0/1-8
  spanning-tree portfast  !edge
 !int range fa0/10-12
  !spanning-tree portfast !network
  end
~~~

<br>

~~~
!@CoreBABA
conf t
 spanning-tree uplinkfast    !unnecessary for rstp (has built-in convergence)
 spanning-tree backbonefast
 spanning-tree portfast bpdufilter default
 spanning-tree portfast bpduguard default
 int range fa0/1-8
  spanning-tree portfast
 !int range fa0/10-12
  !spanning-tree portfast !network
  end
~~~


<br>
<br>

---
&nbsp;


### 🎯 Exercise 09: Determine STP Features
What STP features should be applied on the network to optimize STP traffic and network performance.

~~~
!@C1
conf t
 int range e0/0-3,e1/2-3
  spanning-tree guard loop
  spanning-tree portfast network
 int range e1/0,e1/1
  spanning-tree portfast edge
  spanning-tree bpduguard enable
  spanning-tree bpdufilter enable
 spanning-tree backbonefast
  end  
~~~

<br>

~~~
!@C2
conf t
 int range e1/2-3
  spanning-tree guard loop
  spanning-tree portfast network
  spanning-tree uplinkfast
 int range e1/0,e1/1
  spanning-tree portfast edge
  spanning-tree bpduguard enable
  spanning-tree bpdufilter enable
 spanning-tree backbonefast
  end  
~~~

<br>

~~~
!@A1
conf t
 int range e0/1-3,e1/0
  spanning-tree guard loop
  spanning-tree portfast network
  spanning-tree uplinkfast
 int e0/0
  spanning-tree portfast edge
  spanning-tree bpduguard enable
  spanning-tree bpdufilter enable
 spanning-tree backbonefast
 spanning-tree uplinkfast
  end  
~~~

<br>

~~~
!@A2
conf t
 int range e0/0-3,e1/0
  spanning-tree guard loop
  spanning-tree portfast network
  spanning-tree uplinkfast
 int e1/0
  spanning-tree portfast edge
  spanning-tree bpduguard enable
  spanning-tree bpdufilter enable
 spanning-tree backbonefast
 spanning-tree uplinkfast
  end  
~~~


<br>
<br>

---
&nbsp;


### 4. SUPERMAN (802.1S)
__Step 1__: Configure VTP

~~~
!@CoreTAAS,C1,C2
conf t
 vtp domain ccna
 vtp mode server
 vtp version 1
 end
~~~

~~~
!@CoreBABA,A1,A2
conf t
 vtp domain ccna
 vtp version 1
 vtp mode client
 end
~~~


<br>


__Step 2__: Configure VLANs

~~~
!@CoreTAAS,C1
conf t
 vlan 1-40
  exit
 vlan 41-70
  exit
 vlan 71-100
 end
~~~

<br>

~~~
!@CoreBABA
conf t
 int range fa0/2,fa0/4
  switchport mode access
  switchport access vlan 10
 int range fa0/6,fa0/8
  switchport mode access
  switchport access vlan 50
 int fa0/3
  switchport mode access
  switchport access vlan 100
 int range fa0/5,fa0/7
  switchport voice vlan 100
  end
~~~


<br>


__Step 3__: Enable 802.1S
~~~
!@CoreTAAS,CoreBABA,C1,C2,A1,A2
conf t
 spanning-tree mode mst
 spanning-tree mst configuration
  name superman-stp
  revision 1
   instance 1 vlan 1-40
   instance 2 vlan 41-70
   instance 3 vlan 71-100
   end
show spanning-tree mst configuration
~~~


<br>


Reconfigure Port Priority
~~~
!@CoreTAAS,C1
config t
 spanning-tree mst 0 root primary
 spanning-tree mst 1 root secondary
 spanning-tree mst 2 root primary
 spanning-tree mst 3 root secondary
end
~~~

<br>

~~~
!@CoreBABA,C2
config t
 spanning-tree mst 0 root Secondary
 spanning-tree mst 1 root primary
 spanning-tree mst 2 root Secondary
 spanning-tree mst 3 root primary
end
~~~


<br>


Who is SUPERMAN (802.1S)
Multiple VLANs sharing a spanning tree instance,  
compared to PVST & RST where each VLANs is its own STP instance.


<br>
<br>

---
&nbsp;


## Port Aggregation
LACP vs PAGP

| Mode             | On  | Active/Desirable | Passive/Auto |
| ---              | --- | ---              | ---          |
| On               | [x] | [ ]              | [ ]          | 
| Active/Desirable | [ ] | [x]              | [x]          |
| Passive/Auto     | [ ] | [x]              | [ ]          |

~~~
!@CoreTAAS
conf t
 int range fa0/10-12
  channel-group 1 mode active
  channel-protocol lacp
  end
show int po1 | inc BW
~~~

<br>

~~~
!@CoreBABA
conf t
 int range fa0/10-12
  channel-group 1 mode passive
  channel-protocol lacp
  end
show int po1 | inc BW
~~~


<br>
<br>

---
&nbsp;


### 🎯 Exercise 10: Configure Etherchannel links

| Device | Po  |
| ---    | --- |
| C1-C2  | 12  |
| A1-C1  | 11  |
| A1-C2  | 10  |
| A2-C2  | 22  |
| A2-C1  | 20  |


<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>


<br>
<br>

---
&nbsp;


## IP ADDRESSING
### Switch Virtual Interface (SVI)

~~~
!@CoreTAAS
conf t
 int vlan 10
  description WIFIVLAN
  ip add 10.41.10.2 255.255.255.0
  no shut
  exit
 int vlan 50
  description CCTVVLAN
  ip add 10.41.50.2 255.255.255.0
  no shut
  exit
 int vlan 100
  description VOICEVLAN
  ip add 10.41.100.2 255.255.255.0
  no shut
 int range fa0/2,fa0/4
  switchport mode access
  switchport access vlan 10
  exit
 int range fa0/6,fa0/8
  switchport mode access
  switchport access vlan 50
  exit
 int fa0/3
  switchport mode access
  switchport access vlan 100
  exit
 int range fa0/5,fa0/7
  switchport mode access
  switchport access vlan 100
  switchport voice vlan 100
  mls qos trust device cisco-phone
  mls qos trust cos
  end
~~~

<br>

~~~
!@CoreBABA
conf t
 int vlan 10
  description WIFIVLAN
  ip add 10.41.10.4 255.255.255.0
  no shut
  exit
 int vlan 50
  description CCTVVLAN
  ip add 10.41.50.4 255.255.255.0
  no shut
  exit
 int vlan 100
  description VOICEVLAN
  ip add 10.41.100.4 255.255.255.0
  no shut
  end
~~~

<br>

~~~
!@P1
conf t
 int e0/0
  no shut
  ip add 10.2.1.101 255.255.255.0
  ip route 0.0.0.0 0.0.0.0 10.2.1.1
  end
~~~

<br>

~~~
!@P2
conf t
 int e0/0
  no shut
  ip add 10.2.1.102 255.255.255.0
  ip route 0.0.0.0 0.0.0.0 10.2.1.2
  end
~~~

<br>

~~~
!@A1
conf t
 int e0/0
  switchport mode access
  switchport access vlan 10
  end
~~~

<br>

~~~
!@A2
conf t
 int e1/0
  switchport mode access
  switchport access vlan 10
  end
~~~


<br>
<br>

---
&nbsp;


## Port Security
~~~
!@CoreBABA
conf t
 int fa0/6
  switchport mode access
  switchport port-security
  switchport port-security mac-address sticky
  switchport port-security maximum 1
  switchport port-security violation shutdown
  exit
 int fa0/8
  switchport mode access
  switchport port-security
  switchport port-security mac-address sticky
  switchport port-security maximum 1
  switchport port-security violation shutdown
  end
sh port-security address
sh int status err-disable
~~~

<br>

__Make Ports Alive again__
~~~
!@CoreBABA
config t
 int fa0/6
  no switchport port-security
  shut
  no shut
 int fa0/8
  no switchport port-security
  shut
  no shut
  end
~~~

 
<br>
<br>

---
&nbsp;


## ARP Inspection

__STATIC ARP INSPECTION__
~~~
!@CoreBABA
conf t
 ip arp inspection VLAN 1
 arp access-list STATIC-ARP
  permit ip host __.__.__.__  host mac __.__.__.__

  exit
 ip arp inspection filter STATIC-ARP vlan 1
 ip arp inspection validate src-mac dst-mac ip
 
 int range fa0/2-12
  ip arp inspection trust
  end
~~~  

<br>

~~~
!@C1
conf t
 ip arp inspection vlan 10
 arp access-list ARP
  permit ip host 10.2.1.100 mac host 0050.56c0.000f
 !
 ip arp inspection filter ARP vlan 10 static
 ip arp inspection validate src-mac dst-mac ip
 !
 int range e0/0-3,e1/0-3,e2/0-3,e3/0-2
  ip arp inspection trust
  end
~~~


<br>
<br>

---
&nbsp;


## DHCP Snooping & DAI

~~~
!@C1
conf t
 ip dhcp excluded-address 10.2.1.1 10.2.1.100
 ip dhcp pool MGMT
  network 10.2.1.0 255.255.255.0
  default-router 10.2.1.1
  dns-server 192.168.1.133
  domain-name C1.MGMT.COM
 end
~~~

<br>

~~~
!@C2
conf t
 ip dhcp excluded-address 10.2.1.1 10.2.1.100
 ip dhcp pool MGMT
  network 10.2.1.0 255.255.255.0
  default-router 10.2.1.2
  dns-server 10.2.1.2
  domain-name C2.MGMT.COM
 end
~~~

<br>

~~~
!@A1
conf t
 ip dhcp snooping
 ip dhcp snooping vlan 10
 int po11
  ip dhcp snooping trust
  exit
 int po10
  no ip dhcp snooping trust
  exit
 !
 no ip dhcp snooping information option
 end
show ip dhcp snooping
show ip dhcp snooping binding
~~~

<br>

~~~
!@P1
conf t
 int e0/0
  ip add dhcp
  end
~~~


&nbsp;
---
&nbsp;


__PREVENT DHCP STARVATION ATTACKS__
~~~
!@CoreTAAS
conf t
 ip dhcp snooping
 ip dhcp snooping vlan 1,10,50,100
 int po1
  ip dhcp snooping trust
  exit
 int fa0/1
  no ip dhcp snooping trust
  exit
 !
 no ip dhcp snooping information option
 !
 int fa0/1
  ip dhcp snooping limit rate 10
  end
show ip dhcp snooping
show ip dhcp snooping binding
~~~


<br>
<br>

---
&nbsp;


## FHRP
1. HSRP - MAC: 0000.0C07.AC  xx
2. VRRP - MAC: 0000.5E00.01  xx
3. GLBP - MAC: 0007.b4       xx.yyzz


&nbsp;
---
&nbsp;


### HSRP
~~~
!@CoreTAAS
conf t
 hostname CTAAS-PLDT
 !
 track 1 int g0/1 line-protocol
 !
 int vlan 1
  standby 1 ip 10.41.1.6
  standby 1 preempt
  standby 1 Priority 150
  standby 1 Track 1 decrement 60
  end
~~~

<br>

~~~
!@CoreBABA
conf t
 hostname CBABA-GLOBE
 !
 int vlan 1
  standby 1 ip 10.41.1.6
  standby 1 Priority 100
  end
~~~

<br>

~~~
!@C1
conf t
 track 1 int vlan 10 line-protocol
 !
 int vlan 10
  standby 1 ip 10.2.1.3
  standby 1 preempt
  standby 1 Priority 150
  standby 1 Track 1 decrement 60
  end
sh standby
~~~

<br>

~~~
!@C2
conf t
 int vlan 10
  standby 1 ip 10.2.1.3
  standby 1 Priority 100
  end
sh standby
~~~


&nbsp;
---
&nbsp;


### VRRP

~~~
!@C1
conf t
 track 1 int vlan 10 line-protocol
 !
 int vlan 10
  no standby 1
  !
  vrrp 1 ip 10.2.1.3
  vrrp 1 preempt
  vrrp 1 Priority 150
  vrrp 1 Track 1 decrement 60
  end
sh vrrp
~~~

<br>

~~~
!@C2
conf t
 int vlan 10
  no standby 1
  !
  vrrp 1 ip 10.2.1.3
  vrrp 1 Priority 100
  end
sh vrrp
~~~


<br>
<br>

---
&nbsp;


## Cisco & Fortinet

~~~
!@FWEDGE - LOCAL USER DIRECTORY
config system admin
 edit admin
  set accprofile super_admin
  set vdom root
  set password C1sc0123
  next
 edit user1
  set accprofile super_admin
  set vdom root
  set password pass
  end
show system admin
~~~


&nbsp;
---
&nbsp;


### IP ADDRESS
~~~
!@R4
conf t
 int e3/3
  no shut
  ip add 10.3.1.1 255.255.255.252
  end 
~~~

<br>

~~~
!@FWEDGE - L2 & L3 INTERFACE
config system interface
 edit port2
  set vdom root
  set mode static
  set type physical
  set ip 10.3.1.2 255.255.255.252
  set allowaccess ping https http ssh telnet
  set status up
  next
 edit port1
  set mode static
  set ip 208.8.8.200 255.255.255.0
  set allowaccess ping https http ssh telnet
  next
 edit loopback1
  set vdom root
  set type loopback
  set status up
  set ip 69.0.0.1 255.255.255.255
  set allowaccess ping https http ssh telnet
  end
get system interface physical
execute ping 10.3.1.1
~~~


&nbsp;
---
&nbsp;


### STATIC ROUTING
~~~
!@FWEDGE
get router info routing-table all
#
config router static
 edit 1
  set status enable
  set dst 0.0.0.0/0
  set gateway 208.8.8.2
  set distance 254
  set device port1
  end
execute ping 8.8.8.8
execute traceroute 8.8.8.8
~~~


&nbsp;
---
&nbsp;


### DYNAMIC ROUTING
~~~
!@C1,C2,R4
conf t
 no router eigrp 100
 end
~~~

<br>

~~~
!@C1
conf t
 router ospf 1
  network 10.1.4.4 0.0.0.3 area 0
  network 10.2.1.0 0.0.0.255 area 0
  network 10.2.2.0 0.0.0.255 area 0
  network 192.168.1.129 0.0.0.31 area 0
  end
~~~

<br>

~~~
!@C2
conf t
 router ospf 1
  network 10.1.4.8 0.0.0.3 area 0
  network 10.2.1.0 0.0.0.255 area 0
  network 10.2.2.0 0.0.0.255 area 0
  network 192.168.1.129 0.0.0.31 area 0
  end
~~~

<br>

~~~
!@R4
conf t
 router ospf 1
  router-id 4.4.4.4
  exit
 int range e1/0-1,e3/3
  ip ospf 1 area 0
 int e3/3
  ip ospf network point-to-point
  end
sh ip ospf neigh
~~~

<br>

~~~
!@FWEDGE
config router ospf 
 set router-id 10.3.1.2
 set passive-interface loopback1 port1
 config area
  edit 0.0.0.0
  end
 config network
  edit 1
   set prefix 208.8.8.0 255.255.255.0
   set area 0.0.0.0
   set comments OUTSIDE
   next
  edit 2
   set prefix 10.3.1.0 255.255.255.252
   set area 0.0.0.0
   set comments INSIDE
   next
  edit 3
   set prefix 69.0.0.1 255.255.255.255
   set area 0.0.0.0
   set comments LOOPBACK
   end
 config ospf-interface
  edit FW-R4
   set interface port2
   set status enable
   set network-type point-to-point
   end
  end
get router info ospf neighbor
get router info ospf status
get router info routing-table all
~~~


&nbsp;
---
&nbsp;


### FW POLICY
~~~
!@FWEDGE
config firewall policy
 edit 1
  set name INSIDE-TO-OUTSIDE
  set srcintf port2
  set dstintf port1
  set srcaddr all
  set dstaddr all
  set action accept 
  set schedule always
  set service ALL
  set nat enable
  next
 edit 2
  set name OUTSIDE-TO-INSIDE
  set srcintf port1
  set dstintf port2
  set srcaddr all
  set dstaddr all
  set action accept 
  set schedule always
  set service ALL
  set nat disable
  end
show firewall policy
~~~


&nbsp;
---
&nbsp;


### REDISTRIBUTE : DEFAULT ROUTE PROPAGATION
~~~
!@FWEDGE
config router ospf 
 set default-information-originate enable 
 end
~~~

<br>

~~~
!@P1
ping 8.8.8.8
traceroute 8.8.8.8 probe 1
~~~


<br>
<br>

---
&nbsp;

~~~
!@FWEDGE
config system interface
 edit port2
  config vrrp
   edit 1
    set ?
~~~



