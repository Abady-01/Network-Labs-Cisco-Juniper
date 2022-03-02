
![image](https://user-images.githubusercontent.com/78827896/156429489-99958f79-76bc-49ac-8b47-6d2f05aea451.png)


# Lab content

**in this lab I used juniper QFX image as Layer 2 Swithc to work juniper QFX Switch you have to install QFX-routing Engine and QFX-Packet Forward Engine then they work as one device in PnetLab.**
- `vqfxre-10K-F-18.4R1.9` </br>
- `vqfxpfe-10K-F-18.4R1.9` </br>

</br>
</br>

### To preparing your lab with this image : </br> </br>

**First install image on PnetLab by** `ishare` **command :**

` ishare pull vqfxre-10K-F-18.4R1.9 `  

</br>

`ishare pull vqfxpfe-10K-F-18.4R1.9` </br>

**Then follow this documents** </br>

##### https://www.eve-ng.net/index.php/documentation/howtos/howto-add-juniper-vqfx/

![image](https://user-images.githubusercontent.com/78827896/155206694-4a9faaf3-c8ec-47fa-85f9-ca6e2aa8427f.png) </br>
![image](https://user-images.githubusercontent.com/78827896/155207369-9a52a699-6d2c-4fe7-aa02-8b19d1f58c64.png) </br>


`mv /opt/unetlab/addons/qemu/vqfxpfe-10K-F-17.4R1.16/cosim_20180212.qcow2 /opt/unetlab/addons/qemu/vqfxpfe-10K-F-17.4R1.16/hda.qcow2` </br>

`mv /opt/unetlab/addons/qemu/vqfxre-10K-F-17.4R1.16/jinstall-vqfx-10-f-17.4R1.16.img /opt/unetlab/addons/qemu/vqfxre-10K-F-17.4R1.16/hda.qcow2` </br>

![image](https://user-images.githubusercontent.com/78827896/155211094-cf00154d-3c64-4603-a986-82c078329bc4.png) </br>




# first time juniper device booting up the initial (mandatory) configuration:

### 1.Turn on vqfx-re and keeep off vqfx-pfe:

### 2. Do this mandatory configuration on vqfx-re:

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

### Now exit and login as user was created `Juniper01`, Turn on both of engine `vqfxre and vqfxpfe` and your juniper device is ready to work

# All username and password in this lab is: 

**Username: Juniper01** 

**Password: Lab123** 

































