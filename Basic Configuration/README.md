

# Lab Contents:    
1. **Layer 2 Switch image i used on PNETlab is** `i86bi_linux_l2-adventerprisek9-ms.SSA.high_iron_20190423.bin` </br> </br>
2. **Virtual PC (VPCS)** </br> </br> </br>



![image](https://user-images.githubusercontent.com/78827896/148983250-a11de005-6764-4047-96af-61604d0b80b3.png)

**Download the lab** https://github.com/Abady-01/Network-Labs-Cisco-Juniper/raw/main/Basic%20Configuration/Basic_Configuration_Lab.zip </br></br>

**Or** </br></br> 

**Copy The URL of Lab.zip file and generate Download link here >>**    https://downgit.github.io/#/home 

</br>
</br>

</br>


## All username is (lab) and password is (123)  

</br>
</br>
</br>


# Command Emplemented 

### Change Hostname:
`Swithc(config)# hostname < name >    # Example: Swithc(config)# hostname Switch-1_Floor_1`  </br>
### VTP Status:
`Swithc(config)# vtp mode transparent` </br>
### Create VLAN Management & VLAN users:
`Swithc(config)#vlan 10`  </br>
`Swithc(config-vlan)# name MGMT` </br>
`Swithc(config)#vlan 20` </br>
`Swithc(config-vlan)# name users` </br>

### Create Interface Management VLAN:
`Swithc(config)# int vlan 10` </br>
`Swithc(config-if)# ip address < ip address >`  .............# Example: Switch(config-if)# ip address 192.168.1.1 </br>

### Set Password in different modes:
`Swithc(config)# enable secter < password >` </br>
`Swithc(config)# service password-encryption` </br>

### Configure Console & VTY lines:
`Swithc(config)# line console 0` </br>
`Swithc(config-line)# password < password >`    ..............# Example: Switch(config-line)# password 123 </br>
`Swithc(config-line)# login` </br>

`Swithc(config)#line vty 0 4` </br>
`Swithc(config-line)# password < password >` </br>
`Swithc(config-line)# login local` </br>
`Swithc(config-line)# transport input telnet ssh` </br>

### Trunk Interface configuration:
`Swithc(config)# int e0/0` </br>
`Swithc(config-if)# switchport trunk encapsulation dot1q` </br>
`Swithc(config-if)# switchport mode trunk` </br>
`Swithc(config-if)# switchport trunk allowed vlan all` </br>

### Access Ineterface configuration:
`Swithc(config)#int e0/0` </br>
`Swithc(config-if)# switchport mode access` </br>
`Swithc(config-if)# switchport access vlan < VLAN-Number/ID >` </br>

### Create User:
`Swithc(config)# username lab privilege < Authoraized_Num > secret < password >` ...... # Example: username Adam privilege 10 secret 123 </br>

### SSH Configuration:
`Swithc(config)# ip ssh versioin 2` </br>
`Swithc(config)# ip domain-name < name >` </br>
`Swithc(config)# crypto key generate rsa moduluse 1024` </br>

### Configure CDP & LLDP 
`Swithc(config)# run cdp`  </br>
`Swithc(config)# run lldp` </br>


















login mean just request password </br>
login local mean request password with username  </br>
to connect by ssh in cisco command is : ssh -l <username> <ip_address> Ex: ssh -l lab 3.3.10.10 </br>
  the degree of privilig users </br>
  option of transparen input ssh </br>
