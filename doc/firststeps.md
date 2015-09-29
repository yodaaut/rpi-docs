# First Steps
This should be done after a fresh install.

## Users and Passwords
The minimal raspberry pi installation has only the admin-user `root` with a standard password. This should be changed immediatly.
* Login to the pi as root
* change the password
* add new user
```bash
ssh root@ip_from_pi
passwd
adduser USERNAME
```
If you want to delete the user with its homedirectory and/or its owned files, you need the `perl-modules` package.
```bash
apt-get update
apt-get install perl-modules
deluser --remove-all-files USERNAME
```
After creating a user, add the user to the sudo-group, if necessary.
* install sudo
* add your user to the sudo-group
* logout as root
* use your user
```bash
apt-get install sudo
adduser USERNAME sudo
exit
```
If you need root-priviledges, get them with `sudo`.
If you need permanent root-priviledges, get them with `sudo -Es`.
If you want to change to root, do `su - root`.

## ssh root-login
Since Debian Jessie the sshd configuration has changend upon the installation-progress. The root isn't allowed to login over ssh.
Due to our unattended installation-progress this access was granted because of non-existing user.
Now we have a user, so let's turn the root-access back to deny.
* open `/etc/ssh/sshd_config`
* search for `PermitRootLogin yes`
* change it to `PermitRootLogin no`
* restart ssh-daemon
For the lazy one's:
```bash
sudo sed -i 's/PermitRootLogin yes$/PermitRootLogin no/' /etc/ssh/sshd_config
sudo systemctl restart sshd.service
```

## Update packages
From time to time there are new updates available.
* Update the package-list
* Download and install the installed packages
```bash
sudo apt-get update
sudo apt-get upgrade
```


