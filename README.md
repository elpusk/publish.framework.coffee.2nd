# publish.framework.coffee.2nd
coffee framework second edition

- Currently, coffee-manager-2nd_2.0_amd64.deb is a version supports
  + the Magnetic strip reading(MSR) function of lpu237. ( exclusive open - single process only can use this functionality at the same time )
  + i-button reading function of lpu237.( shared open - multi process can use this functionality at the same time )
  + This functional limitation is related to OPOS functionality.

- [Debian Installer](/installer/debian12/coffee-manager-2nd_2.0_amd64.deb)

- Installed Components
  + elpusk-hid-d : Daemon program.(2.0)
  + liblpu237_dll.so : MSR SO library for using elpusk-hid-d.
  + liblpu237_ibutton.so : i-button SO library for using elpusk-hid-d.
  + libdev_lib.so : device io library. this is used by elpusk-hid-d internally.
 
- Installation Method
  + sudo dpkg -i coffee-manager-2nd_2.0_amd64.deb

- Removal Method
  + sudo dpkg -P coffee-manager-2nd or
  + sudo dpkg -r coffee-manager-2nd

- Update Method
  + remove old version : `sudo dpkg -P coffee-manager-2nd`
  + install new version : `sudo dpkg -i coffee-manager-2nd_2.0_amd64.deb`

- Manual Removal : In case of installation or removal errors.
  + dpkg database backup : `sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.bak`
  + dpkg database manual cleanup : `sudo nano /var/lib/dpkg/status` and remove "Packge: coffee-manager-2nd" part.
  + Delete all usr/share/elpusk directory.
  + Delete all var/log/elpusk directory.

- Informations
  + See [Wiki](https://github.com/elpusk/publish.framework.coffee.2nd/wiki)
  + Problems See [issues tab](https://github.com/elpusk/publish.framework.coffee.2nd/issues)
  + test code
    - C++ 17.
    - lpu237 device msr, i-button reading test.
    - [test project main function](/code/test/tp_lpu237_dll/tp_main.cpp)
    - [header file for msr reading](/code/inc/tg_lpu237_dll.h)
    - [header file for i-button reading](/code/inc/tg_lpu237_ibutton.h)