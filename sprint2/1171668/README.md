RCOMP 2019-2020 Project - Sprint 2 - Member 1171668 folder
===========================================
(This folder is to be created/edited by the team member 1171668 only)

## IPv4 network addresses ##

### Local servers and administration workstations (DMZ) ###
	Hosts Required: 12
	Network: 10.169.38.128/28
	Usable Hosts: 14
	First IP Address: 10.169.38.129
    Last IP Address: 10.169.38.142

### Floor one outlets ###
	Hosts Required: 70
	Network: 10.169.39.0/25
	Usable Hosts: 126
	First IP Address: 10.169.39.1
    Last IP Address: 10.169.39.126

### Ground floor outlets ###
	Hosts Required: 60
	Network ID: 10.169.37.64/26
	Usable Hosts: 62
	First IP Address: 10.169.38.65
    Last IP Address: 10.169.38.126

### Wi-Fi network ###
	Hosts Required: 100
	Network ID: 10.169.39.128/25
	Usable Hosts: 126
	First IP Address: 10.169.39.129
    Last IP Address: 10.169.39.254

### VoIP (IP-phones) ###
	Hosts Required: 35
	Network ID: 10.169.38.0/26
	Usable Hosts: 62
	First IP Address: 10.169.38.1
    Last IP Address: 10.169.38.62

## Routing tables ##
### Router IC EdB ###
	0.0.0.0/0 via 10.169.36.1

### Router MC Campus ###
	10.169.36.0/23 via 10.169.36.2
	10.169.38.0/23 via 10.169.36.3
	10.169.34.0/23 via 10.169.36.4
	10.169.32.0/23 via 10.169.36.5
	0.0.0.0/0 via 17.10.5.149