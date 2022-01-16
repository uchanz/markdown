# Enable FIPS 140-2 and Fscrypt

## Activate Fips 140-2

Enter the following command to download package:
```command
sudo apt update
sudo apt install ubuntu-advantage-tools
sudo ua attach <TOKEN>
```
> Note: you need to create account on ubuntu advantage for token by click this [LINK](https://ubuntu.com/advantage)

Enable FIPS
1. Enable FIPS including security updates.
```fips
sudo ua enable fips-updates
```
2. Verify that the system is attached to UA and has FIPS enabled.
```verify
sudo ua status
```
3. Please proceed to the reboot section.

>Note: To verify that FIPS is enabled after the reboot check the /proc/sys/crypto/fips_enabled file and ensure it is set to 1. If it is set to 0, the FIPS modules will not run in FIPS mode. If the file is missing, the FIPS kernel is not installed, you can verify that FIPS has been properly enabled with the ua status command.

## Fscrypt setup on Ubuntu 20.04

### Initial setup
To setup a filesystem to support encryption, first check that your block size is equal to your page size by comparing the outputs of getconf PAGE_SIZE and tune2fs -l /dev/device | grep 'Block size'. If these are not the same, DO NOT ENABLE ENCRYPTION.

```
getconf PAGE_SIZE
4096
```

```
sudo tune2fs -l $DEVICE | grep 'Block size'
Block size:               4096
```

As the values are the same we can proceed. Now enable encryption on the EXT4 device:

```
tune2fs -O encrypt $DEVICE
```

Now we need to install some fscrypt
```
sudo apt-get install fscrypt libpam-fscrypt
```

### Set up PAM
Create the file /usr/share/pam-configs/keyinit-fix (need sudo rights) and fill with the following

```
Name: keyinit fix
Default: yes
Priority: 0
Session-Type: Additional
Session:
	optional	pam_keyinit.so force revoke
```

Next re-configure pam to use fscrypt

```
sudo pam-auth-update
```
Now log out of the session and in again to load the new pam files.

### Encrypt the home partitition

```
sudo fscrypt setup
Replace "/etc/fscrypt.conf"? [y/N] y
Customizing passphrase hashing difficulty for this system...
Created global config file at "/etc/fscrypt.conf".
sudo fscrypt setup /
```
Do this as in a TTY terminal (i.e. CTRL-ALT 1) as root or another user as your system might act strange if your are graphically logged in while doing this.

```
sudo su -
export USERNAME=user1
mv /home/$USERNAME /home/$USERNAME.bak
mkdir /home/$USERNAME
chown $USERNAME:$USERNAME /home/$USERNAME
fscrypt encrypt /home/$USERNAME --user=$USERNAME
rsync -avH --info=progress2 --info=name0 /home/$USERNAME.bak/ /home/$USERNAME/
rm -rf /home/$USERNAME.bak
```

### References
[Enabling FIPS 140](https://ubuntu.com/security/certifications/docs/fips-enablement)

[Set up fscrypt](https://tlbdk.github.io/ubuntu/2018/10/22/fscrypt.html)