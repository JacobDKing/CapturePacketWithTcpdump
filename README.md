# Capture a Packet With TCPDump
This project is meant to show comfortability and competence with using the TCPdump program to capture packets.

In this project, I act as an analyst who needs to use tcpdump to capture and analyze live network traffic from a Linux virtual machine.

Tasks in this lab:

  - Identify available network interfaces. 
  - Use tcpdump to capture live network traffic.
  - Save network traffic to a packet capture file.
  - Filter the packet capture data.

<br />
<br />

<h2>Identify Network Interfaces</h2>
In this task, tcpdump is used to filter live network packet traffic on an interface.

Use ifconfig to identify the interfaces that are available:
 <br /> 
<img src="https://i.imgur.com/xD0UJVu.png" height="80%" alt="Identify Network Interfaces 1"/> <br />
The Ethernet network interface is identified as eth0. <br />
Use tcpdump to identify the interface options available for packet capture: <br />
<img src="https://i.imgur.com/lWAJDMZ.png" height="80%" alt="Identify Network Interfaces 2"/> <br />





<h2>Inspect the network traffic of a network interface with tcpdump</h2>
In this example, some of the properties that tcpdump outputs for the packet capture data previously shown will be identified.

Run tcpdump with the following options: 
  - Capture data specifically from the eth0 interface.
  - Display detailed packet data.
  - Capture 5 packets of data.

<img src="https://i.imgur.com/TPyRnl9.png" height="80%" alt="Inspect the network traffic of a network interface with tcpdump 1"/> <br />


<h4>Exploring network packet details</h4>

In the example data at the start of the packet output, tcpdump reported that it was listening on the eth0 interface, and it provided information on the link type and the capture size in bytes: <br />
<img src="https://i.imgur.com/80FtZWa.png" height="80%" alt="Inspect the network traffic of a network interface with tcpdump 2"/> <br />
On the next line, the first field is the packet's timestamp, followed by the protocol type, IP: <br />
<img src="https://i.imgur.com/XyNQ6rw.png" height="80%" alt="Inspect the network traffic of a network interface with tcpdump 3"/> <br />
The verbose option, -v, has provided more details about the IP packet fields, such as TOS, TTL, offset, flags, internal protocol type (in this case, TCP (6)), and the length of the outer IP packet in bytes: <br />
<img src="https://i.imgur.com/IBHXHV1.png" height="80%" alt="Inspect the network traffic of a network interface with tcpdump 4"/> <br />
In the next section, the data shows the systems that are communicating with each other: <br />
<img src="https://i.imgur.com/GszEnf4.png" height="80%" alt="Inspect the network traffic of a network interface with tcpdump 5"/> <br />
The remaining data filters the header data for the inner TCP packet: <br />
<img src="https://i.imgur.com/HegR1Ud.png" height="80%" alt="Inspect the network traffic of a network interface with tcpdump 6"/> <br />

<br />
<br />

<h2>Capture network traffic with tcpdump</h2>
In this step, tcpdump is used  to save the captured network data to a packet capture file.

Capture packet data into a file called capture.pcap using a specific command will be used to run tcpdump in the background with the following options: 

  - Capture data from the eth0 interface.
  - Do not attempt to resolve IP addresses or ports to names.This is best practice from a security perspective, as the lookup data may not be valid. It also prevents malicious actors from being alerted to an investigation.
  - Capture 9 packets of data and then exit.
  - Filter only port 80 traffic. This is the default HTTP port.
  - Save the captured data to the named file.

<img src="https://i.imgur.com/6hOkCkz.png" height="80%" alt="Capture network traffic with tcpdump 1"/> <br />
Use curl to generate some HTTP (port 80) traffic: <br />
<img src="https://i.imgur.com/7wEpq97.png" height="80%" alt="Capture network traffic with tcpdump 2"/> <br />
Verify that packet data has been captured: <br />
<img src="https://i.imgur.com/8gnKF5Y.png" height="80%" alt="Capture network traffic with tcpdump 3"/> <br />

<br />
<br />

<h2>Filter the captured packet data</h2>
In this step, tcpdump will be used to filter data from the packet capture file that was previously saved.

Use the tcpdump command to filter the packet header data from the capture.pcap capture file using a command to run tcpdump with the following options: 

  - Disable port and protocol name lookup.
  - Read capture data from the named file.
  - Display detailed packet data.

<img src="https://i.imgur.com/9kKeB9y.png" height="80%" alt="Filter the captured packet data 1"/> <br />
Use the tcpdump command to filter the extended packet data from the capture.pcap capture file using a specific command to run tcpdump with the following options:  <br />

  - Disable port and protocol name lookup.
  - Read capture data from the named file.
  - Display the hexadecimal and ASCII output format packet data. (Security analysts can analyze hexadecimal and ASCII output to detect patterns or anomalies during malware analysis or forensic analysis.) <br />
<img src="https://i.imgur.com/t7L14u7.png" height="80%" alt="Filter the captured packet data 2"/> <br />

<br />
<br />





<h4>End of Project</h4>
