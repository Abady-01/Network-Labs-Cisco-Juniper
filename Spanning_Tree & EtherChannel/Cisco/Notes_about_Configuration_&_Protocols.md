

![image](https://user-images.githubusercontent.com/78827896/156818062-6cd4465d-5da7-4c0d-8bae-5ee5160bc752.png)   

![image](https://user-images.githubusercontent.com/78827896/156818137-b654dc50-b614-4640-87a8-e94b142aaae5.png) 



**The most recent models and IOS versions of Cisco switches default to use RSTP instead of STP.**

**By default, RSTP is enabled on all Ethernet switching enabled ports on the Juniper Networks EX series Switches.**

**Since RSTP only has single Spanning Tree instance for all VLANs across a trunk and there is no VLAN awareness, all traffic will be forwarded or blocked based on the VLAN 1 topology.**

**MSTP is if you have thousands of vlan**

**The priority of switch to become a root Bridge**

> essentially the switch with the lowest priority becomes the root </br>


> If a tie occurs based on the priority portion of the BID, the switch with the lowest MAC address portion of the BID is the root. </br>

**The priority of to win a port as root port**

> if none root Switche has two port linked to root Bridge then switch need a tiebreaker, as follows: </br>


> 1. the cost of link to reach to Root Brige. </br>
> 2. Choose based on the lowest neighbor bridge ID. </br>
> 3. Choose based on the lowest neighbor port priority. </br>
> 4. Choose based on the lowest neighbor internal port number. </br> 

**How two Designated ports in tow different Switch win in Designated role election?** 

Chapter 9: Spanning Tree Protocol Concepts - page 221

![image](https://user-images.githubusercontent.com/78827896/156834758-d9aa5f05-b11f-409a-b2e5-8c66a01b7b2d.png)


> When a nonroot switch forwards a Hello, the nonroot switch sets the root cost field in the Hello to that switch’s cost to reach the root. 
> In effect, the switch with the lower cost to reach the root, among all switches connected to a segment, becomes the DP on that segmen. </br>



> If the advertised costs tie, the switches break the tie by choosing the switch with the lower BID.
> In this case, SW2 would also have won, with a BID of 32769:0200.0002.0002 versus SW3’s 32769:0200.0003.0003.
> But switch ports connected to endpoint devices should become DPs and settle into a forwarding state and user port fast.
 
 **RSTP works so much like STP that they can both be used in the same network. RSTP and STP switches can be deployed in the same network**
 
 **New RSTP Prot Rules**
> RSTP uses the term alternate port to refer to a switch’s other ports that could be used as the root port if the root port ever fails.
> Note that backup ports apply only to designs that use hubs, so they are unlikely to be useful today.
 
 
 
 
 `**See if juniper support RSTP in 802.1Q, in 2011 the IEEE moved all the RSTP details into a
revised 802.1Q standard. As it stands today, RSTP actually sits in the 802.1Q standards
document`
 
 ## do 
 
 port fast - bpdu guard - 
 
# Notes

And even if some switches use RSTP and some use STP, the switches can
interoperate and still build a working spanning tree—and you never even have to think about
changing any settings!

remember STP + RSTP + MSTP is from IEEE while pvst+ and Rpvst+ from Cisco "make sure is VSTP is form IEEE"
RSTP creates one tree—the Common Spanning Tree (CST) —while RPVST+ creates one
tree for each and every VLAN. 

MSTP is equal Rpvst because is besad on RSTP and used RSTP Rules and port state 

Chapter 10: RSTP and EtherChannel Configuration page 246 "take a picture"
 (, you might be interested in reading more about RSTP configuration in the
companion website’s Appendix O, “Spanning Tree Protocol Implementation.”) 

 with Cisco Catalyst switches dose not support the single tree like STP or RSTP, you have to use multi instances protocol like PVST or RPVST or MSTP "make sure from this info" 

SW1(config)# spanning-tree mode ?
mst
 Multiple spanning tree mode
pvst
 Per-Vlan spanning tree mode
rapid-pvst
 Per-Vlan rapid spanning tree mode
SW1(config)#

The reason that there is Multi tree instance of STP is for redundancy So if you use MSTP, PVST, RpVST and make the root bridg is one device is not make sance at least two swich most be a root 

 requires a decimal number between 0 and 65,535. But not just any number in that
range will suffice; it must be a multiple of 2*4096 because the header of BID is change and add system ID multi tree STP has last 2 Bytes for priority, from 4096 to 65535 
like 4096, 8192, 12288, 16384, 20480, 24576, 28672, 32768, 36864, 40960, 45056, 49152, 53248, 57344, 61440 

. STP no longer operates on physical interfaces Fa0/14 and Fa0/15, instead
operating on the PortChannel1 interface, so only that interface is listed in the output.

"take pic of 249"

"take pic Appendix page 6"

 most network engineers make the distribution layer switches be the root. For instance,
the configuration could make D1 be the root by having a lower priority, with D2 config-
ured with the next lower priority, so it becomes root if D1 fails. "typicaly is the correct behavor" 
"because if you using Core its have all vlan for all project insted of it let each Distribution be root of its LANs "

# port channel

 Cisco Catalyst switches support the Cisco-proprietary Port Aggregation Protocol
(PAgP) and the IEEE standard Link Aggregation Control Protocol (LACP) , based on IEEE
standard 802.3ad. 

PAgP = {desirable | auto}
LACP = { active | passiv }

or { on | on } you can not use PAgP or LACP with on like {on | passiv} its wrong must on with on, in other side

physical interface remains configured as part of the PortChannel, but it is not used as part of
the channel, often being placed into some nonworking state.
The list of items the switch checks includes the following:
■
 Speed
■
 Duplex
■
 Operational access or trunking state (all must be access, or all must be trunks)
■
 If an access port, the access VLAN
■
 If a trunk port, the allowed VLAN list (per the switchport trunk allowed command)
■
 If a trunk port, the native VLAN
■
 STP interface settings interface stp cost

