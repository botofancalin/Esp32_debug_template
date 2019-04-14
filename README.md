# Esp32_debug_template
A template project for debugginf esp-idf projects on VsCode

## Get the tools ##
1. Install git from https://git-scm.com/download/win
2. Clone the esp-idf v3.2 branch using command:  
 `git clone --recursive -b release/v3.2 https://github.com/espressif/esp-idf.git`
3. Add IDF_PATH and path to esp-idf\tools to system "path" environment variables 
(see https://docs.espressif.com/projects/esp-idf/en/stable/get-started-cmake/add-idf_path-to-profile.html#add-paths-to-profile-windows-cmake )
4. Install https://dl.espressif.com/dl/esp-idf-tools-setup-1.2.exe 
to get the cmake, ninja build, openocd and all other tools needed to build, flash and debug the esp32 


## Get the IDE ##
1. Install Visual Studio code from https://code.visualstudio.com/docs/?dv=win
2. Install C/C++ Intellisense, VsCode Action Buttons and Native Debug extension on VsCode
 ![image](img/VsCode_extensions.jpg)

## Set the drivers ##
1. Connect the Wrover Kit (or some other ft2232 debugger) o PC USB
2. Install the FTDI drivers from https://www.ftdichip.com/Drivers/VCP.htm
 ![image](DeviceManager1.PNG)
3. Download Zadig tool from https://zadig.akeo.ie/
4. Open Zadig Tool and go to Options->List All Devices
 ![image](img/zadig1.png)
5. Select the FT2232 channel you want to use as Jtag.
In case of Wrover-Kit, is channel 0: “Dual RS232-HS (interface 0)”, according to Wrover-Kit schematic:
 ![image](img/wrover_ft2232.PNG)


6. Select WinUSB -> Click Replace Driver  
 ![image](img/zadig2.PNG)
7. After operation completed, disconnect and reconnect the device to USB port
8. In case that other channel (channel 1 in case of wrover-kit) is not detected as com port (used by esptool for flashing),
you must enable the VCP mode on channel 1, this way:
- On device manager, right click on “USB Serial Converter B” - >Properties ->Advanced
Select “Load VCP” then click OK.
 ![image](img/vcp.PNG)

## Open the project, build, debug ##

1. Open this project in VsCode: Right click on the project folder->Open with Code
 ![image](img/OpenProject.jpg)
2. If you installed the VsCode extensions properly, you should see the command buttons on the lower bar:
 ![image](img/bar.jpg)
- You can use Py Build to build the project using Cmake
- After build, you can flash the project to target using Py Flash command
3. Start Debugging:
 !["image"](img/Esp32_win_gdb_debug.jpg)