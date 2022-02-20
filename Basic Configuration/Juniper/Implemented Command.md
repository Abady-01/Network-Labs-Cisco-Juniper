0

on first time Start the Junos OS command-line interface from root mode `root@:~ #` use cli command 
`root@:~ # cli`


in juniper insted of VTP there is GVRP and MVRP :
 MVRP is disabled by default.
 to configure it, it is under edit >> protocols 
 to show is it enable or disable
 show mvrp 
 show gvrp 
 show protocols mvrp 
 shwo protocols gvrp 
 
 create interface vlan 
 
 set vlan MGMT l3-interface vlan.<MGMT vlan-id> example: set vlan MGMT l3-interface vlan.20

 **Note**  you can manage juinper device with vlan interface or L3 management interface that exist phisycaly on device 

 **Trunk** 
 ELS EX and QFX devices:

root# set interfaces ge-0/0/<port#>.0 family ethernet-switching interface-mode trunk [native-vlan-id <id>] vlan members [ whitespace separated list of vlan names or IDs ]

root# commit
 
Legacy devices:

root# set interfaces ge-0/0/<port#>.0 family ethernet-switching port-mode trunk [native-vlan-id <id>] vlan members [ whitespace separated list of vlan names or IDs ]
 
 show ethernet-switching interfaces 
 show ethernet-switching interfaces details
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
