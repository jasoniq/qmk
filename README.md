# QMK

Docker compose setup for compiling QMK firmware

## Setup

Clone the official QMK firmware repo into the `qmk_firmware` directory.
A custom fork also works, as long as it's cloned into teh `qmk_firmware` directory.

```
git clone https://github.com/qmk/qmk_firmware qmk_firmware
```

## Usage

Launch the docker image and exec directly into the running container.
Then run the desired QMK commands from directly within the docker container.

```
docker compose up -d
docker exec -it qmk_cli bash
qmk compile -kb <keyboard_name> -km <keymap_name>
```

Note: flashing directly from docker may not work.

## Example

Compiling a new firmware to install on Boardsource Corne keyboard with Blok RP2040 module.

```
qmk compile -kb crkbd/rev1 -km default -e CONVERT_TO=blok
```

This will output a `u2f` firmware flash file into the root of the `qmk_firmware` directory which
can be manually copied directly onto your keyboards bios storage to manually flash.

## References

 - docs https://docs.qmk.fm/
 - configurator https://config.qmk.fm
 - firmware https://github.com/qmk/qmk_firmware/tree/master/keyboards/crkbd/rev1
