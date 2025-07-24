# Getting Started with MQTT on groov EPIC

## Part 1: Set Up groov EPIC

### Step 1: Connect the groov EPIC to the Network
Start by connecting your groov EPIC device to your local network.
You can use either Wi-Fi or Ethernet, depending on your setup.

<div align="center">
  <img src="IMAGES/0.jpg" width="720" height="1279">
</div>

### Step 2: Find the IP Address
Once connected, identify the IP address of your groov EPIC.
In this example, the IP address is: ip.of.the.plc

<div align="center">
  <img src="IMAGES/1.jpg" width="720" height="1279">
</div>

<div align="center">
  <img src="IMAGES/2.jpeg" width="720" height="1279">
</div>

This address allows you to access the device from your computer.
Open a web browser and enter the IP address:
http://ip.of.the.plc

You will be directed to the login page of the groov EPIC interface.

<div align="center">
  <img src="IMAGES/3.png" >
</div>

### Step 3: Log In to the groov EPIC Interface
Use the following credentials to log in:

<div>
  <table>
    <tr>
      <th>Username</th>
      <th>EXAMPLE USERNAME</th>
    </tr>
    <tr>
      <td>Password</td>
      <td>EXAMPLE PASSWORD</td>
    </tr>
  </table>
</div>

<div align="center">
  <img src="IMAGES/4.png" >
</div>

### Step 4: View the Main Menu
After logging in, you will see the groov EPIC main system menu.

<div align="center">
  <img src="IMAGES/5.png" >
</div>

### Step 5: Open Node-RED
From the main menu:

Select the Node-RED option.

Click on "Open Node-RED Editor".

<div align="center">
  <img src="IMAGES/6.png" >
</div>

You are now inside the Node-RED editor, ready to build and configure MQTT flows on your groov EPIC.

<div align="center">
  <img src="IMAGES/a.png" >
</div>

## Part 2: Building the MQTT Flow

### Step 1: Add an Inject Node
In the left sidebar, under the "input" section, locate the Inject node.

Drag it into the Node-RED workspace.

Double-click the node to configure it:

Set the Payload type to: string

Enter the Value: hello!

Click Done.

<div align="center">
  <img src="IMAGES/7.png" >
</div>

### Step 2: Add an MQTT Out Node
Under the "output" section, find the MQTT out node.

Drag it next to the Inject node.

Double-click the MQTT out node to configure it:

<div align="center">
  <img src="IMAGES/8.png" >
</div>

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

<div align="center">
  <img src="IMAGES/9.png" >
</div>

<div align="center">
  <img src="IMAGES/10.png" >
</div>

<div align="center">
  <img src="IMAGES/11.png" >
</div>

<div align="center">
  <img src="IMAGES/12.png" >
</div>

### Step 3: Add an MQTT In Node
From the "input" section, drag an MQTT in node into the workspace.

Double-click it to configure:

Use the same broker: localhost:1883

Set the Topic to: communication

Set QoS to: 2

Click Done.

<div align="center">
  <img src="IMAGES/13.png" >
</div>


### Step 4: Add a Debug Node
Under the "output" section, find and drag a Debug node next to the MQTT in node.

Double-click it:

Make sure the Output is set to: msg.payload

Click Done.

<div align="center">
  <img src="IMAGES/14.png" >
</div>

Connect the MQTT in node to the Debug node.

<div align="center">
  <img src="IMAGES/15.png" >
</div>

### Step 5: Deploy the Flow
Click the red "Deploy" button in the upper-right corner to activate your flow.

<div align="center">
  <img src="IMAGES/16.png" >
</div>

#### Flow Overview
The Inject node manually sends a message (hello!)

The MQTT Out node publishes that message to the topic: communication

The MQTT In node subscribes to the same topic (communication)

The Debug node displays the message output in the Node-RED debug sidebar
