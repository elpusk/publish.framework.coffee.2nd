# publish.framework.coffee.2nd
coffee framework second edition

- Currently, coffee-manager-2nd v2.13 is a version supports
  + the Magnetic strip reading(MSR) function of lpu237. ( exclusive open - single process only can use this functionality at the same time )
  + i-button reading function of lpu237.( shared open - multi process can use this functionality at the same time )
  + This functional limitation is related to OPOS functionality.
  + lpu237 firmware update utility.(lpu230_update)
  + After installing this program, you can use [Web Mapper 2nd](https://elpusk.github.io/library.js.coffee.2nd/app/webmapper/).
  + Recover device from hidbootloader with [Web Mapper 2nd](https://elpusk.github.io/library.js.coffee.2nd/app/webmapper/)
  + For lpu237 magnetic card reading & i-button reading, MCP Server of Claude & Cursor(local only, Claude - Only Windows)

- [Debian Installer](/installer/debian12/coffee-manager-2nd_2.13_amd64.deb)
- [Windows 11 Installer for x64](/installer/win11/coffee_manager_2nd_x64.msi)
- [Windows 11 Installer for x86](/installer/win11/coffee_manager_2nd_x86.msi)

- **Very Important Note**
  + Before installing this package, **YOU MUST TERMINATE ALL WEB BROWERS.**
  + Before using the libtg_lpu237_dll.so(tg_lpu237_dll.dll) ,libtg_lpu237_ibutton.so(tg_lpu237_ibutton.dll) or libtg_lpu237_fw.so(tg_lpu237_fw.dll) file, the lpu237 interface must be set to **"USB HID vendor"** mode.
  + After installaion, you can change lpu237 interface on [web mapper 2nd](https://elpusk.github.io/library.js.coffee.2nd/app/webmapper/) <- Use google-chrome brower.
  + for changing interface, use [the setting](https://github.com/elpusk/library.js.coffee/blob/master/lpu237_data/lp237_set_hid_only.xml) file.

- Installed Components( installer v2.13 )
  + coffee-service.exe : v2.2 : service program for Windows
  + elpusk-hid-d(elpusk-hid-d.exe) : v2.12 : Daemon program.
  + libtg_lpu237_dll.so(tg_lpu237_dll.dll) : v6.3 : MSR SO library for using elpusk-hid-d.
  + libtg_lpu237_ibutton.so(tg_lpu237_ibutton.dll) : v6.3 : i-button SO library for using elpusk-hid-d.
  + libtg_lpu237_fw.so(tg_lpu237_fw.dll) : v6.3 : firmware update SO library for using elpusk-hid-d.
  + libdev_lib.so(dev_lib.dll) : v1.3 : device io library. this is used by elpusk-hid-d and lpu230_update internally.
  + lpu230_update(lpu230_update.exe) : v2.9 : lpu230 firmware update utility.
  + libtg_rom.so(tg_rom.dll) : v1.4 : rom file control library.
  + lpu23x-ibutton-mcp(lpu23x-ibutton-mcp.exe) : v1.1 : lpu237 magnetic card reading MCP server.
  + lpu23x-msr-mcp(lpu23x-msr-mcp.exe) : v1.1 : lpu237 i-button reading MCP server. 
 
- Installation Method  
  __*Warning: All web browsers must be closed before installation.*__
  - Debian12
    + If you don't use the google-chrome brower, it must be installed before installating coffee-manager-2nd_2.13_amd64.deb.
    + Before installation, install libnss3-tools.(`sudo apt install libnss3-tools`)
    + sudo dpkg -i coffee-manager-2nd_2.13_amd64.deb
  - Windows11
    + run coffee_manager_2nd_x64.msi( for 64 bits OS ) or coffee_manager_2nd_x86.msi( for 32 bits OS )
  - MCP Server( Only x64, Only manual installation ) 
    - Terminates Claude Desktop anf Cursor.
    - Windows Claude Desktop : open C:\Users\your-account\AppData\Roaming\Claude\claude_desktop_config.json
    - Windows Cursor : open  C:\Users\your-account\ .cursor\mcp.json
    - Debian12 Cursor : open  ~/.cursor/mcp.json
    - Please add the following content to claude_desktop_config.json or mcp.json file.

``` json
FOR WINDOWS
{
  ...
  "mcpServers":{
    "msr-mcp": {
    "command": "C:\\Program Files\\elpusk\\00000006\\coffee_manager\\mcp\\lpu23x-msr-mcp"
    },
    "ibutton-mcp": {
    "command": "C:\\Program Files\\elpusk\\00000006\\coffee_manager\\mcp\\lpu23x-ibutton-mcp"
    }
  }
  ...
}

FOR DEBIAN12
{
  ...
  "mcpServers":{
    "msr-mcp": {
    "command": "/usr/share/elpusk/program/00000006/coffee_manager/mcp/lpu23x-msr-mcp"
    },
    "ibutton-mcp": {
    "command": "/usr/share/elpusk/program/00000006/coffee_manager/mcp/lpu23x-ibutton-mcp"
    }
  }
  ...
}
```

- Removal Method
  + sudo dpkg -P coffee-manager-2nd or
  + sudo dpkg -r coffee-manager-2nd

- Update Method
  + remove old version : `sudo dpkg -P coffee-manager-2nd`
  + install new version : `sudo dpkg -i coffee-manager-2nd_2.13_amd64.deb`

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
    - [header file for udpating firmware](/code/inc/tg_lpu237_fw.h)
  + The used libraries
    - boost c++ 1.80
    - libusb 1.0
    - openssl 1.1.1s
    - nlohmann/json
    - ftxui 6.1.9
  + lpu237 firmware upate
    - See [Wiki](https://github.com/elpusk/publish.framework.coffee.2nd/wiki/lpu230_update)

