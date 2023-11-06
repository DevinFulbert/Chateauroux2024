# 9/ Les Confs des différents équipements

## <span style="color: black"> **Interfaces / IP's du Switch Core** ##

```
interface FastEthernet1/0/1
 switchport access vlan 211
 switchport mode access
!
interface FastEthernet1/0/2
 switchport access vlan 211
 switchport mode access
!
interface FastEthernet1/0/3
 switchport access vlan 211
 switchport mode access
!
interface FastEthernet1/0/4
 switchport access vlan 211
 switchport mode access
!
interface FastEthernet1/0/5
 switchport access vlan 216
 switchport mode access
!
interface FastEthernet1/0/6
 switchport access vlan 216
 switchport mode access
!
interface FastEthernet1/0/7
 switchport access vlan 216
 switchport mode access
!
interface FastEthernet1/0/8
 switchport access vlan 216
 switchport mode access
!
interface FastEthernet1/0/9
 switchport access vlan 217
 switchport mode access
!
interface FastEthernet1/0/10
 switchport access vlan 217
 switchport mode access
!
interface FastEthernet1/0/11
 switchport access vlan 217
 switchport mode access
!
interface FastEthernet1/0/12
 switchport access vlan 217
 switchport mode access
!
interface FastEthernet1/0/13
 switchport access vlan 215
 switchport mode access
!
interface FastEthernet1/0/14
 switchport access vlan 215
 switchport mode access
!
interface FastEthernet1/0/15
 switchport access vlan 215
 switchport mode access
!
interface FastEthernet1/0/16
 switchport access vlan 215
 switchport mode access
!
interface FastEthernet1/0/17
 switchport access vlan 214
 switchport mode access
!
interface FastEthernet1/0/18
 switchport access vlan 214
 switchport mode access
!
interface FastEthernet1/0/19
 switchport trunk encapsulation dot1q
 switchport trunk allowed vlan 217
 switchport mode trunk
!
interface FastEthernet1/0/20
 switchport trunk encapsulation dot1q
 switchport mode trunk
!
interface FastEthernet1/0/21
 switchport access vlan 210
 switchport mode access
!
interface FastEthernet1/0/22
 switchport access vlan 210
 switchport mode access
!
interface FastEthernet1/0/23
 switchport access vlan 210
 switchport mode access
!
interface FastEthernet1/0/24
 switchport access vlan 210
 switchport mode access
!
interface GigabitEthernet1/0/1
!
interface GigabitEthernet1/0/2
!
interface Vlan1
 no ip address
!
interface Vlan210
 ip address 172.28.0.254 255.255.255.0
!
interface Vlan211
 ip address 172.28.1.254 255.255.255.0
!
interface Vlan212
 no ip address
!
interface Vlan213
 no ip address
!
interface Vlan215
 ip address 172.28.5.254 255.255.255.0
 ip helper-address 172.28.1.2
!
interface Vlan216
 ip address 172.28.2.1 255.255.255.0
!
interface Vlan217
 ip address 172.28.3.2 255.255.255.0
!
ip default-gateway 172.28.3.254
ip classless
ip route 0.0.0.0 0.0.0.0 172.28.2.254
ip http server
ip http secure-server
!
```

## <span style="color: black"> **Interfaces / IP's / Routes des Routeurs** ##

Routeur 1 :

```
interface Embedded-Service-Engine0/0
 no ip address
 shutdown
!
interface GigabitEthernet0/0
 ip address 221.87.136.2 255.255.255.252
 ip nat outside
 no ip virtual-reassembly in
 duplex auto
 speed auto
!
interface GigabitEthernet0/1
 ip address 172.28.3.253 255.255.255.0
 ip nat inside
 no ip virtual-reassembly in
 glbp 1 ip 172.28.3.254
 glbp 1 load-balancing host-dependent
 duplex auto
 speed auto
 no mop enabled
!
interface Serial0/1/0
 no ip address
 shutdown
 clock rate 2000000
!
ip default-gateway 221.87.136.1
ip forward-protocol nd
!
no ip http server
no ip http secure-server
!
ip nat inside source list 1 interface GigabitEthernet0/0 overload
ip nat inside source list 2 interface GigabitEthernet0/0 overload
ip route 0.0.0.0 0.0.0.0 221.87.136.1
ip route 172.28.2.0 255.255.255.0 172.28.3.2
ip route 172.28.3.0 255.255.255.0 183.44.36.1
!
access-list 1 permit 192.168.36.0 0.0.0.255
access-list 2 permit 172.28.0.0 0.0.31.255
!
```

Routeur 2 :

```
interface Embedded-Service-Engine0/0
 no ip address
 shutdown
!
interface GigabitEthernet0/0
 ip address 183.44.36.1 255.255.255.252
 ip nat outside
 ip virtual-reassembly in
 duplex auto
 speed auto
!
interface GigabitEthernet0/1
 ip address 172.28.3.252 255.255.255.0
 ip nat inside
 ip virtual-reassembly in
 glbp 1 ip 172.28.3.254
 glbp 1 load-balancing host-dependent
 duplex auto
 speed auto
!
interface Serial0/0/0
 no ip address
 shutdown
 clock rate 2000000
!
ip default-gateway 183.44.36.2
ip forward-protocol nd
!
no ip http server
no ip http secure-server
!
ip nat inside source list 1 interface GigabitEthernet0/0 overload
ip nat inside source list 2 interface GigabitEthernet0/0 overload
ip route 0.0.0.0 0.0.0.0 183.44.36.2
ip route 172.28.2.0 255.255.255.0 172.28.3.2
ip route 172.28.3.0 255.255.255.0 221.87.136.2
!
access-list 1 permit 192.168.36.0 0.0.0.255
access-list 2 permit 172.28.0.0 0.0.31.255
!
```