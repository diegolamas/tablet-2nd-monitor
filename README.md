# tablet-2nd-monitor

## HOW-TO:
        
1. `pip install dotmap`  
2. `sudo apt install x11vnc`
3. If you don't have "VIRTUAL1" monitor (`xrandr -q`): https://unix.stackexchange.com/questions/378373/add-virtual-output-to-xorg
4. Create a password: `x11vnc -storepasswd`
5. Get modeline for your tablet's resolution: `gtf 1280 800 60` (1280x800 in this case)
6. Using the modeline: 
    1. `xrandr --newmode "1280x800_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync`
    2. `xrandr --addmode VIRTUAL1 1280x800_60.00`
    3. `xrandr --output VIRTUAL1 --mode 1280x800_60.00 --right-of EDP1` (EDP1 is the name of my primary monitor (check `xrandr -q` output))
7. Start vnc server: `x11vnc -clip 1280x800+1366+0` (+1366+0 is the position for the 2nd display, my primary monitor resolution is 1366x768 so 1366 is the starting position).
8. Use a VNC client on your tablet to connect to your PC using your ip (`ifconfig`) and the password you created before.

### links

https://askubuntu.com/a/750497

https://github.com/mrenrich84/vnc_virtual_display_linker
