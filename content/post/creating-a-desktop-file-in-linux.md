---
title: "Creating a Desktop File in Linux"
date: 2018-06-05T07:47:26+02:00
draft: false
---

Recently, I downloaded [TeamSpeak](https://www.teamspeak.com/) which is a voice application.
I extracted the application to a folder and inside was `ts3client_runscript.sh` which would allow me to run the application.

Over time it became redundant to continually open the terminal to navigate and run the script to use the application.
Here are the steps I took to enable it to be run from the application launcher.

First, I wanted the application to be used regardless of which user I was logged in as. So I moved it from my `Downloads` folder into `/usr/local/share/`

``` bash
sudo cp -R ~/Downloads/TeamSpeak3/ /usr/local/share/teamspeak/
```

Next I needed to ensure that any user could run the `ts3client_runscript.sh` script now in `/usr/local/share/teamspeak`.
I gave read, write and execute permissions to the entire teamspeak folder.

``` bash
sudo chmod +rwx -R /usr/local/share/teamspeak/
```

With this done, any user would have access to teamspeak and be able to run it. Next up I needed the launcher to be aware of it.
I downloaded an image to use as an icon and saved it to `/usr/local/share/teamspeak/ts3icon.png`

First, create a desktop file for your user.
``` bash
touch $home/.local/share/applications/teamspeak.desktop
```

Next use your favourite editor and place the following inside your teamspeak.desktop file.
``` bash
[Desktop Entry]
Name=Teamspeak
Comment=
Exec=/usr/local/share/teamspeak/ts3client_runscript.sh
Icon=/usr/local/share/teamspeak/ts3icon.png
Terminal=false
Type=Application
```

That's it you're done. You've got a teamspeak application in the application launcher with a pretty icon to boot.