# ZX Interface 2 custom multi ROM catridge
Another custom ROM cartridge for ZX Interface 2, supporting 256kb EPROM with manual ROM selection using switch. The 256kb EPROM can hold up to 4 16kb banks, which is selectable with a switch combination.
This cartridge only supports 16KB images and manual bank switch and no paging out - it behaves just as the original ROM catridges.

## Schema and PCB version 1
Just a simple schema created with KiCad from description of original Interface 2 and Roms as found on the internet.

| SCHEMA | PCB |
| ------ | --- |
|<img width="500" alt="image" src="https://github.com/thomasheckmann/zx-interface-2-rom/assets/14136378/24d9d5d2-00fc-4982-a62f-d98555bc82f8">|<img width="500" alt="image" src="https://github.com/thomasheckmann/zx-interface-2-rom/assets/14136378/fd5c1722-be26-4a0e-b76c-133080a56d07">|

Assembled the cartridge looks like this

<img width="500" alt="image" src="https://github.com/thomasheckmann/zx-interface-2-rom/assets/14136378/98390b0a-0d1a-49b4-8ea4-dc8fd6eeafcf">

## PCB version 1.1
Even that the first version of the PBC works ok, a few errors was made - but again I'm new to KiCad, so I'm slowly learning :-)

- Most important error is that I forgot to check the pads, I simply forgot to check that the pads are added to the solder mask layer! So as can be seen on the image, I had to carefully scrabe the surface - for the pads to be visible.

- The switch are "mirrored" in my oppinion, I would expect the left switch to be the most significant bit (MSB) - so another change for next version.

- Slot in connector turned out to be a bit too narrow, so I had to make it a bit wider.

- If you look closely vias are placed between the connector pads, in next version that will be avoided - by adding safe zones between all pads.

- Resistor value changed from 4K7 to 10K, suggested as the EEPROM is CMOS and not TTL.

- EEPROM rotated so it has same orientation as the other IC (stupid yes, but important to some like me)

- Changed PCB from 4 to 2 layers (Only used 4 to reduces the number of vias created between pads)

With these changes version 1.1 of this little PCB ends up like this:

| <!---> | <!---> |
| ------ | ------ |
|<img src="https://github.com/thomasheckmann/zx-interface-2-rom/assets/14136378/3ecfddf8-48ed-49c6-b536-00d8d13c5ec7" width="500"/>|<img src="https://github.com/thomasheckmann/zx-interface-2-rom/assets/14136378/a1923019-f344-4d02-9720-eff2e236e8e6" width="500"/>|

And here how it looks like when build and attached to a ZX Spectrum

| <!---> | <!---> |
| ------ | ------ |
|<img src="https://github.com/thomasheckmann/zx-interface-2-rom/assets/14136378/94ab6a40-55e5-43df-91f7-bf072351550d" width="500"/>|<img src="https://github.com/thomasheckmann/zx-interface-2-rom/assets/14136378/0b4fb879-edc7-415a-9ce8-14aa38968d2d" width="500"/>|

## How to create image for EEPROM
The W27C512 EEPROM can contain 4 x 16Kb images - selectable with the switch, forming the binary number 0-3 of the bank active.

For Windows
```
COPY /B ROM_3+ROM_2+ROM_1+ROM_0 IMAGE.BIN
```
Use your favorite (E)EPROM programmer to transfer the IMAGE.BIN to the EEPROM

```
LEFT|RIGHT
OFF | OFF - 0: ROM_0
OFF | ON  - 1: ROM_1
ON  | OFF - 2: ROM_2
ON  | ON  - 3: ROM_3
```
## PCB version 1.2
Only small changes to v1.2 of the board, which I think now can be considered final.

- Changed from pull-ups to pull-downs, to match actual behaviour of DIP-SWITCH (up = 1/ON/HIGH, down = 0/OFF/LOW)
- Made PADS 2mm longer, as some connectors might have issues with the smaller size

| SCHEMA | PCB |
| ------ | --- |
|<img width="500" src="https://github.com/thomasheckmann/zx-interface-2-rom/assets/14136378/6fc38f5d-754c-4e6b-84c2-64827928ea93">|<img width="500" src="https://github.com/thomasheckmann/zx-interface-2-rom/assets/14136378/57d7350c-4b89-4942-81d7-d956b0ae1a11">|

## How to create image for EEPROM
The W27C512 EEPROM can contain 4 x 16Kb images - selectable with the switch, forming the binary number 0-3 of the bank active.

For Windows
```
COPY /B ROM_0+ROM_1+ROM_2+ROM_3 IMAGE.BIN
```
Use your favorite (E)EPROM programmer to transfer the IMAGE.BIN to the EEPROM
```
LEFT|RIGHT
OFF | OFF - 0: ROM_0
OFF | ON  - 1: ROM_1
ON  | OFF - 2: ROM_2
ON  | ON  - 3: ROM_3
```
