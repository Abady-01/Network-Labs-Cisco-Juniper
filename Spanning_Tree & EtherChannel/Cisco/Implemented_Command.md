
## With Spanning-tree protocols Cisoc support `PVST+, Rpvst+, MSTP`  </br> and dose not support any single instance Spanning-tree like `STP or RSTP`

</br>

</br>

</br>

``` 
     1. initial configuration 
     
     2. configure PVST+ change root priority, port cost.
     
     3. configure Rpvst+ change root priority, prot cost.
     
     4. configure MSTP spesify the root and secondry.
     
     5. enabe port fast and bpdu guard
   
```
## 1. initial configuration:


switch(config)# `hostname Cisco_L2_Sw-101`

Cisco_L2_Sw-101(config)# `#service password-encryption `
     
Cisco_L2_Sw-101(config)# `no ip domain lookup`

 __________________________________________________**Configure Vlan 11,12,13,21,22,23,31,32,33,41,42,43:**

Cisco_L2_Sw-101(config)# `vlan 11`

Cisco_L2_Sw-101(config-vlan)# `name V_11` 

__________________________________________________**SSH configuration:**

Cisco_L2_Sw-101(config)# `ip domain name Cisco_Lab_Switch`

Cisco_L2_Sw-101(config)# `ip ssh version 2`

Cisco_L2_Sw-101(config)# `crypto key generate rsa module 2048` 

__________________________________________________**Create user:**

Cisco_L2_Sw-101(config)# `username <my-username> Cisco01 privilege 15 secret <Password> (Lab123)`

__________________________________________________**All Interface Trunk:**

Cisco_L2_Sw-101(config-if)# `switchport trunk encapsulation dot1q`

Cisco_L2_Sw-101(config-if)# `switchport mode trunk`

Cisco_L2_Sw-101(config-if)# `switchport trunk allowed vlan all`

__________________________________________________**Console line:**

Cisco_L2_Sw-101(config-line)# `login local`

Cisco_L2_Sw-101(config-line)# `session-timeout 3000` 

__________________________________________________**vty line:**

Cisco_L2_Sw-101(config-line)# `login local`

Cisco_L2_Sw-101(config-line)# `transport input ssh`

Cisco_L2_Sw-101(config-line)# `session-timeoute 3000`

__________________________________________________**To share config file from Sw-101 to other 3 Switches by** `scp://` **:**
     
Cisco_L2_Sw-101(config)# `ip scp server enable` 

> When useing `scp://` : </br>

>  1- On server side make suer that you directory is where you want to copy from, and make `cd` to right folder, </br>
>  **Example if you want copy** `startup-config` **from nvram make** `cd nvram:` *because client after access to ip server like 
>  scp://192.168.1.1 client will look for files on your current server directory* </br>
>  </br>
>  2. On client side make sure that you enable SSH and generate a SSH key 


**To verify:**

Cisco_L2_Sw-101# `show vlan`

Cisco_L2_Sw-101# `show interface status`

Cisco_L2_Sw-101# `show run interface e0/0`

Cisco_L2_Sw-101# `show ip ssh`

Cisco_L2_Sw-101# `show user `

Cisco_L2_Sw-101# `show interface e0/0 switchport`

Cisco_L2_Sw-101# `show interface trunk`

Cisco_L2_Sw-101# `show interface status` ___also show trunk port </br>




SW1(config)# spanning-tree mode ? "to enble protocols of STP" </br>

spanning-tree vlan vlan-id priority x "To define priority of bridge for x vlan " </br>

spanning-tree vlan x root primary (on the switch that should be primary) </br>
spanning-tree vlan x root secondary (on the switch that should be secondary) you have not to type priority number </br>

 show spanning-tree vlan 9 </br>
 
 show spanning-tree </br>
 
 SW1# show spanning-tree summary </br>
 
 show spanning-tree interface interface-id </br>
 
 show spanning-tree root, lists the root’s BID for each VLAN </br>
 
 Port Costs: The interface subcommand spanning-tree [vlan x] cost y lets an engineer </br>
set the switch’s STP/RSTP cost on that port, either for all VLANs or for a specific VLAN </br>
on that port. </br>

e the spanning-tree portfast and </br>
the spanning-tree bpduguard enable interface subcommands. </br>





show protocols </br>
vstp { </br>
    vlan all { </br>
        interface all; </br>
    } </br>
    
   
    
    root> show configuration protocols vstp </br>
    
    root> show spanning-tree bridge    | no-more </br>
    
    https://kb.juniper.net/InfoCenter/index?page=content&id=KB15138  </br>
    
    https://kb.juniper.net/InfoCenter/index?page=content&id=KB12260 </br>
    
    https://kb.juniper.net/InfoCenter/index?page=content&id=KB18291&actp=RSS </br>
    
    https://community.juniper.net/communities/community-home/digestviewer/viewthread?MID=70609#bm121e6471-0b79-41ab-b5f2-20fc3ca7cd39  </br>
    
    how many VSTP support vlan  </br>
    




## Ether Channel 

 channel-group number mode on "to add ether chnnel" </br>
 
 show etherchannel </br>
 
 SW1# show spanning-tree vlan 3 </br>
 
 SW1# show etherchannel 1 summary </br>
 
  show etherchannel 1 port-channel </br>
 
 show etherchannel [channel-group- </br>
 Lists information about the state of EtherChannels on </br>
number] {brief | detail | port | port- </br>
 this switch.</br>
channel | summary} </br>
 
 e show etherchannel 1 summary </br>
 
# Implementing RSTP </br>
 
 he spanning-tree mode </br>
rapid-pvst </br> 

    
