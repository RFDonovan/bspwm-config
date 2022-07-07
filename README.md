# BSPWM
This is a repo of my supposedly custom `BSPWM` config while tinkering on my newly installed `ArchCraft` OS.
A journey on exploring Tiling Window Manager.
## BSPC
Adding rules to send `brave` to desktop number 2 when launching
```shell
bspc rule --list|grep Fire
#Firefox:Places:* => state=floating follow=on focus=on
bspc rule --list|grep 2
#firefox:*:* => desktop=^2 follow=on focus=on
#chromium:*:* => desktop=^2 follow=on focus=on
#Gimp-2.10:*:* => desktop=^7 state=floating follow=on focus=on
bspc rule -a brave -o desktop=^2
bspc rule --list|grep 2
#firefox:*:* => desktop=^2 follow=on focus=on
#chromium:*:* => desktop=^2 follow=on focus=on
#Gimp-2.10:*:* => desktop=^7 state=floating follow=on focus=on
#brave:*:* -> desktop=^2
``` 
### SXHKD or Simple X HotKey Deamon

#### Adding Brave browser in the hotkey

Inside the config file `.config/sxhkd/sxhkdrc` we can add the following lines
```shell
# Open Application
Super + shift + {f,w,e,b}
{thunar,firefox,geany,brave}
```

#### using super+pageup pagedown to send window on next,previous desktop

Inside the config file `.config/sxhkd/sxhkdrc` we can add the following lines
```shell
# Send focused window to the next workspace and follow using pgup and pagedown
super + {Prior,Next}
bspc node focused --to-desktop {prev.local,next.local} --follow
```
