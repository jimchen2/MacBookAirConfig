# MacBookAirConfig

This repo is for my configuration files for MacBook Air 15 inch 2023. 

## Why MacBook?

So my previous laptop was System76 Darter Pro

### MacBook Air vs System76 Darter Pro

1. Pros
- Power Efficiency: Although not as good as 18 hours(advertised), MacBook easily runs 10 hours of web browsing tasks. Darter Pro was advertised to run 9 hours, however, it seldomly exceeds 4 hours on light tasks.
- Hardware: Macbook is advertized to run smoothly for 10 years. Darter Pro has some random hardware bugs(with keyboard, even when I boot to grub, no OS, some keys would randomly be remapped and cause undeterministic behaviors, and considering the laptop was pretty new(less than half a year old). Dirt easily falls into the touchpad and keyboard of Darter Pro, causing it to be dirty. Touchpad is unresponsive on tap sometimes(undeterministic). Considering it is a small company somewhere in Colorado, I cannot send my laptop there for them to repair.
- Thermal: Macbook Air is very cool. 
 
2. Things I don't care that much
- Weight: MacBook Air weighs at 1.5 kg, Darter Pro weighs at 1.66 kg
- Noise: MacBook Air is quiet, Darter Pro fan is very loud
- Brand: While System76 is on average quite expensive, it is less recognized than Apple

3. Cons
- Open-source: System76 is (and promotes) open source, while Apple is proprietary
- ArchLinux not available: So I am using Asahi Fedora, without the AUR packages. Still decent.
- No Microphone

## Downloading Installer for Asahi(in China)

So the files are not available in China, just download and upload them to a S3 bucket (hopefully available in China), then change the urls in the installing script(alx.sh file and installer json file)

## Enabling Fn

MacBook has this annoying feature where you need to press alt+fn+f4(closing) or alt+f2(renaming), so remap the fn from the initramfs and regenereate it.

Change this file `/etc/modprobe.d/keyboard.conf`
```
options hid-apple swap_fn_leftctrl=1
options hid_apple fnmode=2
```
Then `sudo dracut --regenerate-all --force`

## Remaping Other Keys

Use evremap:
 
1. Move the executable
2. Create a systemd service
```
[Unit]
Description=Evremap Keyboard Remapper
After=multi-user.target

[Service]
Type=simple
ExecStart=/usr/local/bin/evremap remap /etc/evremap/config.toml
Restart=on-failure

[Install]
WantedBy=multi-user.target
```
3. The file `/etc/evremap/config.toml` (in this repo)

## Removing Gnome Bloatware
![image](https://github.com/jimchen2/MacBookAirConfig/assets/123833550/8b5914dc-80c3-4821-a8c4-5fb96cdbd980)

## Setting Gnome Shortcuts

## Disable While Typing

