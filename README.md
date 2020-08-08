# NVIDIA Prime Startup Script for Optimus Laptops #

This is a startup script that uses bumblebee's bbswitch to completely shut off the GPU in `prime-select` intel mode. This results (for me) in about 7W usage on a Thinkpad X1 Extreme versus 12-14W with the GPU on. You must have proprietary nvidia drivers installed with nvidia-prime (ubuntu distributions only).

### Installation ###
1. Install bbswitch: `# apt install bbswitch-dkms`
1. `$ git clone https://github.com/hakasapl/prime-wrapper-bbswitch`
1. Copy `gpu-bbswitch` to any folder.
1. Add crontab entry: `sudo crontab -e` and add the line `@reboot sudo <SCRIPT_LOCATION>/gpu-bbswitch`

### Usage ###
Simply running `prime-select <intel,nvidia>` and rebooting will automaticall turn the gpu on/off.

### Troubleshooting ###
**No Display Output in nVidia Mode**  
If you are using GDM (Gnome Display Manager), you need to modify the file `/etc/X11/Xwrapper.config`. Add the following line to the end of the file.
```
needs_root_rights=yes
```
