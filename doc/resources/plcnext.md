# PLCNext Tutorials and Code
Documentation and Code for PLCNext

Versions used in this repository:
- AXC F 2152 Controller running firmware 25.0.3
- PLCNext Engineer 2025.9
- sdk version 2025.0

# Examples

|\#| Name | Description |
| ----- | ------ | ------ |
|[01](https://github.com/cmu-mfi/plcnext_tutorials/tree/main/SimpleIOReadWrite/README.md) | [SimpleIOReadWrite](https://github.com/cmu-mfi/plcnext_tutorials/tree/main/SimpleIOReadWrite/README.md) | Control the IO of the controller in a real-time cpp program | 
|[02](https://github.com/cmu-mfi/plcnext_tutorials/tree/main/NoEngineerHelloWorld/README.md) | [NoEngineerHelloWorld](https://github.com/cmu-mfi/plcnext_tutorials/tree/main/NoEngineerHelloWorld/README.md) | Create a cpp real-time program that uses logging and deploy it to the controller withouth using PLCNext Engineer | 
|[03](https://github.com/cmu-mfi/plcnext_tutorials/tree/main/RestCommunication/README.md) | [RestCommunication](https://github.com/cmu-mfi/plcnext_tutorials/tree/main/RestCommunication/README.md) | Uses a cpp real-time program to read and write IO from the controller and also makes it available to the rest interface, through which it also receives commands to set the output. | 
|[04](https://github.com/cmu-mfi/plcnext_tutorials/tree/main/MqttCommunication/README.md) | [MqttCommunication](https://github.com/cmu-mfi/plcnext_tutorials/tree/main/MqttCommunication/README.md) | Read the IO from the PLCNext starter kit, sends it over MQTT to a broker using the IIot Library by PlcNext. | 
|[05](https://github.com/cmu-mfi/plcnext_tutorials/tree/main/GrpcRemoteCommunication/README.md) | [GrpcRemoteCommunication](https://github.com/cmu-mfi/plcnext_tutorials/tree/main/GrpcRemoteCommunication/README.md) | How to read and write controller data remotely using grpc. An example using the command-line tool grpcurl and python is provided. | 
|[06](https://github.com/cmu-mfi/plcnext_tutorials/tree/main/GrpcLocalCommunication/README.md) | [GrpcLocalCommunication](https://github.com/cmu-mfi/plcnext_tutorials/tree/main/GrpcLocalCommunication/README.md) | How to read and write controller data localy using grpc running on python on the controller itself. Employs a podman container to use python. | 
|[07](https://github.com/cmu-mfi/plcnext_tutorials/tree/main/OpcUaCommunication/README.md) | [OpcUaCommunication](https://github.com/cmu-mfi/plcnext_tutorials/tree/main/OpcUaCommunication/README.md) | Read controller data remotely by connecting to the OPC UA server of the controller. An example using the program UaExpert is provided. | 
|[08](https://github.com/cmu-mfi/plcnext_tutorials/tree/main/ToasterOven/README.md) | [ToasterOven](https://github.com/cmu-mfi/plcnext_tutorials/tree/main/OpcUaCommunication/README.md) | An extensive example project utilizing ladder logic, cpp real-time programs, the rest interface, and remote grpc. | 

# General Ressources
- [PLCNext Info Center](https://www.plcnext-community.net/infocenter/about/home/)
- [CPP Tutorial](https://www.plcnext-runtime.com/ch00-00-introduction.html)
- [CPP Examples](https://github.com/PLCnext/CppExamples)
- [PLCNext How-To](https://github.com/savushkin-r-d/PLCnext-howto/tree/master)
- [PLCNext Engineer Help](https://engineer.plcnext.help/2025.0_en/_index.htm?iframe=https://engineer.plcnext.help/2025.0_de/LoggingMonitoring.htm)

## Specific Links
- [CPP Component Structure and Port Definitions](https://www.plcnext-community.net/infocenter/programming/cplusplus/icomponent_and_iprogram/)
- [CPP Data Types](https://www.plcnext-community.net/infocenter/programming/supported_elementary_data_types/)
- [Axioline User Diagnostics and Error Codes](https://www.plcnext-community.net/robohelp/infocenter/assets/docs/um_en_axl_f_sys_diag_8663_en_08.pdf)
- [PLCNex Ecosystem](https://www.rs-online.com/designspark/a-practical-introduction-to-plcnext-part-1-the-ecosystem)

## Tutorials
- [Connect to Controller in Windows](https://www.realpars.com/blog/plcnext-engineer)
- [Setting up PLCNext Engineer Project](https://www.realpars.com/blog/phoenix-contact-plcnext)
  - Not entirely correct, when setting up Axioline Device, the 3rd slot should be: **AXL SE SC Rev. >=00** not **AXL SE SC-A Rev. >=00**
- [Ladder Logic IO Control](https://www.realpars.com/blog/plcnext-ladder-logic)
- [How to import cpp program into PLC Engineer](https://www.youtube.com/watch?v=IUGSZzuzm-c)

# Installation & Setup on Linux
How to install all dependencies and tools necessary to work with plcnext. All the steps are valid for ubuntu linux.
## PLCNext Technology Toolchain (plcncli)
Download the right version from [here](https://www.phoenixcontact.com/en-us/products/software-package-plcnext-technology-toolchain-1639782)

Run the executable:
```sh
/bin/sh PLCnext_Toolchain_2024.6.sh
```
Press q and then y to accept the license.

Move the folder to /opt and link the file:
```sh
sudo ln -sf /opt/PLCnext_Toolchain/plcncli /usr/bin/plcncli
```
Test if plcncli is accessible:
```sh
plcncli --version
```

## PLCNext SDK (for AXC F 2125)
Download axcf2152 2025.0.3 sdk from [here](https://www.phoenixcontact.com/en-us/products/controller-axc-f-2152-2404267) (Pick the right version and operating system under Software)

Navigate to where the download got saved and run:
```sh
chmod a+x axcf2152-linux_sdk-2025.0.3-25.0.3.99.sh
sudo mkdir -p 
sudo mkdir /opt/pxc/2025.0 -p
sudo chown $USER:$USER /opt/pxc/ -R
```
Install the sdk with plcncli:
```sh
plcncli install sdk --path axcf2152-linux_sdk-2025.0.3-25.0.3.99.sh -d /opt/pxc/2025.0
```
## Connect AXC F 2125 on Linux
When plugging the controller directly into the computer via ethernet while using Wifi for internet:

Find Device Name of Ethernet:
```sh
nmcli device
```
Create connection:
```sh
nmcli con add con-name "plc-con" ifname <device name> type ethernet
```
Configure connection:
```sh
nmcli con modify plc-con ipv6.method disabled
nmcli con modify plc-con ipv4.method shared ipv4.addresses 192.168.1.1/24
```
Enable and test connection:
```sh
nmcli con up plc-con
ping 192.168.1.10 (address of controller)
ping github.com (Check if internet works)
```

# Installation & Setup on Windows
How to install all dependencies and tools necessary to work with plcnext. All the steps are tested on Windows 11.
## Install PLCNext Engineer
Download from [here](https://www.phoenixcontact.com/en-us/products/programming-plcnext-engineer-1046008)
## Install plcncli
Download from [here](https://www.phoenixcontact.com/en-us/products/software-package-plcnext-technology-toolchain-1639782)
## Install sdk for AXC F 2152
Download axcf2152 2025.0.3 sdk from [here](https://www.phoenixcontact.com/en-us/products/controller-axc-f-2152-2404267) (Pick the right version and operating system under Software)
## Install and setup Eclipse (when working on cpp projects)
Follow instructions from [here](https://www.plcnext-community.net/infocenter/programming/cplusplus/cpp_required_installations) and [here](https://www.plcnext-community.net/infocenter/programming/cplusplus/working_with_eclipse)
## Connect AXC F 2125 on Windows
Connecting to the controller via ethernet:
 - https://www.realpars.com/blog/plcnext-engineer
 - https://www.realpars.com/blog/phoenix-contact-plcnext