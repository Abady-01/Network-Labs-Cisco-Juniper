## First Time using juniper appliance: 

#### - Juniper will start with root mode, Initially, the root user account requires no password.  </br>

#### - Start the Junos OS command-line interface (CLI): </br>

`root@# cli` </br>
`root@>` </br>


#### - Enter Junos OS configuration mode: </br>

`cli> configure` </br>
`[edit]` </br>
`root@#` </br>


#### - Set the root password, entering either a clear-text password that the system will encrypt, or password that is already encrypted, or an SSH public key string.

`[edit]` </br>
`root@# set system root-authentication plain-text-password` </br>
`New password: type password` </br>
`Retype new password: retype password` </br>

#### - Configure the IP address and prefix length for the device management ether on fxp0 or em0 </br>

`[edit]` </br>
`root@# set interfaces fxp0 unit 0 family inet address <ip address>/<perfix>` </br>

#### - Configure Basic system setting like , hostname , back server , dns server , etc.. Under `edit system` </br>

```
[edit]
root@ show
system {
    host-name hostname;
    domain-name domain.name;
    backup-router address;
    root-authentication {
        (encrypted-password "password" | public-key);
        ssh-dsa "public-key";
        ssh-ecdsa "public-key";
        ssh-rsa "public-key";
    }
    name-server {
        address;
    }
    interfaces {
        fxp0 {
            unit 0 {
                family inet {
                    address address ;
                } } } } }

```

#### - Management Juniper Device:
> to manege Juniper device all juniper device has a phisycal L3 management port called **em0** or **fxp0** so withoute create interface vlan you can manage juniper through this interface **or** as usually create interface vlan for management. 

#### - Vlan Interface on juniper:
> Because most of Juniper device is a layer 3 Switch `set vlan vlan100 l3-interface irb.100` this command has **two influence:** </br>
> **one:** is make vlan 100 L3 vlan and make the state of interface vlan 100 is up up state </br>
> **seconde:** as i mention because most of juniper Switch is L3 Swithc this command active **inter vlan route** automatically and put interface vlan 100 to routing tabel and all interface vlan has route and reach to other interface vlan, so to isolate may i have to use VRF. </br>
> **Note** Juniper has two logical interface for vlan interface one is `vlan` other is `irb` so besad on which interface is supported by JunOS create vlan interface on it like `set vlan remote l3-interface vlan.20` **or** `set vlan MGMT l3-interface irb.20` and you can know witch logical vlan is support by `show interface terse`

 #### - Native Interface: 
 > On junper native vlan has to location in heirarchy: </br>
 > 1. `set interface ge-0/0/0 unit 0 family ethernet-switching interface-mode trunk [native-vlan-id <id>]` </br>
 > 2. `set interface ge-0/0/0 native-vlan-id <vlan-id>`




 
 































