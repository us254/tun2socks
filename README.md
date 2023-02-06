

To run a command in Command Prompt (CMD) on Windows, you can follow these steps:

1:  Click on the Start button and search for Command Prompt or cmd.
2:  Right-click on the Command Prompt result and select Run as administrator (if you want to run the command with administrative privileges).
3:  In the Command Prompt window, type the command you want to run and press Enter.

The command will be executed and the result will be displayed in the Command Prompt window.



In order to include the folder with the tun2socks files in the Windows environment path system, perform these steps.

--------------------------------
To add the path of a folder to the Windows environment path system, you can follow these steps:

1:  Right-click on the Start button and select System
2:  Click on Advanced system settings
3:  Click on the Environment Variables button
4:  Under System Variables, scroll down and find the Path variable
5:  Click on the Edit button
6:  Click on New and add the path of the folder you want to add
7:  Click OK to close all the windows
8:  The new path should now be available in the Windows environment path system
----------------------------------------------
Execute this command afterwards.

```
tun2socks -device wintun -proxy socks5://127.0.0.1:10808

```
Locate the server address in your v2ray configuration.
For instance, the address of the server in the v2ray settings is 185.221.160.231.

Execute this command afterwards.


```
route print

```
---------------------
 Connection-specific DNS Suffix  . : domain.name
   IPv4 Address. . . . . . . . . . . : 192.168.1.5
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.1.1

Interface List
 41...........................WireGuard Tunnel
---------------------------

After opening a new Command Prompt window, run these commands based on the outcome of the previous command.

```

1:  netsh interface ip set address name=wintun source=static addr=10.10.10.1 mask=255.255.255.0 gateway=none
2:  netsh interface ip add dns name=wintun addr=1.1.1.1
3:  netsh interface ipv6 set interface wintun forwarding=disabled
4:  route add 0.0.0.0 mask 0.0.0.0 10.10.10.1 if 41 metric 5
5:  route add 185.221.160.231 mask 255.255.255.255 192.168.1.1

```

