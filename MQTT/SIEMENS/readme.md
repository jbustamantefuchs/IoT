# Siemens MQTT

Step-by-step guide to implementing **MQTT** communication on **Siemens** devices using **TIA Portal** and the `LMQTT_Client` library.

## Part 1: Create a Siemens account

1.  Go to: 👉 [https://support.industry.siemens.com](https://support.industry.siemens.com/)
2.  In the top-right corner, click **“Register”**.
3.  Fill in your details (name, email, country, etc.).
4.  Check your email to confirm the registration.
5.  Log in to the portal using your new account.

<p align="center">
  <img src="https://raw.githubusercontent.com/jbustamantefuchs/IoT/main/MQTT/SIEMENS/IMAGES/0.png" alt="Siemens MQTT Image 0">
</p>

---

## Part 2: Download the communication library

1.  Visit the official Siemens support page for the communication libraries:

    https://support.industry.siemens.com/cs/document/109780503
2.  Scroll down to the **“Download”** section.
3.  Select the appropriate version for your installed TIA Portal
4.  Click the **download icon**.
5.  Accept the license terms if prompted.
6.  Download and unzip the archive on your computer.

<p align="center">
  <img src="https://raw.githubusercontent.com/jbustamantefuchs/IoT/main/MQTT/SIEMENS/IMAGES/1.png" alt="Siemens MQTT Image 0">
</p>
<p align="center">
  <img src="https://raw.githubusercontent.com/jbustamantefuchs/IoT/main/MQTT/SIEMENS/IMAGES/2.png" alt="Siemens MQTT Image 0">
</p>

---

## Part 3: Import the library into TIA Portal

1.  Open your project in **TIA Portal**.
2.  Go to the **“Project Library”** panel.
3.  Right-click and select: **Manage libraries** → **Open library**.
4.  Browse for the `.al#` file you downloaded. (# represents the version of Tia in use)
5.  The library will open as a **Global Library**.
6.  From there, you can drag and drop function blocks, data types, and other components into your project.

<p align="center">
  <img src="https://raw.githubusercontent.com/jbustamantefuchs/IoT/main/MQTT/SIEMENS/IMAGES/3.png" alt="Siemens MQTT Image 0">
</p>
<p align="center">
  <img src="https://raw.githubusercontent.com/jbustamantefuchs/IoT/main/MQTT/SIEMENS/IMAGES/4.png" alt="Siemens MQTT Image 0">
</p>
<p align="center">
  <img src="https://raw.githubusercontent.com/jbustamantefuchs/IoT/main/MQTT/SIEMENS/IMAGES/5.png" alt="Siemens MQTT Image 0">
</p>
<p align="center">
  <img src="https://raw.githubusercontent.com/jbustamantefuchs/IoT/main/MQTT/SIEMENS/IMAGES/6.png" alt="Siemens MQTT Image 0">
</p>

---

## Part 4: Set-Up **LMQTT\_Client FB**

### a) Add the LMQTT\_Client FB to a Network\*

1.  Open **TIA Portal** and navigate to the program block where you want to implement MQTT communication.
2.  In an empty network, insert a new **Function Block (FB)**.
3.  Search for and select: `LMQTT_Client`.
4.  When prompted, create an associated Data Block for the FB.
5.  Accept the default name: `LMQTT_Client_DB`.

<p align="center">
  <img src="https://raw.githubusercontent.com/jbustamantefuchs/IoT/main/MQTT/SIEMENS/IMAGES/7.png" alt="Siemens MQTT Image 0">
</p>
<p align="center">
  <img src="https://raw.githubusercontent.com/jbustamantefuchs/IoT/main/MQTT/SIEMENS/IMAGES/8.png" alt="Siemens MQTT Image 0">
</p>

---

### b) Create a New Data Block for Parameters

1.  Go to **Program blocks** → right-click → **Add new block**.
2.  Choose **Data Block**.
3.  Name it as desired (e.g., Data\_block\_MQTT).

<p align="center">
  <img src="https://raw.githubusercontent.com/jbustamantefuchs/IoT/main/MQTT/SIEMENS/IMAGES/9.png" alt="Siemens MQTT Image 0">
</p>

---

### c) Open the Data Block and add the following variables:

FULL TAGS:

<div align="center">
  <table>
    <tr>
      <th>Alias</th>
      <th>Type</th>
    </tr>
    <tr>
      <td>enable</td>
      <td>Bool</td>
    </tr>
    <tr>
      <td>publish</td>
      <td>Bool</td>
    </tr>
    <tr>
      <td>subscribe</td>
      <td>Bool</td>
    </tr>
    <tr>
      <td>unsubscribe</td>
      <td>Bool</td>
    </tr>
    <tr>
      <td>qos</td>
      <td>USInt</td>
    </tr>
    <tr>
      <td>retain</td>
      <td>Bool</td>
    </tr>
    <tr>
      <td>publishMsgLen</td>
      <td>100</td>
    </tr>
    <tr>
      <td>willMsgLen</td>
      <td>100</td>
    </tr>
    <tr>
      <td>connParam</td>
      <td>"LMQTT_typeConnParam"</td>
    </tr>
    <tr>
      <td>clientID</td>
      <td>WString</td>
    </tr>
    <tr>
      <td>username</td>
      <td>WString</td>
    </tr>
    <tr>
      <td>password</td>
      <td>WString</td>
    </tr>
    <tr>
      <td>willtopic</td>
      <td>WString</td>
    </tr>
    <tr>
      <td>willMsgPayload</td>
      <td>Array[0..99] of Byte</td>
    </tr>
    <tr>
      <td>mqttTopic</td>
      <td>WString</td>
    </tr>
    <tr>
      <td>publishMsgPayload</td>
      <td>Array[0..99] of Byte</td>
    </tr>
    <tr>
      <td>receivedTopic</td>
      <td>WString</td>
    </tr>
    <tr>
      <td>receivedMsgPayload</td>
      <td>Array[0..99] of Byte</td>
    </tr>
    <tr>
      <td>valid</td>
      <td>Bool</td>
    </tr>
    <tr>
      <td>done</td>
      <td>Bool</td>
    </tr>
    <tr>
      <td>busy</td>
      <td>Bool</td>
    </tr>
    <tr>
      <td>error</td>
      <td>Bool</td>
    </tr>
    <tr>
      <td>status</td>
      <td>Word</td>
    </tr>
    <tr>
      <td>diagnostics</td>
      <td>"typeDiagnostics"</td>
    </tr>
    <tr>
      <td>receivedMsgStatus</td>
      <td>USInt</td>
    </tr>
    <tr>
      <td>receivedMsgDataLen</td>
      <td>UDint</td>
    </tr>
  </table>
</div>

<p align="center">
  <img src="https://raw.githubusercontent.com/jbustamantefuchs/IoT/main/MQTT/SIEMENS/IMAGES/10.png" alt="Siemens MQTT Image 0">
</p>

---

### d) Set up the variables values as:

QoS = 1 (publishing accepts 2 but subscribing only 1)

Retain = 1

willMsgLen=100

mqttTopic=test ( feel free to use other topic)

### e) Now, on connParam, set up the ip and the port of our broker

<p align="center">
  <img src="https://raw.githubusercontent.com/jbustamantefuchs/IoT/main/MQTT/SIEMENS/IMAGES/11.png" alt="Siemens MQTT Image 0">
</p>

---

## Part 5: Link the Variables to the FB

1.  Return to the network where the `LMQTT_Client` FB is located.
2.  Connect each FB parameter to the corresponding variable in the `Block_IoT_MQTT`.
3.  Ensure proper assignment:

<p align="center">
  <img src="https://raw.githubusercontent.com/jbustamantefuchs/IoT/main/MQTT/SIEMENS/IMAGES/12.png" alt="Siemens MQTT Image 0">
</p>
<p align="center">
  <img src="https://raw.githubusercontent.com/jbustamantefuchs/IoT/main/MQTT/SIEMENS/IMAGES/13.png" alt="Siemens MQTT Image 0">
</p>

#### **Recommendation**

For detailed information about each parameter's behavior, refer to the official documentation provided by Siemens on the download page for the **LMQTT\_Client** library.

---

## Part 6: Create a Watch and Force tables

<p align="center">
  <img src="https://raw.githubusercontent.com/jbustamantefuchs/IoT/main/MQTT/SIEMENS/IMAGES/14.png" alt="Siemens MQTT Image 0">
</p>

Add the following variables into the Watch table

<p align="center">
  <img src="https://raw.githubusercontent.com/jbustamantefuchs/IoT/main/MQTT/SIEMENS/IMAGES/15.png" alt="Siemens MQTT Image 0">
</p>

Download and lets test, and monitor all in the watch table

<p align="center">
  <img src="https://raw.githubusercontent.com/jbustamantefuchs/IoT/main/MQTT/SIEMENS/IMAGES/16.png" alt="Siemens MQTT Image 0">
</p>

In “publishMsgPayload”, you can choose the type of variable you want to send. For this example, leave it set to HEX. We’ll publish the character “A”, which corresponds to 16#41, so replace 16#00 with 16#41.
Make sure the mqttTopic is set to 'test'. Then, click Modify, and set the values to 1 or True for “enable: and “publish”.

Now check the subscriber to see if it received the message.

<p align="center">
  <img src="https://raw.githubusercontent.com/jbustamantefuchs/IoT/main/MQTT/SIEMENS/IMAGES/17.png" alt="Siemens MQTT Image 0">
</p>

To receive data, just publish the desired information externally, like this:

<p align="center">
  <img src="https://raw.githubusercontent.com/jbustamantefuchs/IoT/main/MQTT/SIEMENS/IMAGES/18.png" alt="Siemens MQTT Image 0">
</p>

Check the receivedMsgPayload in the Watch table. The value should change from 16#00 to 16#42, which corresponds to the character B.

<p align="center">
  <img src="https://raw.githubusercontent.com/jbustamantefuchs/IoT/main/MQTT/SIEMENS/IMAGES/19.png" alt="Siemens MQTT Image 0">
</p>

---
