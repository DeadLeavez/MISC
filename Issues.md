# INDEX
- [Launcher](#launcher)
- [Game](#game)
- [Appendix](#appendix)

# Launcher

### Default server 'SPT-AKI' is not available
Common Causes:
You are host
- Server is not running
- Launcher is not set to the correct address
- Server has bad ``\Aki_Data\Server\configs\http.json`` settings. Should always be ``0.0.0.0`` in both IP fields. 

Common Causes:
You are not host
- Launcher is not set to the correct address
- Host has not port forwarded correctly
- Host is behind [CGNAT](#CGNAT)

Either
- Trailing ``/``, Make sure the IP in the launcher is ``http://xxx.xxx.xxx.xxx:6969``

### ERROR A patch in <plugin> FAILED. One or more errors occurred. SUBSEQUENT PATCHES HAVE NOT LOADED, CHECK LOG FOR MORE DETAILS
Common Causes:
- Wrong aki version
- Server has bad ``\Aki_Data\Server\configs\http.json`` settings. Should always be ``0.0.0.0`` in both IP fields. 
- Bad IP setting in launcher settings. Some routers don't support NAT loopback. If you're on LAN with router. Use Local IP instead of WAN IP. or ``127.0.0.1`` if you're on the same PC.

# Game

### Game doesn't load. Frozen. 
Common Causes:
- Bundle Issue (Lots of mods. Try async bundle loader, send cache, or remove bundle mods )
- Mod issue
- Bad AKI install

### Cannot see host menu
Common Causes:
- Incorrect installation of Fika. 

### Cannot see hosted games in the lobby menu
Common Causes:
- Connected to the wrong server
- Missing Fika-server on the server

### Stuck on Waiting for X players
Common Causes:
- Outdated version of fika

### Unable to connect to the server. Make sure that all ports are open
Common Causes:
Hosting with port forwarding
- Host doesn't have port UDP 25565(default) port forwarded
- Client or Host doesn't have ``EscapeFromTarkov.exe`` allowed through their firewall
- Has UPNP enabled/disabled (try changing it)

Common Causes:
Hosting on [VPN](#vpn)
- Client or Host doesn't have ``EscapeFromTarkov.exe`` allowed through their firewall
- Not bound/forced THEIR OWN VPN IP in F12
- Has UPNP enabled (should be disabled)
- Has Native Sockets enabled (Only enable this AFTER you have ensured everything work. And disable if it doesn't work afterwards.)

# Appendix

### CGNAT
```diff
+ Check if you are on CGNAT +
Sign in to your router and locate the WAN IP address.
If the WAN IP of your router is within any of the following ranges, you are on CGNAT:
- 192.168.x.x
- 10.x.x.x
- 172.16.x.x to 172.31.x.x
- 100.64.x.x to 100.127.x.x
If your WAN IP is outside these ranges you might not be on CGNAT but do verify if the WAN IP in your router matches the IP shown on https://ipv4.icanhazip.com. If the IPs do not match, you are on CGNAT. Port forwarding may not be possible without acquiring a static IP from your ISP.
```

Solution: USE [VPN](#vpn)

### VPN
```diff
VPN is a virtual local network over the internet. It removes any need to port forward on routers, and is in some cases the only viable option if port forwarding isn't possible. Or you're behind a CGNAT
+ Best VPNs to use for hosting Fika
Radmin VPN or ZeroTier (Both are free)
Avoid Hamachi if possible
```