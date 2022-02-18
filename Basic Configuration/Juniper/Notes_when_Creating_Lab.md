## First Time using juniper appileance: 

#### 1. Juniper will start with root mode, Initially, the root user account requires no password.  </br>

#### 2.Start the Junos OS command-line interface (CLI): </br>

`root@# cli` </br>
`root@>` </br>


#### 3. Enter Junos OS configuration mode: </br>

`cli> configure` </br>
`[edit]` </br>
`root@#` </br>


#### 4. Set the root password, entering either a clear-text password that the system will encrypt, or password that is already encrypted, </br>

#### or an SSH public key string. </br>

`[edit]` </br>
`root@# set system root-authentication plain-text-password` </br>
`New password: type password` </br>
`Retype new password: retype password` </br>

#### 5. Configure the IP address and prefix length for the device management ether on fxp0 or em0 </br>

`[edit]` </br>
`root@# set interfaces fxp0 unit 0 family inet address address/prefix-length` </br>

#### 6. Configure Basic system setting like , hostname , back server , dns server , etc.. Under `edit system` </br>

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

































