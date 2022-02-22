
# Lab content

**in this lab i used** `junos-vsrx3-x86-64-20.1R1.11` **image as Layer 2 Swithc **

### To preparing your lab with this image : </br>

**First install image by ishare :** ` ishare pull junos-vsrx3-x86-64-20.1R1.11 ` </br>

**Then follow this documents** </br>

##### https://www.eve-ng.net/index.php/documentation/howtos/howto-add-juniper-vsrx-ng-15-x-and-later/ 

![image](https://user-images.githubusercontent.com/78827896/154631982-d99e68b4-a389-4478-83c1-fbab1b06c1ef.png) </br>

# first time juniper device booting up the initial (mandatory) configuration:

**vqfx-re (ttyd0)**

**login:** `root`

**Password:** `Juniper`

**root@vqfx-re:RE:0%** `cli`

**root@vqfx-re>** `edit`

**root@vqfx-re#** `set system root-authentication plain-text-password` 

**New password:**  ____write a password

**Retype new password:**

**root@vqfx-re#** `set system host-name Juniper_SW_101`

**root@vqfx-re#** `set system login user Juniper01 class super-user authentication plain-text-password` 

**New password:** `Lab123`  

**Retype new password:**`Lab123`

**root@vqfx-re#** `commit` 

### Now exit and login as user was created Juniper01 and your juniper device is ready to work

# All username and password in this lab is: 

**Username: Juniper01** 

**Password: Lab123** 

































