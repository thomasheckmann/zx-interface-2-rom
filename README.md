# zx-interface-2-rom
Another custom ROM cartridge for ZX Interface 2, supporting 256kb EPROM with manual ROM selection using switch. The 256kb EPROM can hold up to 4 16kb banks, which is selectable with a switch combination.

## schema and PCB version 1
Just a simple schema created with KiCad from description of original Interface 2 and Roms as found on the internet.

| SCHEMA | PCB |
| ------ | --- |
|<img width="480" alt="image" src="https://github.com/thomasheckmann/zx-interface-2-rom/assets/14136378/24d9d5d2-00fc-4982-a62f-d98555bc82f8">|<img width="480" alt="image" src="https://github.com/thomasheckmann/zx-interface-2-rom/assets/14136378/fd5c1722-be26-4a0e-b76c-133080a56d07">|

Assembled the cartridge looks like this

<img width="602" alt="image" src="https://github.com/thomasheckmann/zx-interface-2-rom/assets/14136378/98390b0a-0d1a-49b4-8ea4-dc8fd6eeafcf">

## PCB version 2
Even that the first version of the PBC works ok, a few errors was made - but again I'm new to KiCad, so I'm slowly learning :-)

Most important error is that I forgot to check the pads, I simply forgot to check that the pads are added to the solder mask layer! So as can be seen on the image, I had to carefully scrabe the surface - for the pads to be visible.

The switch are "mirror" in my oppion, I would expect the left switch to be the most significant bit (MSB) - so another change for next version.

<img width="602" alt="image" src="https://github.com/thomasheckmann/zx-interface-2-rom/assets/14136378/3ecfddf8-48ed-49c6-b536-00d8d13c5ec7">

