# dbus-serialbattery
This is a driver for VenusOS devices (any GX device sold by Victron or a Raspberry Pi running the VenusOS image). 

The driver will communicate with a Battery Management System (BMS) that support serial communication (RS232 or RS485) 
and publish this data to the dbus used by VenusOS. The main purpose is to supply up to date State Of Charge (SOC) values
to the inverter, but many extra parameters is also published if available from the BMS.

Driver support:
 * Smart BMS range from [LLT Power](https://www.lithiumbatterypcb.com/product-instructionev-battery-pcb-boardev-battery-pcb-board/ev-battery-pcb-board/smart-bms-of-power-battery/) 
(Cell values are currently only supported for the first 16 cells: Min Cell V, Max Cell V, Cell Balance) 

Planned support:
 * AntBMS
 * Smart Daly BMS 

### How to install
1. You need to have a VenusOS device set up and running on your system and have [root access](https://www.victronenergy.com/live/ccgx:root_access).
2. You also need to connect your BMS to the VenusOS device using a serial interface. A USB->232 converter like the FT232R. The FT232R already has a driver included in the VenusOS.
3. Use a FTP client that support SFTP to copy the driver files to the rooted VenusOS device. [Filezilla](https://filezilla-project.org/) is a good option
   - copy the dbus-serialbattery folder to `/data/etc/`
   - copy or move rc.local to `/data/`
   - copy or move serial-starter.d to `/data/conf/`
   - reboot your VenusOS device and check if your battery is connected