---
layout: post
title:  "Enabling multiple users in RDP on Microsoft Windows 10."
image: assets/images/windows-10-logo.png
---
Before anything else, **do NOT download any already patched `termsrv.dll` files available on the web!** Microsoft is constantly updating those files, and since Windows 10 has a lot of versions, it is possible that you're going to break your files. I compared some files from the 1809 october version and the patched files available on the web, and they differ a lot. 

1. Download and install an HEX Editor (I recommend HxD, because it is free):
[You can download HxD here](https://mh-nexus.de/en/hxd/).

2. Backup the termsrv.dll file:

```copy C:\Windows\system32\termsrv.dll %USERPROFILE%\Desktop\termsrv.dll.backup```

3. Run HxD as an administrator. Right-click on whatever the HED editor you chose and `Run as Administrator`.

4. Find and open the following file into the HEX editor:
`C:\Windows\system32\termsrv.dll`

5. Replace the following HEX: `39 81 3C 06 00 00 0F 84 3B 2B 01 00` with the HEX `B8 00 01 00 00 89 81 38 06 00 00 90`, and remember to check if there is an option to **search and replace HEX code** instead of normal text.

6. Save the file. If you are unable to save the file due to permissions, try saving it on another location and solve the permission problems before replacing the file on `C:\Windows\system32\`.

---

A month ago I decided to implement a "Microsoft-first" approach into the company that now I am working for. Since they have almost every software running exclusively on top of Windows, we decided to migrate the other minors services to Microsoft/Azure platforms. 

It has been a painful month, to say the last. Microsoft has some weird abstractions involving RDP. They believe that *multiple RDP connections to a system is na EULA violation*. Since this do **not** reflect the reality, I am posting this tutorial.
