

**Verifying and Analyzing Ethernet Switching**

`show interfaces status`

`show interfaces f0/1 counters`

`show mac address-table dynamic`

`show mac address-table dynamic vlan 1`





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
    
1. implement rstp and its show and its enable or disable </br>

2. implement pvst and its show and its enable or disable </br>

3. implement rpvst+ and its show and its enable or disable </br>

4. implement MSTP and its show and its enable or disable </br>

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

    
