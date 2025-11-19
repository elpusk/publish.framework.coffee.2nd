# publish.framework.coffee.2nd
coffee framework second edition

- Currently, coffee-manager-2nd_2.3_amd64.deb is a version supports
  + the Magnetic strip reading(MSR) function of lpu237. ( exclusive open - single process only can use this functionality at the same time )
  + i-button reading function of lpu237.( shared open - multi process can use this functionality at the same time )
  + This functional limitation is related to OPOS functionality.
  + lpu237 firmware update utility.(lpu230_update)

- [Debian Installer](/installer/debian12/coffee-manager-2nd_2.3_amd64.deb)

- **Very Important Note**
  + Before using the liblpu237_dll.so or liblpu237_ibutton.so file, the lpu237 interface must be set to **"USB HID vendor"** mode.
  + After installaion, you can change lpu237 interface on [web mapper](https://elpusk.github.io/library.js.coffee/tools_lpu237_full.html) <- Use google-chrome brower.
  + for changing interface, use [the setting](https://github.com/elpusk/library.js.coffee/blob/master/lpu237_data/lp237_set_hid_only.xml) file.

- Installed Components( pkg v2.3 )
  + elpusk-hid-d : v2.3 : Daemon program.
  + liblpu237_dll.so : v6.0 :MSR SO library for using elpusk-hid-d.
  + liblpu237_ibutton.so : v6.0 :i-button SO library for using elpusk-hid-d.
  + libdev_lib.so : v1.0 : device io library. this is used by elpusk-hid-d internally.
  + lpu230_update : v2.2 : lpu230 firmware update utility.
  + dev_lib.so : v1.0 : HID device io library(used by elpusk-hid-d and lpu230_update ).
 
- Installation Method
  + If you don't use the google-chrome brower, it must be installed before installating coffee-manager-2nd_2.3_amd64.deb.
  + Before installation, install libnss3-tools.(`sudo apt install libnss3-tools`)
  + sudo dpkg -i coffee-manager-2nd_2.3_amd64.deb

- Removal Method
  + sudo dpkg -P coffee-manager-2nd or
  + sudo dpkg -r coffee-manager-2nd

- Update Method
  + remove old version : `sudo dpkg -P coffee-manager-2nd`
  + install new version : `sudo dpkg -i coffee-manager-2nd_2.3_amd64.deb`

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

