 
 ``` 
     1.Change Hostname.
     2.VTP Status. 
     3.Create VLAN Management & VLAN users.
     4.Create Interface VLAN.
     5.Trunk Interface configuration.
     6.Set Password in different modes.
     7.Configure Console & VTY lines.
     8.Access Ineterface configuration.
     9.Create User.
     10.Configure CDP & LLDP. 
 ```

## 1.Change Hostname: 
Juniper01@Juniper_SW_101> `edit`  ______ // going to edit mode or configuration mode </br>
Entering configuration mode

{master:0}[edit] </br>
Juniper01@Juniper_SW_101# `edit system` 

[edit system] </br>
Juniper01@Juniper_L2_SW-101# `set host-name Juniper_L2_SW-101`

## 2.VTP Status:
in juniper insted of VTP there is GVRP and MVRP , and MVRP is disabled by default to configure:

[edit protocols] </br>
Juniper01@Juniper_L2_SW-101# `set mvrp interface xe-0/0/0` 


### To verify: </br>

[edit protocols] </br>
Juniper01@Juniper_L2_SW-101# `show mvrp` 

Juniper01@Juniper_L2_SW-101> `show mvrp` 

## 3.Create VLAN Management & VLAN users:
{master:0}[edit] </br>
Juniper01@Juniper_SW_101# `set vlan user40 vlan-id 40`

{master:0}[edit] </br>
Juniper01@Juniper_SW_101# `set vlan user40 description all_40_users_can_access_to_vlan_user40;`

{master:0}[edit] </br>
Juniper01@Juniper_SW_101# `set vlan remote vlan-id 50`

{master:0}[edit] </br>
Juniper01@Juniper_SW_101# `set vlan remote description Management_vlan` 

{master:0}[edit] </br>
Juniper01@Juniper_SW_101# `set vlan V-native vlan-id 10`

{master:0}[edit] </br>
Juniper01@Juniper_SW_101# `set vlan V-native description "This vlan is native for xe-0/0/0 link"`

{master:0}[edit] </br>
Juniper01@Juniper_SW_101# `commit` // to test configuration `commit check`

### To verify: </br>

{master:0}[edit vlans] </br>
Juniper01@Juniper_L2_SW-101# `show` 
```
default {
    vlan-id 1;
}
remote {
    description Management_vlan;
    vlan-id 50;
}
user40 {
    description "all_40_users_can_access_to_vlan_user40;";
    vlan-id 40;
}

```

{master:0}[edit vlans] </br>
Juniper01@Juniper_L2_SW-101# `show user40` 

Juniper01@Juniper_L2_SW-101> `show vlans`

Juniper01@Juniper_L2_SW-101> `show vlans brief`


## 4.Create Interface VLAN:
> Juniper support 2 logical L3 interface for vlans  `vlan and irb` besad on which logical L3 interface is JunOS supported create vlan interface: </br> 
> if support vlan interface it will be like: `set interface vlan unit x ...` </br>
> if support irb interface it will be like : `set interface irb  unit x ...` </br>
> 
> `unit 50` **refer to tag of remote vlan that has vlan-id = 50 So this interface Vlan is for remot vlan interface**  </br>
> `unit 40` **refer to tag of user40 vlan that has vlan-id = 40 So this interface Vlan is for user40 vlan interface**

</br> </br>

Juniper01@Juniper_SW_101# `set vlans remote l3-interface irb.50`  _**without this command interface vlan not get to up state**

Juniper01@Juniper_SW_101# `set interface irb unit 50 family inet address 10.10.50.101/24`  </br>

Juniper01@Juniper_SW_101# `set vlans user40 l3-interface irb.40` _**without this command interface vlan not get to up state**

Juniper01@Juniper_SW_101# `set interface irb unit 40 family inet address 10.10.40.101/24`  </br>

### To verify:

{master:0}[edit interfaces] </br>
Juniper01@Juniper_L2_SW-101# `show irb` 

Juniper01@Juniper_L2_SW-101> `show interface terse`

Juniper01@Juniper_L2_SW-101> `show interface irb`


##  5.Trunk Interface configuration and native vlan:

Juniper01@Juniper_L2_SW-101# `set interface xe-0/0/0 unit 0 family ethernet-switching interface-mode trunk`

Juniper01@Juniper_L2_SW-101# `set interface xe-0/0/0 unit 0 family ethernet-switching vlan member [ remote user40 ]`

Juniper01@Juniper_L2_SW-101# `set interface xe-0/0/0 native-vlan-id 10` _**the hierarchy of native vlan is before unit 0 or before logical interface**

### To verify:
Juniper01@Juniper_L2_SW-101> `show ethernet-switching interface`

Juniper01@Juniper_L2_SW-101> `show ethernet-switching interface detail`

> **Part of result** </br>
> Tagging: tagged                           ......_**untagged mean mode is access and tagged mean mode is trunk**  

Juniper01@Juniper_L2_SW-101> `show configuratioin | display set | match trunk`





## 6.Set Password in different modes: & 7.Configure Console & VTY lines: 

> **set password for console by default is no passowrd** 
         
Juniper01@Juniper_L2_SW-101# `set system pic-console-authentication plain-text-password`  </br>
New password: </br>
Retype new password: </br>

> **Use `system port` hierarchy to configure console and auxiliary ports:** </br>
> By default, the terminal type is set to unknown. To change the terminal type, include the type statement, specifying a terminal-type of ansi, vt100, small-xterm, or xterm. The first three terminal types set a screen size of 80 columns by 24 lines. The last type, xterm, sets the size to 80 columns by 65 rows.


Juniper01@Juniper_L2_SW-102# `set system ports ?`    
```
Possible completions:                                
 auxiliary            Auxiliary port              
 console              Console port                
```

Juniper01@Juniper_L2_SW-102# `set system ports console ?`  **to configure console port**

```
Possible completions:
  disable              Disable console
  insecure             Disallow superuser access
  log-out-on-disconnect  Log out the console session when cable is unplugged
  type                 Terminal type 
```  

> **configuration Telnet , SSH , web Interface Console**

> All it is under `edit system services` hierarchy: 

{master:0}[edit system services] </br>
Juniper01@Juniper_L2_SW-102# `set telnet connection-limit 2` 

{master:0}[edit system services] </br>
Juniper01@Juniper_L2_SW-101# `set ssh protocol-version v2`

 {master:0}[edit system services] </br>
Juniper01@Juniper_L2_SW-102# `set ssh hostkey-algorithm ssh-rsa`

{master:0}[edit system services] </br>
Juniper01@Juniper_L2_SW-101# set ssh connection-limit 2 


**Jweb config !!!**

### To verify:

{master:0}[edit system port] </br>
Juniper01@Juniper_L2_SW-101# `show` or `show console` or `show auxiliary`

{master:0}[edit system services] </br>
Juniper01@Juniper_L2_SW-101# `show telnet`

{master:0}[edit system services] </br>
Juniper01@Juniper_L2_SW-101# `show ssh`

## 8.Access Ineterface configuration:
Juniper01@Juniper_L2_SW-101# `set interface xe-0/0/1 unit 0 family ethernet-swithcing interface-mode access`

Juniper01@Juniper_L2_SW-101# `set interface xe-0/0/1 unit 0 family ethernet-swithcing vlan member user40`

### To verify:
Juniper01@Juniper_L2_SW-101> `show configuratioin | display set | match access`
Juniper01@Juniper_L2_SW-101> `show ethernet-switching interface detail`

> **Part of result** </br>
> Tagging: untagged                           ......_**untagged mean mode is access and tagged mean mode is trunk**  

## 9.Create User:

the hierarcy is `edit >> system >> login` 

Juniper01@Juniper_L2_SW-101# `set system login user user100 class super-user authentication plain-text-password` </br>
New password: </br>
Retype new password: </br>

> explain of command: </br>
Juniper01@Juniper_L2_SW-101# `set system login user <username> class <authorize or user> authentication plain-text-password`


### To verify:

{master:0}[edit system login] </br>
Juniper01@Juniper_L2_SW-101# `show`

Juniper01@Juniper_L2_SW-101# `status`

Juniper01@Juniper_L2_SW-101> `show system loging`

Juniper01@Juniper_L2_SW-101> `show system user`

Juniper01@Juniper_L2_SW-101> `show cli authorization` **To show the authorization of current user**

## 10.Configure LLDP: 
Juniper01@Juniper_L2_SW-101#`set protocols lldp interface all`  **This enough to work lldp currectly**

#### Optionaly


**{master:0}[edit protocols]  </br>
Juniper01@Juniper_L2_SW-101# `set lldp?`     </br>    
Possible completions:  </br>
lldp &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp; &ensp;&ensp;&ensp; Link Layer Detection Protocol  </br>
lldp-med &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp; LLDP Media Endpoint Discovery**  </br>



**{master:0}[edit protocols lldp] </br>
Juniper01@Juniper_L2_SW-102# `set neighbour-port-info-display port-description`**

### To verify:
Juniper01@Juniper_L2_SW-101> `show lldp`        //**to show configuration of lldp** </br>
Juniper01@Juniper_L2_SW-101> `show lldp neighbour`  </br>
Juniper01@Juniper_L2_SW-101> `show lldp neighbour interface xe-0/0/0`  </br>
Juniper01@Juniper_L2_SW-101> `show lldp detail`  </br>
