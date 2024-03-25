# CiscoAutoConfig-PortTracer
A python program used for managing access layer switches in a large network environment. Adding functionality to determine switch name and port number connected to any MAC address input.

We have Cisco devices of all ages and IOS versions, and writing EEM scripts only helps newer devices, so what about the older
devices? The program I created was to help network administration in large scale networks. It makes searching through large sets of switches and
applying changes a lot less tedious. 
The program does a few things: 
Retrieves a list of IP addresses 
Prompts for SSH credentials 
Auto SSH’s to devices in the list one at a time 
Downloads and parses ‘sh cdp neighbor detail’ and ‘sh interface status’ into dictionary’s 
Then, in the menu, there are views for certain criteria: 
Show error disabled ports
Show devices in CDP neighbor but not trunked or AP’s not in AP vlan based on CDP model
Show connected interfaces that are configured for trunk or AP’s but have no CDP neighbor 
Then, a separate menu for changing interface configurations: 
Auto default and reconfigure port to either access, trunk, or AP depending on CDP model
Auto default and reconfigure ports who are connected and configured for trunk or AP that have no CDP
Auto default error disabled ports
Manually configure port 
The program is written in Python 2.7 and uses Paramiko to handle SSH connections. I use it on my Linux machine, but am working on porting it to
windows. 
Being that this is my first Python program, I’d really appreciate feedback on the code, thanks. 
usage: autocisco.py [-h] -f HOSTS [-a ACCESS] [-w WIRELESS] [-v VOICE]
 An awesome Python Program to search through switches and auto configure ports
based on CDP via SSH.
 optional arguments:
  -h, --help show this help message and exit
  -f HOSTS, --hosts HOSTS Specify a hosts file
  -a ACCESS, --access ACCESS Enter Access Vlan Value -- (default = 1)
  -w WIRELESS, --wireless WIRELESS Enter Wireless Vlan Value -- (default = 1)
  -v VOICE, --voice VOICE Enter Voice Vlan Value -- (default = 1)
