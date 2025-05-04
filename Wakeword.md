# Wakeword Sensor

## DF0327

### MSM261S4030H0

### Pinout
| Pin | ESP32 | Function |
|-----|-------|----------|
| V   | +V | Supply 1.8 to 3.3 V. This pin should be decoupled to Pin 1 with a 0.1 μF capacitor and a 10μF capacitor. |
| G | Gnd | Gnd |
| WS | ?? | Serial Data‐Word Select for I²S Interface. |
| LR | GND | Left/Right Channel Select. When set low, the microphone outputs its signal in the left channel of the I²S frame; when set high, the microphone outputs its signal in the right channel. |
| CK | ?? |Serial Data Clock for I²S Interface |
| DA | ?? | Serial Data Output for I²S Interface. This pin tristates when not actively driving the appropriate output channel. The SD trace should have a 100 kΩ pull‐down resistor to discharge the line during the time that all microphones on the bus have tristated their outputs.|

### I²S DATA INTERFACE   
The serial data is in slave mode I²S format, which has 24‐bit depth in a 32 bit word. In a
stereo frame there are 64 SCK cycles, or 32 SCK cycles per data‐word. When L/R=0, the output
data in the left channel, while L/R=Vdd, data in the right channel. The output data pin (SD) is
tri‐stated after the LSB is output so that another microphone can drive the common data line.   

### Data Word Length   
The output data‐word length is 24 bits per channel. The Mic must always have 64 clock
cycles for every stereo data‐word (fSCK = 64 × fWS).   

### Data‐Word Format   
The default data format is I²S, MSB‐first. In this format, the MSB of each word is delayed by
one SCK cycle from the start of each half‐frame.

```
i2s_audio:
  - i2s_lrclk_pin: GPIO23
    i2s_bclk_pin: GPIO22

speaker:
  - platform: i2s_audio
    id: speaker_out
    dac_type: external
    i2s_dout_pin: GPIO19
    mode: mono

microphone:
  - platform: i2s_audio
    id: microphone_in
    i2s_din_pin: GPIO21
    adc_type: external
    channel: left
    pdm: false
````
