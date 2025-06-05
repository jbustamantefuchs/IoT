# Getting Started with MQTT on groov EPIC

## Part 1: Set Up groov EPIC

### Step 1: Connect the groov EPIC to the Network
Start by connecting your groov EPIC device to your local network.
You can use either Wi-Fi or Ethernet, depending on your setup.

<p align="center">
  <img src="https://raw.githubusercontent.com/jbustamantefuchs/IoT/main/MQTT/Groov%20Epic/IMAGES/0.jpg" alt="Siemens MQTT Image 0" width="720" height="1279">
</p>

### Step 2: Find the IP Address
Once connected, identify the IP address of your groov EPIC.
In this example, the IP address is: 192.168.20.49

<p align="center">
  <img src="https://github.com/jbustamantefuchs/IoT/blob/main/MQTT/Groov%20Epic/IMAGES/1.jpg" alt="Siemens MQTT Image 0" width="720" height="1279">
</p>

<p align="center">
  <img src="https://github.com/jbustamantefuchs/IoT/blob/main/MQTT/Groov%20Epic/IMAGES/2.jpg" alt="Siemens MQTT Image 0" width="720" height="1279">
</p>


This address allows you to access the device from your computer.
Open a web browser and enter the IP address:
http://192.168.20.49

You will be directed to the login page of the groov EPIC interface.

<p align="center">
  <img src="https://github.com/jbustamantefuchs/IoT/blob/main/MQTT/Groov%20Epic/IMAGES/3.png" alt="Siemens MQTT Image 0">
</p>

### Step 3: Log In to the groov EPIC Interface
Use the following credentials to log in:

<div align="center">
  <table>
    <tr>
      <th>Username</th>
      <th>student</th>
    </tr>
    <tr>
      <td>Password</td>
      <td>changeme</td>
    </tr>
  </table>
</div>

<p align="center">
  <img src="https://github.com/jbustamantefuchs/IoT/blob/main/MQTT/Groov%20Epic/IMAGES/4.png" alt="Siemens MQTT Image 0">
</p>


### Step 4: View the Main Menu
After logging in, you will see the groov EPIC main system menu.

<p align="center">
  <img src="https://github.com/jbustamantefuchs/IoT/blob/main/MQTT/Groov%20Epic/IMAGES/5.png" alt="Siemens MQTT Image 0">
</p>

### Step 5: Open Node-RED
From the main menu:

Select the Node-RED option.

Click on "Open Node-RED Editor".

<p align="center">
  <img src="https://github.com/jbustamantefuchs/IoT/blob/main/MQTT/Groov%20Epic/IMAGES/6.png" alt="Siemens MQTT Image 0">
</p>

<p align="center">
  <img src="https://github.com/jbustamantefuchs/IoT/blob/main/MQTT/Groov%20Epic/IMAGES/7.png" alt="Siemens MQTT Image 0">
</p>

You are now inside the Node-RED editor, ready to build and configure MQTT flows on your groov EPIC.

<p align="center">
  <img src="https://github.com/jbustamantefuchs/IoT/blob/main/MQTT/Groov%20Epic/IMAGES/a.png" alt="Siemens MQTT Image 0">
</p>

## Part 2: Building the MQTT Flow

### Step 1: Add an Inject Node
In the left sidebar, under the "input" section, locate the Inject node.

Drag it into the Node-RED workspace.

Double-click the node to configure it:

Set the Payload type to: string

Enter the Value: hello!

Click Done.

<p align="center">
  <img src="https://github.com/jbustamantefuchs/IoT/blob/main/MQTT/Groov%20Epic/IMAGES/8.png" alt="Siemens MQTT Image 0">
</p>

### Step 2: Add an MQTT Out Node
Under the "output" section, find the MQTT out node.

Drag it next to the Inject node.

Double-click the MQTT out node to configure it:

Click the pencil icon next to the Server field to add a new broker.

In the configuration window:

Server: localhost

Port: 1883

Click Add

Back in the node settings:

Set the Topic to: communication

Set QoS (Quality of Service) to: 2

Click Done.

Connect the Inject node to the MQTT out node by dragging from the gray dot.

<p align="center">
  <img src="https://github.com/jbustamantefuchs/IoT/blob/main/MQTT/Groov%20Epic/IMAGES/9.png" alt="Siemens MQTT Image 0">
</p>

<p align="center">
  <img src="https://github.com/jbustamantefuchs/IoT/blob/main/MQTT/Groov%20Epic/IMAGES/10.png" alt="Siemens MQTT Image 0">
</p>

<p align="center">
  <img src="https://github.com/jbustamantefuchs/IoT/blob/main/MQTT/Groov%20Epic/IMAGES/11.png" alt="Siemens MQTT Image 0">
</p>

<p align="center">
  <img src="https://github.com/jbustamantefuchs/IoT/blob/main/MQTT/Groov%20Epic/IMAGES/12.png" alt="Siemens MQTT Image 0">
</p>


### Step 3: Add an MQTT In Node
From the "input" section, drag an MQTT in node into the workspace.

Double-click it to configure:

Use the same broker: localhost:1883

Set the Topic to: communication

Set QoS to: 2

Click Done.

<p align="center">
  <img src="https://github.com/jbustamantefuchs/IoT/blob/main/MQTT/Groov%20Epic/IMAGES/13.png" alt="Siemens MQTT Image 0">
</p>

<p align="center">
  <img src="https://github.com/jbustamantefuchs/IoT/blob/main/MQTT/Groov%20Epic/IMAGES/14.png" alt="Siemens MQTT Image 0">
</p>

### Step 4: Add a Debug Node
Under the "output" section, find and drag a Debug node next to the MQTT in node.

Double-click it:

Make sure the Output is set to: msg.payload

Click Done.

<p align="center">
  <img src="https://github.com/jbustamantefuchs/IoT/blob/main/MQTT/Groov%20Epic/IMAGES/15.png" alt="Siemens MQTT Image 0">
</p>

Connect the MQTT in node to the Debug node.

### Step 5: Deploy the Flow
Click the red "Deploy" button in the upper-right corner to activate your flow.

<p align="center">
  <img src="https://github.com/jbustamantefuchs/IoT/blob/main/MQTT/Groov%20Epic/IMAGES/16.png" alt="Siemens MQTT Image 0">
</p>

#### Flow Overview
The Inject node manually sends a message (hello!)

The MQTT Out node publishes that message to the topic: communication

The MQTT In node subscribes to the same topic (communication)

The Debug node displays the message output in the Node-RED debug sidebar
