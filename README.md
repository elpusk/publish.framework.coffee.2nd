# publish.framework.coffee.2nd
coffee framework second edition

- Currently, coffee-manager-2nd v2.10 is a version supports
  + the Magnetic strip reading(MSR) function of lpu237. ( exclusive open - single process only can use this functionality at the same time )
  + i-button reading function of lpu237.( shared open - multi process can use this functionality at the same time )
  + This functional limitation is related to OPOS functionality.
  + lpu237 firmware update utility.(lpu230_update)
  + After installing this program, you can use [Web Mapper](https://elpusk.github.io/library.js.coffee.2nd/) or [Web Mapper 2nd](https://elpusk.github.io/library.js.coffee.2nd/).
  + Recover device from hidbootloader with [Web Mapper 2nd](https://elpusk.github.io/library.js.coffee.2nd/)

- [Debian Installer](/installer/debian12/coffee-manager-2nd_2.10_amd64.deb)
- [Windows 11 Installer for x64](/installer/win11/coffee_manager_2nd_x64.msi)
- [Windows 11 Installer for x86](/installer/win11/coffee_manager_2nd_x86.msi)

- **Very Important Note**
  + Before using the liblpu237_dll.so(.dll) or liblpu237_ibutton.so(.dll) file, the lpu237 interface must be set to **"USB HID vendor"** mode.
  + After installaion, you can change lpu237 interface on [web mapper](https://elpusk.github.io/library.js.coffee.2nd/app/webmapper/) <- Use google-chrome brower.
  + for changing interface, use [the setting](https://github.com/elpusk/library.js.coffee/blob/master/lpu237_data/lp237_set_hid_only.xml) file.

- Installed Components( installer v2.10 )
  + coffee-service.exe : v2.1 : service program for Windows
  + elpusk-hid-d(elpusk-hid-d.exe) : v2.9 : Daemon program.
  + liblpu237_dll.so(lpu237_dll.dll) : v6.1 :MSR SO library for using elpusk-hid-d.
  + liblpu237_ibutton.so(lpu237_ibutton.dll) : v6.1 :i-button SO library for using elpusk-hid-d.
  + libdev_lib.so(dev_lib.dll) : v1.1 : device io library. this is used by elpusk-hid-d and lpu230_update internally.
  + lpu230_update(lpu230_update.exe) : v2.7 : lpu230 firmware update utility.
  + libtg_rom.so(tg_rom.dll) : v1.2 : rom file control library.
 
- Installation Method  
  __*Warning: All web browsers must be closed before installation.*__
  - Debian12
    + If you don't use the google-chrome brower, it must be installed before installating coffee-manager-2nd_2.10_amd64.deb.
    + Before installation, install libnss3-tools.(`sudo apt install libnss3-tools`)
    + sudo dpkg -i coffee-manager-2nd_2.10_amd64.deb
  - Windows11
    + run coffee_manager_2nd_x64.msi( for 64 bits OS ) or coffee_manager_2nd_x86.msi( for 32 bits OS )

- Removal Method
  + sudo dpkg -P coffee-manager-2nd or
  + sudo dpkg -r coffee-manager-2nd

- Update Method
  + remove old version : `sudo dpkg -P coffee-manager-2nd`
  + install new version : `sudo dpkg -i coffee-manager-2nd_2.9_amd64.deb`

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
  + The used libraries
    - boost c++ 1.80
    - libusb 1.0
    - openssl 1.1.1s
    - nlohmann/json
    - ftxui 6.1.9
  + lpu237 firmware upate
    - See [Wiki](https://github.com/elpusk/publish.framework.coffee.2nd/wiki/lpu230_update)

