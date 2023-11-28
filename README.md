# Ephemeral Port Forwarding with Windscribe for qBitTorrent - A Guide

### Requirements

* qBitTorrent
* WireGuard, IKEv2 (best), or UDP (alright), or TCP, Stealth, and WStunnel (not recommended unless you cannot use the others). Port isn't very important. 443 is best.
![](Images/Protocol.png)

### Activate port forwarding

1. [Log in to Windscribe.](https://windscribe.com/login)
2. Go to the [ephemeral port forwarding page.](https://windscribe.com/myaccount#porteph)
3. Request **matching** or **specific** port. ==Note down the port.==
4. Disconnect (if currently connected) and reconnect. *For WireGuard, you may have to switch servers or disconnect for a brief period of time.*

### Configure Windscribe & qBitTorrent

1. Open Windscribe, and connect.
2. Turn on the **always on firewall**. This prevents your internet traffic from leaking in the event Windscribe disconnects. Leave this setting on for the remainder of your torrenting session.
![](Images/AlwaysOn.png)
3. Open qBitTorrent.
4. Press Alt + O. This should open the Preferences menu for qBitTorrent. You can also select Tools > Preferences on the top.
5. Select *Connection* on the left.
6. Select **TCP** as your peer connection method, and type in the port you noted down. **Disable UPnP** as well.
![](Images/Port.png)
7. Select *Advanced* on the left.
8. **Bind** qBitTorrent to your **VPN network interface**. 
![](Images/Interface.png)
    * Windows:
         * On WireGuard, it should be titled ==Windscribe WireGuard==.
         * On IKEv2, it should be titled ==Windscribe IKEv2==.
         * On OpenVPN (UDP/TCP/Stealth/WStunnel) it should be titled ==Local Area Connection== (potentially with a number). You will have to check this in your Windows adapter settings. 
    * Linux, MacOS:
         * The network interface may show up as ==utun420== or ==tun0==.

9. Check if your port is forwarding. You can do this at [YouGetSignal](https://www.yougetsignal.com/tools/open-ports/) or [Can You See Me.](https://canyouseeme.org/) Make sure you type in the correct port. If it says it is open, then you are good to go.

Make sure you **do not turn off Windscribe's Always On firewall before you close your torrenting client.** Make sure to **close your torrenting client from the tray** before you shut down the VPN and its firewall. **You will need to turn off the Always-On firewall if you want to use the internet without a VPN after you are done.** You can set it to automatic or manual in order to disable the always on firewall.

Do not open your torrenting client without the VPN connected and with the Always On firewall active. This is a risk and **may leak your true IP.**