# NVIDIA Prime Wrapper Script for Optimus Laptops #

This is a wrapper script that utilizes the `prime-select` command, but also uses bumblebee's bbswitch to completely shut off the GPU in intel mode. This results (for me) in about 7W usage on a Thinkpad X1 Extreme versus 12-14W with the GPU on. You must have proprietary nvidia drivers installed with nvidia-prime (ubuntu distributions only).

### Installation ###
1. Install bbswitch: `# apt install bbswitch-dmks`
1. `$ git clone https://github.com/hakasapl/prime-wrapper-bbswitch`
1. `# cp prime-wrapper-bbswitch/gpu-mode /usr/local/bin/`

### Usage ###
`# gpu-mode [query,intel,nvidia] [-s,-n]`

Option `nvidia` will set `prime-select` to nvidia, and turn on the GPU at boot. Option `intel` will set `prime-select` to intel, and turn off the GPU at boot.

The `-s` option will shutdown the system (no option is reboot automatically)
The `-n` option will setup the system to use the given mode, but will do no power operation, and the changes will take effect in the next reboot.

**Note:** At this time a reboot is required for changes to take effect, I have yet to find a way to do this without a reboot.

### Troubleshooting ###
**No Display Output in nVidia Mode**  
If you are using GDM (Gnome Display Manager), you need to modify the file `/etc/X11/Xwrapper.config`. Add the following line to the end of the file.
```
needs_root_rights=yes
```
