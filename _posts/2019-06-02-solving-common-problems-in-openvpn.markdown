---
layout: post
title:  "Using OpenVPN Connect before user logon."
image: /assets/images/openvpn-logo.png
---
The Access Server solution came up with the idea that you can make OpenVPN servers easy to manage. That is true until you hit a certain point. OpenVPN makes it hard to to find docs and tutorials about specific software.

This article is about some issues that I’ve run into trying to configure OpenVPN Access Server and OpenVPN Connect. **If you are having trouble with the open source community applications (called OpenVPN Client and OpenVPN Server), these tutorials may not be for you**. Also, **If you are trying to use VPN before your BOOT sequence or to use any Wake-on-LAN services, this tutorial is not for you.**

## Short answer

1. **You need an OVPN file with Autoconnect option.** Download an `.OVPN` file with "Autoconnect" attributes from OpenVPN Access Server Web Admin UI (cursed name). You can check the this attribute in a checkbox on OpenVPN Access Server -> User Management. 

2. **You need to run OpenVPN Connect as a service.** Put the OpenVPN Connect service to start `Automattically`. Go to `Services` (`Win+R` → `services.msc`), and find `OpenVPN Connect`, double-click and change the option `Manually` to `Automatically`. You can read more about the `Automatically` and the `Automatically (dalayed start)` below. 

3. Test it by taking a look into your `Active users` tab into the Web Admin UI and restarting the computer. 

--

## Long answer

A Virtual Private Network (VPN) works on the 7th layer of OSI model, the application layer. With that said, the applications that run over the previous layers needs to be correctly configured before you can use your VPN.

In Windows 10 machines, for example, the network can be 'turned on' (more on this later) in 5 different moments: 

- one before BIOS and UFEI (normally used to use 'Wake-on-LAN');
- one after BIOS and UFEI, but previously the system BOOT sequence (used to 'Boot into network');
- one during the BOOT sequence. This is normally when you can see your computer receiving a DHCP address from the pool.
- one after the BOOT but before the login. This is how you can use domain credentials and access some resources over the network.
- one after the user login. The VPN starts running at this point.

What we are trying to do is to move the VPN connection two steps above. 

On a Windows 10 machine, to make the connection available to the machine instead of the user, **you should run OpenVPN as a service**, not as an application. Services can be loaded using a **Local Machine** credentials which applications cannot use.

### Running OpenVPN Connect as a 'Service'.
When using the OpenVPN Connect, the service will automatically be added into the `Services` (`Win+R` → `services.msc`). 

You can make it starts during BOOT sequence by clicking on it and selecting `Automatically` as an option to start the service after the other services on the machine. **Important: if you chose `Automatically (delayed start)`, the service will take up 2 minutes after the BOOT sequence**, which can lead to falsely assuming that the service is not working. 

### Configuring autologin and auto-connect. 

Also, to make the service run correctly, you need to add an `.OVPN` configuration file with "Autoconnect" attributes into your OpenVPN Connect application. Once you add those configuration files, they are going to be copied to the OpenVPN Connect folder and you can delete the original.OVPN file (differently than the OpenVPN Client application).

To make sure that your client has an Autoconnect profile, login into you (Web Admin UI) and make sure that the checkbox saying `Autoconnect` is marked. 

