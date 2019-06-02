---
layout: post
title:  "Unable to access network mapped drivers in Windows 10 after reboot or logon."
image: /assets/images/windows-10-logo.png
---
The main cause of this event is the fact that Windows is not saving your credentials to login into the folder.

Before anything else, make sure that you can map network files. There are two ways of doing so: one is through the UI (just click on `This Computer` with the right button and then `Map network drivers`. Next, you will be prompted to insert your credentials and chose the drive letter. Make sure that you hit that `Save credentials` checkbox) and the second one is by running the following command on your `PowerShell` or `CMD`:

```
NET USE {driver letter}: \\{name or IP address}\{shared folders name} /user:{name or IP address}\{username} {password} /persistent:yes
```

The command written above has the `/persistent:yes` tag. You can also try `/savcred` to check if it saves. If it doesen't work, congratulations, you got that bug. Now follow these steps:

1. Open your credential manager in Windows 10. Press `Win + R` or go to `Execute...` and type:

```
control /name Microsoft.CredentialManager`
```

Check if you had any credentials saved due to previous tries. If you have any, just remove it.

2. Go `PowerShell` or `CMD` and run the following command: 

```
CMDKEY /add:{username} /user:{name or IP address}\{username} /pass:{password}
```

This will save another credential into your Credential Manager. Now, try to access your network folder using.

```
NET USE {driver letter}: \\{name or IP address}\{shared folders name} /persistent:yes
```

We did not put the user data into it on purpose. Since you already saved the credentials, this won't be necessary. Afterward, try logoff and login again to check if you still can access youe network folder. If it still does not work, we have one more shot.

3. Create a `.bat` file and use the Task Schedule (`Win+R`, then `taskschd.msc`) to allow it to run on login.



---


