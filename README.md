# zenauracore - RGB keyboard control for the Asus Zenbook UX7602ZM

Linux-compatible open-source libusb implementation forked from [wroberts](https://github.com/wroberts)'s fantastic [rogauracore](https://github.com/wroberts/rogauracore).

Supports the Asus Zenbook UX7602ZM RGB keyboard with ID [0b05:8854](https://linux-hardware.org/index.php?id=usb:0b05-8854)

## Usage

```
Usage:
   zenauracore COMMAND ARGUMENTS

Supported Commands [Arguments]:
   initialize_keyboard
   brightness [1-3]
   single_static [color]
   single_strobe [color] [speed]
   single_breathing [color] [speed]
   colorcycle [speed]
   rainbow [speed]
   raindrop [speed]
```
Color can be any three-color hex code such as ff0000 for red or ffffff for white.  
Speed can be any integer from 1-3.

I believe this is all of the supported modes for this laptop. Let me know if I'm missing any.

It also supports these simple shortcut commands for simple static colors:
```
   red
   green
   blue
   yellow
   orange
   gold
   cyan
   magenta
   pink
   white
   black
```
I have found that upon boot you will likely need to run (if permissions error run with sudo):
```sh
zenauracore initialize_keyboard
```
You can then change the color of the keyboard by passing the argument single_static followed by the hex color code:
```sh
zenauracore single_static 0000ff
zenauracore single_static 00ff00
zenauracore single_static ffff00
```
You can also pass in any supported color above as an argument:
```sh
zenauracore red
```

If your keyboard remains dark, its brightness might have defaulted to 0. Try:
```sh
zenauracore brightness 3
```

## Dependencies

### Ubuntu

In all cases you will need `libusb` and `libusb-dev` installed:
```sh
sudo apt install libusb-1.0-0 libusb-1.0-0-dev
```
Optionally you might also need build tools:
```sh
sudo apt install build-essential
```

### Arch

```sh
sudo pacman -S libusb
sudo pacman -S base-devel
```

## Installation

```sh
git clone https://github.com/Novaryu/zenauracore
cd zenauracore
autoreconf -i
```

Then configure, make and install:
```sh
./configure
make
sudo make install
```
Remember to either reload the udev rules or reboot for the changes to take effect.
