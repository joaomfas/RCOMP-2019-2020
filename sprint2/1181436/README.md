RCOMP 2019-2020 Project - Sprint 2 - Member 1181436 folder
===========================================
(This folder is to be created/edited by the team member 1181436 only)

#### This is just an example for a team member with number 1181436 ####
### Each member should create a folder similar to this, matching his/her number. ###
The owner of this folder (member number 1181436) will commit here all the outcomes (results/artifacts/products)		       of his/her work during sprint 2. This may encompass any kind of standard file types.

## Building C IPv4 network addresses ##
### Local servers and administration workstations (DMZ) ###
	Hosts Required: 250
	Network ID: 10.169.34.0/24
	Usabel Hosts: 254
	First IP Address: 10.169.34.1

### Wi-Fi network ###
	Hosts Required: 60
	Network ID: 10.169.35.0/26
	Usabel Hosts: 62
	First IP Address: 10.169.35.1

### Floor one outlets ###
	Hosts Required: 44
	Network ID: 10.169.35.64/26
	Usabel Hosts: 62
	First IP Address: 10.169.35.65

### Ground floor outlets ###
	Hosts Required: 40
	Network ID: 10.169.35.128/26
	Usabel Hosts: 62
	First IP Address: 10.169.35.129

### VoIP (IP-phones) ###
	Hosts Required: 40
	Network ID: 10.169.35.192/26
	Usabel Hosts: 62
	First IP Address: 10.169.35.193

## Routing tables ##
### Router IC EdC ###
	0.0.0.0/0 via 10.169.36.1
### Router MC Campus ###
	10.169.36.0/23 via 10.169.36.2
	10.169.38.0/23 via 10.169.36.3
	10.169.34.0/23 via 10.169.36.4
	10.169.32.0/23 via 10.169.36.5
	0.0.0.0/0 via 17.10.5.149
### Router ISP ###
	10.169.32.0/20 via 17.10.5.150

Nota: O STP está ativo por defeito em todos os switch.

## VLAN database (VTP server:  A_MC) ##
### VTP Domain: vtnag2 ###

	700 - A_groundOutlets
	701 - A_floorOneOutlets
	702 - A_wifi
	703 - A_DMZ
	704 - A_VoIP
	706 - B_groundOutlets
	707 - B_floorOneOutlets
	708 - B_wifi
	709 - B_DMZ
	710 - B_VoIP
	711 - C_groundOutlets
	712 - C_floorOneOutlets
	713 - C_wifi
	714 - C_DMZ
	715 - C_VoIP
	716 - D_groundOutlets
	717 - D_floorOneOutlets
	718 - D_wifi
	719 - D_DMZ
	720 - D_VoIP
