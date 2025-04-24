# HA_Configs
[Home Assistant](https://www.home-assistant.io/) [ESPHome Configs](https://esphome.io/)

## Ant Sig IR Blaster

Buy it from [Bunnings](https://www.bunnings.com.au/antsig-grid-connect-smart-ir-universal-remote-controller_p0118693)
Configure and flash via [ESPHome](https://devices.esphome.io/devices/Antsig-Grid-Connect-Smart-IR-Universal-Remote)
 Note you'll need to solder a FTDI USB to UART to flash the MCU, maybe something like [this](https://core-electronics.com.au/usb-to-uart-converter-cp2102.html)
 
[ir_blaster.yaml](https://github.com/zxrossco/HA_Configs/blob/main/ir_blaster.yaml)

I use this to drive my AC which is a generic box AC from [TECO](https://appliances.teco.com.au/product/teco-5-3kw-inverter-window-wall-air-conditioner/).  Seems that many box AC units come out of a Chinese factory [GREE](https://global.gree.com/).  So I get nice integration with Home Assistant


## PowerPal

Victoria, Australia some years back upgraded everyone to Smart Meters and the solution for home monitoring was sourced through a 3rd party [powerpal](https://www.powerpal.net/).  It requires a cloud connection and their app which is nice and all but I want the data.  

So Home Assistant and ESPHome to the rescue [powerpal.yaml](https://github.com/zxrossco/HA_Configs/blob/main/powerpal.yaml)

You'll need to get the Bluetooth MAC Code of the Powerpal dongle and the pairing code.

The batteries in the dongle had died after some years so the casing was removed and a new set of batteries installed.  This necessitated a new case as it was a sealed unit.

## Presence 

[presence.yaml](https://github.com/zxrossco/HA_Configs/blob/main/presence.yaml) Contains the config for a LD2410 mmWave sensor [like this](https://hlktech.net/index.php?id=988).
Manual for the LD2410 
Adding a PIR too
![LD2410 Image](https://github.com/zxrossco/HA_Configs/blob/main/LD2410.png)
![PIR Image](https://github.com/zxrossco/HA_Configs/blob/main/PIR-Sensor-Pinout.png)

[This](https://www.printables.com/model/703427-mmwave-case-for-ld2410) seems like a workable case 

## Wake Word

[wakeword.yaml](https://github.com/zxrossco/HA_Configs/blob/main/wakeword.yaml) is my ESPHome config of Micro Wake Word running on a Seeed XAIO ESP32S3 Sense.  This config has no local speaker so I'm routing the response back through Home Assistant.

## Seeed XIAO ESP32S3 Sense Camera

[xiao_seeed_sense.yaml](https://github.com/zxrossco/HA_Configs/blob/main/xiao_seeed_sense.yaml) is a ESPHome configuration for the Camera (use the Mic config from wakeword.yaml)  Gives you a functional streaming Camera in Home Assistant, quality wise you get the images you pay for.  I ended up using TP-Link TAPO Cameras in Home Assistant.  The Seeed Sense boards were retasked to listen for Wake Words and STT.

