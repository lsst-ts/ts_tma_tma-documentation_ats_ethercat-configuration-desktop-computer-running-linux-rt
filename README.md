# EtherCat in Normal PC with Linux RT

First of all, the system must have card compatible with the I210 (igb) driver from Intel.

Then install the Ni Industrial Communications for EtherCAT using the NI MAX.

Edit the /etc/natinst/share/ni-rt.ini to add the section following section:

```ini
[<ethercatNetworkInterfaceName>]
Mode=EtherCAT
MasterID=1
```

After doing this, the file should look as follows for ethercatNetworkInterfaceName `enp2s0`:

```shell

admin@ATS-TMA-PXI:~# cat /etc/natinst/share/ni-rt.ini
[systemsettings]
PrimaryMAC="64006A8F8E69"
host_name="ATS-TMA-PXI"
safemode.enabled="False"
NoFPGAApp.enabled="False"
NoApp.enabled="False"
sshd.enabled="True"
ui.enabled="False"
ConsoleOut.enabled="False"



[enp0s31f6]
dhcpipaddr="10.1.22.189"


[LVRT]
RTTarget.RTProtocolAllowed="True"
AdditionalNetworkProtocols="EtherCAT"
[RtLinuxMemReserve]
Base=24


[SupportedWirelessSecurityTypes]
WPA_PSK="true"
WPA_EAP="true"
WEP="true"
Open="true"
WPA2_EAP="true"
WPA2_PSK="true"


[Supported Locales]
english="L1"


[NVE]
MessageQueueUpperBound="1000000"


[enp2s0]
Mode=EtherCAT
MasterID=1
admin@ATS-TMA-PXI:~#

```
