

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
 
