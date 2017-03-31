fake-backlight shouldn't exist, but does.

fake-backlight fakes a backlight for your display
  - because you can't control it any other way in linux
  - because acpi is hard
  - because your oem sucks
  - because your eyes hurt
  - because life is pain

what on earth is this?

if you have a bleeding-edge laptop from certain manufacturers,
you might not be able to control the backlight brightness. 
you might have tried a hundred random hacks, none of which
helped, and linux doesn't have some esoteric driver for your
system either.

if you have a /sys/class/backlight/acpi_video0, but it does
nothing, fake-backlight can help until someone figures out
what insane thought process your oem went thru to arrive at
their decision to not support the acpi standard. hopefully
the developer trying to resolve the problem without any
documentation doesn't off themselves in the process.

fake-backlight works with GNOME, and will use xrandr to control
the software brightness of the display when you change the
backlight using the hotkeys or other method. it sets up a
listener for relevant d-bus signals and will fake a backlight
as needed.

it works, it sucks, too bad :(  at least your eyes won't hurt
from the screen, instead you can hurt them trying to reverse
engineer the oem's acpi implementation and associated drivers.

tested on the razer blade pro 2016 with ubuntu yakkety.


install like a hax0r:

```bash
sudo pip3 install pydbus;
mkdir -p ~/.config/systemd/user;
cp fake-backlight.service ~/.config/systemd/user;
sudo cp fake-backlight /usr/local/bin/;
systemctl --user enable fake-backlight;
systemctl --user start fake-backlight;
```

hopefully i'll figure out wtf razer did to the backlight
controls, but this should help for now and hopefully for
other laptops facing the same issue. i wish they would
answer my emails :(


