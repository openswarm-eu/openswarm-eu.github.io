# AIOT Zephyr Application which uses Memfault for Performance Monitoring

<Button label="🔗 Repository for the developed AIOT Zephyr APM module" link="https://github.com/openswarm-eu/aiot_play_fw_zephyr" block /><br />

## Project information

In this project we present an Application Performance Monitoring (APM) framework for the AIOT Board.
Therefore, we implement a sample Zepyhr application which uses Memfault.
The application periodically sends out "Memfault chunks" via the SmartMesh IP chip.
These chunks arrive at the SmartMesh IP manager, which is connected to an Edge Device, from where they are posted to the Memfault cloud.
This README file will guide through the following steps:
- Setup nRF Connect SDK (NCS) and nrfjprog
- Clone Repository and Import into NCS
- Connect and Program AIOT
- AIOT Network Joining Process
- Applications on the Edge Device
- Observe incoming Memfault Chunks at Memfault Cloud

![image](./img/0-1.png)


## Setup nRF Connect SDK (NCS) and nrfjprog

### NCS
The nRF Connect SDK (NCS) can be downloaded at:
https://developer.nordicsemi.com/nRF_Connect_SDK/doc/latest/nrf/installation/assistant.html

The NCS is available as VS Code extension after installation.
Thus, the version of the NCS, toolchains and Zephyr can be updated inside VS code.

![image](./img/1-1.jpg)

### nrfjprog
The nRF Command Line Tools can be downloaded at:
https://www.nordicsemi.com/Products/Development-tools/nrf-command-line-tools/download

If using the build, flash and debug functions of the NCS, check if the nrfjprog command line tool is installed by typing the command in your terminal:

```
nrfjprog -v
```

**Note**: In this tutorial we used:
- NCS version v.2.3.0 and Toolchain version v.2.3.0
- Command Line Tool versions:
```
nrfjprog -v
>> nrfjprog version: 10.21.0 external
>> JLinkARM.dll version: 7.80
```



## Clone Repository and Import into NCS

Clone Repository:
```
git clone --recurse-submodules git@github.com:aiotsystems/aiot_play_fw_zephyr.git
```

Import in NCS:

![image](./img/2-1.jpg)

Create Build Configuration:

![image](./img/2-2.jpg)

The FW is then built in:

![image](./img/2-3.jpg)


## Connect and Program AIOT

### Setup
The nRF52833 on the AIOT can be programmed via the nRF JTAG connector.
To program the AIOT, a 10 pin IDC ARM JTag cable needs to be connected to a JLink debugger.
Therefore one can use a classical JLink HW debugger in combination with a 20-10 converter PCB or one can simply use another nRFXX-DK with on-board J-LINK debugger and connect to the Debug Out Connector.
![image](./img/3-1.jpg)

After plugging batteries into the AIOT and connecting the debugger to the PC, the AIOT should appear in the NCS under Connected Devices:

![image](./img/3-2.jpg)

### Program

Although, we have used the provided overlay file for the build configuration, check if the UART Pins appear correctly in the Device tree:

![image](./img/3-3.jpg)


In the prj.conf file, paste the Memfault Cloud project key:

![image](./img/3-4.jpg)

### Re-Build and Flash

![image](./img/3-5.jpg)



## AIOT Network Joining Process

Plug-in the Manager into your computer and connect to serial CLI (thrid COM-Port in Windows).
Trouble finding out, which API port corresponds to manager serial API? Check 
out chapter 3.1 of:
https://www.analog.com/media/en/technical-documentation/user-guides/SmartMesh_IP_Tools_Guide.pdf

![image](./img/4-1.jpg)

Then login to the serial API by typing:
```
login user
```
Then you can watch the AIOT network join Process by iteratively issueing the show mote command:
```
sm
```
Finally the AIOT will appear in Operating (Oper) state.
![image](./img/4-2.jpg)


## Applications on the Edge Device

At the Edge Device we receive the heartbeats and push them to the Memfault Cloud.

### JsonServer

The SmartMesh IP Manager is connected via USB to the Edge Device.
JsonServer is a command-line tool that turns the SmartMesh IP Manager serial API into an JSON-based HTTP API.
It is publicly available on Github:
https://github.com/dustcloud/smartmeshsdk/tree/master/app/JsonServer


For more details, refer to: https://dustcloud.atlassian.net/wiki/spaces/SMSDK/pages/95125618/JsonServer 
First clone the Smart Mesh SDK (SMSDK) repository from Github:
```
git clone git@github.com:dustcloud/smartmeshsdk.git
```
Create a new virtual environment environment, install the requirements and start the JSonServer.py script.

Then connect the JSonServer to the manager's serial API (thourth COM-Port in Windows).
```
>> conda create --name SMSDK python=3.11
>> conda activate SMSDK
>> pip install -r requirements.txt
>> python JSonServer.py
JsonServer - (c) Analog Devices, Dust Networks products
  running versions:
    - SmartMesh SDK: 1.4.0.1
> sp
{   'serialports': [   'COM7',
                       'COM12',
                       'COM13',
                       'COM14',
                       'COM15']}
> cm COM15
> s
{   'SmartMesh SDK version': '1.4.0.1',
    'current time': '02/21/2023 11:06:48',
    'managers': {'COM15': 'connected'},
    'running since': '02/21/2023 11:06:27 (0:00:21.193483 ago)',
    'threads running': [   'MainThread',
                           'SnapshotThread',
                           'ManagerHandler@COM15',
                           'DustCli',
                           'WebServer',
                           'COM15_HDLC',
                           'IpMgrSubscribe']}
```


### Node-RED (optional)
In this tutorial, we do not build up on Node-RED but can use it for debugging purposes.
Thus, this section is optional.
Node-RED is a flow-based programming tool for wiring together hardware devices, APIs
and online services.
Node-RED can be either be installed via node-js:
https://nodejs.org/en
by using the Node Package Manager (npm):
```
npm install -g --unsafe-perm node-red
```
Then start Node-RED at port 1880 by typing:
```
node-red
```
Alternatively, Node-RED can be run as a Docker container via the command:
```
docker run -it -p 1880:1880 -v node_red_data:/data --name mynodered nodered/node-red
```
When opening http://127.0.0.1:1880/ one can create two flows and observe the corresponding incoming messages from the JSonServer:
1. Create a flow based on an "http in"-node. Choose the POST method and "/notifData" as URL.
2. Create a flow based on an "http in"-node. Choose the POST method and "/event" as URL.
3. The debug output of the event node shows the joining process of the AIOT.
4. The debug output of the notifData node shows the Memfault chunks generated by the AIOT.

![image](./img/6-1.jpg)

### Memfault CLI

The Memfault CLI is a Python package offering different kinds of interaction with the Memfault cloud via the command line.
In this repository there is a Python script called **smip_to_memfault_exporter.py** in the python folder.
The script listens to HTTP port 1880, grabs the Memfault chunks and pushes to Memfault Cloud via the Memfault CLI.
To run the script, install Python 3.9 and the Memfault CLI.

#### Windows
By using for example anaconda: 
```
conda create --name smip-to_memfault python=3.9
conda activate smip-to_memfault
pip3 install memfault-cli
```

#### Linux
By using for example venv: 
```
python -m venv smip_to_memfault_venv
source smip_to_memfault_venv/bin/activate
pip3 install memfault-cli
```

Before you run the script, insert the project_key from the Memfault cloud into smip_to_memfault_exporter.py:
```
project_key = "***************************"
```

## Observe incoming Memfault Chunks at Memfault Cloud

At the Memfault cloud, you need to provide the *zephyr.elf* FW file in the symbol section.
This can either be done via the Memfault CLI or by hand.
![image](./img/7-1.jpg)

When the AIOT has joined the network and the JSONServer.py and smip_to_memfault_exporter.py are running on the Edge Device, then you can observe the reported values for the testMetric in the Zephyr application in the Memfault cloud.
![image](./img/7-2.jpg)



## License and Copyright

The project is under BSD-3 License (https://spdx.org/licenses/BSD-3-Clause-Clear.html).

Copyrights and Sources are stated in the Comment Header of each file.

Collection of used sources in this project:
| Code Source   | Owner | URL |
|----------|----------|----------|
| aiot_play_fw    | INRIA  | https://github.com/aiotsystems/aiot_play_fw.git   |
| sm_clib    | Dust Networks  | https://github.com/dustcloud/sm_clib   |
| Memfault Packetizer   | Memfault   | https://docs.memfault.com/docs/mcu/data-from-firmware-to-the-cloud/  |

