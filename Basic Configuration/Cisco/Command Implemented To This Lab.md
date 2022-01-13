





# Configuration has Emplemented: 
  
```diff
 
 1.Change Hostname.
 2.VTP Status. 
 3.Create VLAN Management & VLAN users.
 4.Create Interface Management VLAN.
 5.Set Password in different modes.
 6.Configure Console & VTY lines.
 7.Trunk Interface configuration.
 8.Access Ineterface configuration.
 9.Create User.
 10.SSH Configuration.
 11.Configure CDP & LLDP. 
 
 ```
 
 


### 1.Change Hostname:
`Swithc(config)# hostname < name >    # Example: Swithc(config)# hostname Switch-1_Floor_1`  </br>
### 2.VTP Status:
`Swithc(config)# vtp mode transparent` </br>
### 3.Create VLAN Management & VLAN users:
`Swithc(config)#vlan 10`  </br>
`Swithc(config-vlan)# name MGMT` </br>
`Swithc(config)#vlan 20` </br>
`Swithc(config-vlan)# name users` </br>

### 4.Create Interface Management VLAN:
`Swithc(config)# int vlan 10` </br>
`Swithc(config-if)# ip address < ip address >`  .............# Example: Switch(config-if)# ip address 192.168.1.1 </br>

### 5.Set Password in different modes:
`Swithc(config)# enable secter < password >` </br>
`Swithc(config)# service password-encryption` </br>

### 6.Configure Console & VTY lines:
`Swithc(config)# line console 0` </br>
`Swithc(config-line)# password < password >`    ..............# Example: Switch(config-line)# password 123 </br>
`Swithc(config-line)# login` </br>

`Swithc(config)#line vty 0 4` </br>
`Swithc(config-line)# password < password >` </br>
`Swithc(config-line)# login local` </br>
`Swithc(config-line)# transport input telnet ssh` </br>

### 7.Trunk Interface configuration:
`Swithc(config)# int e0/0` </br>
`Swithc(config-if)# switchport trunk encapsulation dot1q` </br>
`Swithc(config-if)# switchport mode trunk` </br>
`Swithc(config-if)# switchport trunk allowed vlan all` </br>

### 8.Access Ineterface configuration:
`Swithc(config)#int e0/0` </br>
`Swithc(config-if)# switchport mode access` </br>
`Swithc(config-if)# switchport access vlan < VLAN-Number/ID >` </br>

### 9.Create User:
`Swithc(config)# username lab privilege < Authoraized_Num > secret < password >` </br></br>

....# Example: username Adam privilege 10 secret 123 </br>

### 10.SSH Configuration:
`Swithc(config)# ip ssh versioin 2` </br>
`Swithc(config)# ip domain-name < name >` </br>
`Swithc(config)# crypto key generate rsa moduluse 1024` </br>

### 11.Configure CDP & LLDP 
`Swithc(config)# run cdp`  </br>
`Swithc(config)# run lldp` </br>

