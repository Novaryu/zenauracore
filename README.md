# zenauracore - RGB keyboard control for the Asus Zenbook UX7602ZM

Linux-compatible open-source libusb implementation forked from [rogauracore](https://github.com/wroberts/rogauracore).

Supports the Zenbook RGB keyboard with ID [0b05:8854](https://linux-hardware.org/index.php?id=usb:0b05-8854)

## Usage

```
Usage:
   zenauracore COMMAND ARGUMENTS

COMMAND should be one of:
   single_static
   red
   green
   blue
   yellow
   gold
   cyan
   magenta
   white
   black
   brightness
   initialize_keyboard
```
There are currently more modes supported by this laptop but I have not reverse-engineered them yet. Hopefully more to come.

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
Certain colors also work just like in rogauracore:
```sh
zenauracore red
```

If your keyboard remains dark, its brightness might have defaulted to 0. Try:
```sh
sudo zenauracore brightness 3
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
