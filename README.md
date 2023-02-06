

In order to include the folder with the tun2socks files in the Windows environment path system, perform these steps.

--------------------------------

1. Right-click on the Start button and select `System`.
2. Click on `Advanced system settings`.
3. Click on the `Environment Variables` button.
4. Under `System Variables`, scroll down and find the `Path` variable.
5. Click on the `Edit` button.
6. Click on `New` and add the path of the folder you want to add.
7. Click `OK` to close all the windows.
8. The new path should now be available in the Windows environment path system.


----------------------------------------------
Adjust the `socks5://host:port` to the appropriate configuration specified in the client's config file for inbound V2Ray, typically set to `socks5://127.0.0.1:10808` .Run the command after making modifications to it.

`
tun2socks -device wintun -proxy socks5://host:port
`


Run this command in a separate command prompt window .

 To see only the default gateway, you can use the following command:
 
`ipconfig | findstr /r /c:"Default Gateway.*:"`

`
route print -4
`

The outcome upon executing the command will be similar to this.

---------------------

### Interface List

- 41: `WireGuard Tunnel`

---------------------------


Run these commands based on the outcome of the previous command.
The "server IP" in a v2ray setting can refer to either the IP address of a cloudflare server or the IP address of your own server, depending on how it is configured.

You only need to make changes to the final two lines.

```

netsh interface ip set address name=wintun source=static addr=10.10.10.1 mask=255.255.255.0 gateway=none
netsh interface ip add dns name=wintun addr=1.1.1.1
netsh interface ipv6 set interface wintun forwarding=disabled
route add 0.0.0.0 mask 0.0.0.0 10.10.10.1 if [Interface NUM] metric 5
route add [server ip] mask 255.255.255.255 [Default Gateway]

```
