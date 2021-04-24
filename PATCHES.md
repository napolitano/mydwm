# Patches and Modifications

This version of DWM has been pre-patched and configured to provide still the efficiency and performance advantages of dwm while adding some layers of comfort to it

## Prerequisites

The modified configuration utilizes "rofi" instead of "dmenu" as a semenatic launcher for applications and "kitty" as default terminal app.
Reason for this decision was weighting out of performance and comfort. Both chosen alternatives provide comfort while maintaining very good performance and a more or less lightweight approach.

On debian based systems you can install them with the following command

```bash
sudo apt-get install rofi kitty
```

If you do not want this changes, you can easily edit the config.def.h (before initial buil) or the config.h file.

## Applied Patches

All applied patches were taken from the offocial source at https://dwm.suckless.org. The applied DIFF-files have been added to this repository for convenience.

### Custom Urgency Borders 

This patch makes borders of "urgent" windows a different color. By default it is bright red. Use config.h item "urgbordercolor" to change it.

An alternative patch which provides a minimal urgent border utilizing the existing features to provide a feature parity to the urgent tags, using the same foreground color as the urgent tags which they inverted.

Source and additional information: https://dwm.suckless.org/patches/urgentborder/

### Colorbar

This patch lets you change the foreground and background color of every statusbar element.

Simply change the RGB values in the config.def.h.

Source and additional information: https://dwm.suckless.org/patches/colorbar/

### Default Tag Apps
 
This patch is for those who dedicate each tag to certain general tasks. Tag 1 might be the tag used for all terminal tasks, tag 2 might be for internet/browser things etc. When you have these tags already mapped out, generally you open one application more than any other in each tag. This patch aims at harnessing this workflow for improvement of speed and practicality.

Source and additional information: https://dwm.suckless.org/patches/default_tag_apps/

### Restart Signal

dwm can now be restarted via MOD+CTRL+SHIFT+Q or by kill -HUP dwmpid

In addition, a signal handler was added so that dwm cleanly quits by kill -TERM dwmpid.

Source and additional information: https://dwm.suckless.org/patches/restartsig/

### Systray

A simple system tray implementation. Multi-monitor is also supported. The tray follows the selected monitor.

In case icons disappear when toggling the bar, try a different font size in dwm. This has helped at least in one case with pidgin.

Source and additional information: https://dwm.suckless.org/patches/systray/

### Tag Labels

Displays the executable name of each tag's current master client after the tag name in the dwm bar.

- For example, if st is the master client on tag 1, then the bar would display [1: st] as opposed to just 1.

The format of the label, for both non-empty and empty tags, is configurable through the configuration variables ptagf and etagf respectively. There is also a config variable, lcaselbl, that, when enabled, makes the first letter lowercase (out of personal preference).

Source and additional information: https://dwm.suckless.org/patches/taglabels/

### TileGap

Window gaps for the tile layout done right (in my humble opinion). The same size gap between master and stack, window and window, and window and screen edge. Size configurable in config.h.

Source and additional information: https://dwm.suckless.org/patches/tilegap/

### Underline tags

Underlines selected tags. This looks good for certain color schemes.

Config variables are avaliable to edit the size and position of the underline, as well as an option to underline all tags instead of just the active ones.

Source and additional information: https://dwm.suckless.org/patches/underlinetags/

## Modifications

The modified configuration utilizes "rofi" instead of "dmenu" as a semenatic launcher for applications and "kitty" as default terminal app.
Reason for this decision was weighting out of performance and comfort. Both chosen alternatives provide comfort while maintaining very good performance and a more or less lightweight approach.

The color scheme was modified to provide better contrast and readibility. You may change it, if you do not like the colors.

## Status Bar and Systray

I'm using Linux Mint on my development computer. The following script was made to fit my needs on my computer and should be understood as a starting point.
If you are also a Linux Mint user, it might work for you out-of-the-box. On Linux mint you have to add the following code to your ~/.profile file.

Non-Standard-Tools have been commented. If you want to use them, you have to install and configure them before using the script.
Be aware that mistakes at this stage may cause startup problems which might need a fix through recovery mode in worst case. So please use and modify this script only if you a) know what you are doing and b) have enough knowledge to fix potential problems.


```bash
#DWM Status Bar Script

#kdeconnect-indicator &
#indicator-cpufreq &
#caffeine-indicator &
#redshift-gtk &
pasystray &
synapse --startup &
mintupdate-launcher &
blueberry-tray &
system-config-printer-applet &
/usr/bin/gnome-keyring &
csd-xrandr &
#mpd & 

while true; do
	xsetroot -name "$USER :: $(date '+%A, %d. %B %Y - KW %U - %H:%M Uhr')"
	sleep 1m
done &
```
