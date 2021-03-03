# Rimworld Multiplayer Headless Server Fork (for 1.1)
Tested and works on Windows 10 and Linux (RimWorld native binary, Debian 9)

## How to use?
* Start Executable with "-host" parameter or add it to a shortcut

## Useful infos for your custom linux server

* Fullscreen should be on, and also RunInBackground in RimWorld XML Configs
* Also set the resolution to something like 640x480
* Edit the "start_RimWorld.sh" to contain following parameters at start "-host"
* Don't use "batchmode nographics" on linux (autosave on linux broken in batch mode, windows is fine, wine is also broken)
* Don't forget to add a pre-generated singleplayer savestate, that will be started in host mode.
* Also don't forget to copy over your pre-configured mod list config. (how do you want to configure it without a gui duh)
* The host mode loads always the file with the newest timestamp. Replay saves have priority over normal saves.

* Use a fake framebuffer display driver (sudo apt-get install xvfb)
* Then execute (or add to the sh file) "Xvfb :1 -screen 0 640x480x24 &"
* Then execute (or add to the sh file) "DISPLAY=:1 ./start_RimWorld.sh"
* Now the server should run fine

## Arbiter throws Socketexceptions and does not start
In my case the localhost ports were blocked by iptables.
Add those lines into your config (/etc/iptables/rules.v4)

* iptables -A INPUT -i lo -j ACCEPT
* iptables -A OUTPUT -o lo -j ACCEPT

## Hardcoded server settings?
Yeah, im lazy. Feel free to edit "Multiplayer.cs" and recompile heh