---
layout: post
title:  "Gracefully installing Firefox 67 on Debian."
image: /assets/images/firefox-logo.png
---
Before anything, notice that this installation will be unable to access your profile previously installed Firefox versions. 

Debian and other Linux distros use ESR versions, which makes you unable to use the package manager to install it. I highly recommend you to keep both the ESR and the latest version or use Firefox Sync - [the single sync app that I trust](https://hacks.mozilla.org/2018/11/firefox-sync-privacy/).

1. Download the latest Firefox directly from the [Firefox page](https://www.mozilla.org/en-US/firefox/new/) or just [click here for the latest Linux version](https://www.mozilla.org/en-US/firefox/download/thanks/).

2. Extract and move its content to the `/opt` folder. You need to be `sudo` to do that. The `/opt` folder is the right place to put handmade installed apps.

3. Make a `chmod +x` on the `firefox` application to enable its capacity to run as an executable. Notice that I am using `sudo` just because I moved it into `/opt` before making the modification.

```
cd /opt/{check your location}
sudo chmod +x firefox
```  

4. Create a symbolic link to the executable. Notice that you have to check the path to your Firefox installation to create the symbolic link.
```
sudo ln -s /opt/{check your location}/firefox /usr/bin/firefox
```

5. Create your own `.desktop` file. This part makes it available to interact with the native menus for a seamless experience. For this part, I took an already built `.desktop` from the previously supported Firefox (ESR) and made some mods.

You can download a beutifully built .desktop file from [my git repository](https://github.com/davimello28/firefox-67-desktop-file).

Place it inside `/usr/share/applications` if you want this icon to be available to all users. For your local users only, place it inside `~/.local/share/applications`. You can check your menus to see if it shows up correctly.
