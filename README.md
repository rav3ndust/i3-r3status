# i3-r3status

## Description

i3status is a small program for generating a status bar for i3bar, dzen2, xmobar
or similar programs. It is designed to be very efficient by issuing a very small
number of system calls, as one generally wants to update such a status line
every second. This ensures that even under high load, your status bar is updated
correctly. Also, it saves a bit of energy by not hogging your CPU as much as
spawning the corresponding amount of shell commands would.

## Development

i3status has the following dependencies:
  * libconfuse-dev
  * libyajl-dev
  * libasound2-dev
  * libnl-genl-3-dev
  * autoconf (compile-time only dependency)
  * asciidoc (only for the documentation)
  * libpulse-dev (for getting the current volume using PulseAudio)

On debian-based systems, the following line will install all requirements:
```bash
apt-get install autoconf libconfuse-dev libyajl-dev libasound2-dev libiw-dev asciidoc libpulse-dev libnl-genl-3-dev
```

## Upstream

i3status is developed at https://github.com/i3/i3status

## Compilation

Prefer installing i3status via your Linux distribution’s package manager.

If you absolutely have to build from source, use:

```bash
  autoreconf -fi
  mkdir build
  cd build
  ../configure --disable-sanitizers
  make -j$(nproc)
  sudo make install
```
# Usage With i3Blocks

I have made a configuration for i3blocks. I am going to make it an official part of the project soon, but for the sake of saving time and storing the code here, here is the **i3blocks.conf**:

```
[app launcher]
full_text=i3-r3 launcher
command=i3-dmenu-desktop --dmenu='dmenu -i -nb black -nf purple -sb green -sf red -l 10 -p "nightshader - Applications List:"'
#interval=persist
align=left
min_width=1100

[separator]

[logout]
full_text=log out of i3-r3
command=logout
align=center
min_width=100

[shutdown]
full_text=shut down
command=shutdown -h 1 && notify-send "Shutting down in 1 minute..."
align=center
min_width=100
```
