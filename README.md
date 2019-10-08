# nVidia Prime Wrapper Script with BBSwitch #

This is a wrapper script that utilizes the `prime-select` command, but also uses bumblebee's bbswitch to completely shut off the GPU in intel mode. This results (for me) in about 7W usage on a Thinkpad X1 Extreme versus 12-14W with the GPU on.

### Installation ###
1. Install bbswitch: `# apt install bbswitch-dmks`
1. `$ git clone https://github.com/hakasapl/prime-wrapper-bbswitch`
1. `# cp prime-wrapper-bbswitch/gpu-mode /usr/local/bin/`

### Usage ###
`gpu-mode [query,intel,nvidia] [-s,-n]`

Option `nvidia` will set `prime-select` to nvidia, and turn on the GPU at boot. Option `intel` will set `prime-select` to intel, and turn off the GPU at boot.

The `-s` option will shutdown the system (no option is reboot automatically)
The `-n` option will setup the system to use the given mode, but will do no power operation, and the changes will take effect in the next reboot.

### Troubleshooting ###
**No Display Output in nVidia Mode**  
Comment out the line `options nvidia-drm modeset=1` in the file `/lib/modprobe.d/nvidia-kms.conf` and run `# update-initramfs -u`
