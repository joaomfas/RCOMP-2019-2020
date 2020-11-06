RCOMP 2019-2020 Project - Sprint 3
===========================================
(This folder is to be created/edited by the team member 1171668 only)

### 1 OSPF dynamic routing ###

Static routing will no longer be used, thus on every router, the existing static routing tables should be erased, the only exception is the default route established in the building A router.

**Configs**

    **Backbone**

    no router ospf 1
    router ospf 1
    network 10.169.36.0 0.0.0.127 area 0
    default-information originate
    exit

    **Edificio A**
    no router ospf 1
    router ospf 1
    network 10.169.36.0 0.0.0.127 area 0
    network 10.169.37.64 0.0.0.63 area 1
    network 10.169.37.0 0.0.0.63 area 1
    network 10.169.37.128 0.0.0.31 area 1
    network 10.169.36.128 0.0.0.127 area 1
    network 10.169.37.160 0.0.0.31 area 1
    exit

    **Edificio B**
    no router ospf 1
    router ospf 1
    network 10.169.36.0 0.0.0.127 area 0
    network 10.169.38.64 0.0.0.63 area 2
    network 10.169.39.0 0.0.0.127 area 2
    network 10.169.39.128 0.0.0.127 area 2
    network 10.169.38.128 0.0.0.15 area 2
    network 10.169.38.0 0.0.0.63 area 2
    exit

    **Edificio C**
    no router ospf 1
    router ospf 1
    network 10.169.36.0 0.0.0.127 area 0
    network 10.169.35.128 0.0.0.63 area 3
    network 10.169.35.64 0.0.0.63 area 3
    network 10.169.35.0 0.0.0.63 area 3
    network 10.169.34.0 0.0.0.255 area 3
    network 10.169.35.192 0.0.0.63 area 3
    exit

    **Edificio D**
    no router ospf 1
    router ospf 1
    network 10.169.36.0 0.0.0.127 area 0
    network 10.169.32.192 0.0.0.63 area 4
    network 10.169.32.128 0.0.0.63 area 4
    network 10.169.32.64 0.0.0.63 area 4
    network 10.169.33.0 0.0.0.255 area 4
    network 10.169.32.0 0.0.0.63 area 4
    exit

**Useful Links**
[Laboratory class 06](https://moodle.isep.ipp.pt/pluginfile.php/318035/mod_resource/content/2/PL06-RCOMP-2019-2020.pdf)
EX 4 ~ 6

### 2 HTTP Service ###

    DMZ->HTTP->{mudar index.html}

### 3 DHCPv4 Service ###

The router in each building must provide the DHCPv4service to all local networks(within the building), except  for  DMZ  networks  and  the  backbone  where  IPv4  node  addresses  are  static  and  manually  set (routers and servers).

For  the  VoIP  VLAN,  the  DHCP  server  configuration  has  toinclude option  150,  it represent  the  IP address of the TFTP (Trivial File Transfer Protocol) server to be used by Cisco IP phones model 7960 to download their configuration file.

**Configs**


    **Edificio B**


    **DHCP SERVER CONFIG**

    ip dhcp excluded-address 10.169.38.65 10.169.38.70
    ip dhcp pool net_B_groundOutlets
    default-router 10.169.38.65
    network 10.169.38.64 255.255.255.192
    dns-server 10.169.38.130
    domain-name rcomp-19-20-na-g2
    exit
    ip dhcp excluded-address 10.169.39.1 10.169.39.5
    ip dhcp pool net_B_floorOneOutlets
    default-router 10.169.39.1
    network 10.169.39.0 255.255.255.128
    dns-server 10.169.38.130
    domain-name rcomp-19-20-na-g2
    exit
    ip dhcp excluded-address 10.169.39.129 10.169.39.133
    ip dhcp pool net_B_wifi
    default-router 10.169.39.129
    network 10.169.39.128 255.255.255.128
    dns-server 10.169.38.130
    domain-name rcomp-19-20-na-g2
    exit
    ip dhcp excluded-address 10.169.38.1 10.169.38.5
    ip dhcp pool net_B_voIP
    default-router 10.169.38.1
    option 150 ip 10.169.38.1
    network 10.169.38.0 255.255.255.192
    dns-server 10.169.38.130
    domain-name rcomp-19-20-na-g2
    exit
### 4 VoIP service ###

In  the  simulation,  for  VoIP local testing,  in  each  building  there **should be  at  least  two connected IP phones** (please, use the 7960 model available in Packet Tracer).

Ports of switches connecting to Cisco IP phones 7960, must have the **voice VLAN enabled** (switchport voice vlan VLANID) and the **access VLAN disabled** (no switchport access vlan).

**Configs**

    **B_HC0.1** [switch ground floor]
    interface GigabitEthernet4/1
    switchport mode access
    switchport voice vlan 710
    no switchport access vlan
    exit

    **B_HC1.1** [switch floor 1]
    interface GigabitEthernet7/1
    switchport mode access
    switchport voice vlan 710
    no switchport access vlan
    exit

    **Edificio B** [router]

    telephony-service
    max-ephones 30
    max-dn 30
    ip source-address 10.169.38.1 port 2000
    auto assign 1 to 30
    exit
    no ephone-dn 1
    ephone-dn 1
    number 2001
    exit
    no ephone-dn 2
    ephone-dn 2
    number 2002
    exit
    dial-peer voice 1 voip
    destination-pattern 1...
    session target ipv4:10.169.36.2
    exit
    dial-peer voice 3 voip
    destination-pattern 3...
    session target ipv4:10.169.36.4
    exit
    dial-peer voice 4 voip
    destination-pattern 4...
    session target ipv4:10.169.36.5
    exit

**Useful Links**
[Laboratory class 06](https://moodle.isep.ipp.pt/pluginfile.php/318035/mod_resource/content/2/PL06-RCOMP-2019-2020.pdf)
EX 9

...

### 5 DNS ###

| Tipo | Nome | Detail |
|------|------|--------|
|NS|.|rcomp-19-20-na-g2|
|NS|rcomp-19-20-na-g2|10.169.39.130|
|ARecord|rcomp-19-20-na-g2|10.169.39.130|
|ARecord|server1|10.169.39.131|
|CNAME|web|server1|
|CNAME|www|server1|
|CNAME|dns|ns|
|NS|ns.building-a.rcomp-19-20-na-g2|10.169.36.130|
|NS|ns.building-c.rcomp-19-20-na-g2|10.169.34.3|
|NS|ns.building-d.rcomp-19-20-na-g2|10.169.33.2|
|CNAME|building-a.rcomp-19-20-na-g2|ns.building-a.rcomp-19-20-na-g2|
|CNAME|building-c.rcomp-19-20-na-g2|ns.building-c.rcomp-19-20-na-g2|
|CNAME|building-d.rcomp-19-20-na-g2|ns.building-d.rcomp-19-20-na-g2|


### 6 NAT (Network Address Translation) ###

    interface gigabitEthernet 0/3/0
    ip nat inside
    interface gigabitEthernet 0/3/0.1
    ip nat inside
    interface gigabitEthernet 0/3/0.2
    ip nat inside
    interface gigabitEthernet 0/3/0.3
    ip nat inside
    interface gigabitEthernet 0/3/0.4
    ip nat inside
    interface gigabitEthernet 0/3/0.5
    ip nat inside
    interface gigabitEthernet 0/2/0
    ip nat outside
    no access-list 5
    access-list 5 permit 10.169.38.128 0.0.0.15
    ip nat inside source list 5 interface gigabitEthernet 0/2/0 overload
    ip nat inside source static tcp 10.169.38.131 80 10.169.36.3 80
    ip nat inside source static tcp 10.169.38.131 443 10.169.36.3 443
    ip nat inside source static tcp 10.169.38.130 443 10.169.36.3 53
    ip nat inside source static udp 10.169.38.130 443 10.169.36.3 53


### 7 Static Firewall (ACLs) ###

Por fazer.