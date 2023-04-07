Microscope entries are used to allow connection between SmartScope and SerialEM.

![Add scope](/assets/add_scope.png)

## General

* **Name:** Should be however your facility calls the microscope. i.e. Arctica, Krios-1
* **Location:** Usually the name of the center. i.e. NIEHS

## Hardware constants

* **Voltage:** Microscope Voltage on kV
* **Spherical abberation:** Microscope spherical abberation
* **Loader Size:** For Autloader microscopes, the value should be 12. Side entry should be 1. If you have a JOEL scope and cannot run a LoadCartridge command from SerialEM, it should be set to 1

## Smartscope Worker


* **Worker Hostname:** Should remain localhost unless SmartScope is set up as a master-worker configuration. *More details soon*
* **Executable:** Should remain smartscope.py unless SmartScope is set up as a master-worker configuration. *More details soon* 

## SerialEM external python connection

!!! tip

    Use the same IP and PORT that was used for testing the connection in the (previous step)[external_python.md]

* **Serialem IP:** IP of the SerialEM computer. 
* **Serialem PORT:** Port of the serialEM python socket. default is 48888.

## Filesystem Paths

!!! warning

    Please make sure that this path is writable by both SerialEM and SmartScope.

These two paths should be pointing to the same directory. One is for SerialEM to save the files in the windows computer. The other is for SmartScope to find the files saved by SerialEM.

* **Windows path:** Path of the directory where SerialEM will save the files, viewed from the SerialEM PC
* **Scope path:** Path of the directory where SerialEM will save the files, viewed from the SmartScope container.

!!! example

    Let's say the data is going to be saved in `X:\\smartscope` and the `X:\\` drive is mounted to the linux computer at `/mnt/gatan_RaidX/`. 

    Also, let's assume that the `/mnt/gatan_RaidX/:/mnt/krios/` bind was set up in the volumes of the smartscope service in the `docker-compose.yaml`. 

    In that case, `X:\\smartscope` is equivalent to `/mnt/krios/smartscope` in the smartscope container.

    Then, the microscope `Windows path= X:\\smartscope` and `Scope path= /mnt/krios/smartscope`
