# publish.framework.coffee.2nd
coffee framework second edition

- Currently, coffee-manager-2nd_2.0~beta1_amd64.deb is a version tested only for the Magnetic strip reading function of lpu237.
- [Debian Installer](/installer/debian12/coffee-manager-2nd_2.0~beta1_amd64.deb)

- Installed Components
  + elpusk-hid-d : Daemon program.(2.0~beta1)
  + liblpu237_dll.so : SO library for using elpusk-hid-d.
 

- Installation Method
  + sudo dpkg -i coffee-manager-2nd_2.0_amd64.deb

- Removal Method
  + sudo dpkg -P coffee-manager-2nd_2.0_amd64.deb or
  + sudo dpkg -r coffee-manager-2nd_2.0_amd64.deb

- Manual Removal : In case of installation or removal errors.
  + dpkg database backup : `sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.bak`
  + dpkg database manual cleanup : `sudo nano /var/lib/dpkg/status`
  + Delete all usr/share/elpusk directory.
  + Delete all var/log/elpusk directory.