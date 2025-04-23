# MCUs used in my Home Assistant setup

## Seeed Studio XIAO ESP32S3

[https://www.seeedstudio.com/XIAO-ESP32S3-p-5627.html]


Onboard LED
```
output:
  - platform: ledc
    pin: GPIO21
    inverted: true
    id: led_output
```

UART
```
uart:
  id: ld2410_uart
  tx_pin: GPIO4
  rx_pin: GPIO5
  baud_rate: 57600 #256000
  data_bits: 8
  stop_bits: 1
  parity: NONE
```

## Seeed Studio XIAO Sense Camera

[https://www.seeedstudio.com/XIAO-ESP32S3-Sense-p-5639.html]

I2S Microphone
```
i2s_audio:
  - id: i2s_microphone
    i2s_lrclk_pin: GPIO42

microphone:
  - platform: i2s_audio
    i2s_audio_id: i2s_microphone
    id: echo_microphone
    i2s_din_pin: GPIO41
    adc_type: external
    bits_per_sample: 16bit
    pdm: true
    channel: left
```
Camera
```
esp32_camera:
  #name: XIAO Camera
  external_clock:
    pin: GPIO10
    frequency: 20MHz
  i2c_pins:
    sda: GPIO40
    scl: GPIO39
  data_pins: [GPIO15, GPIO17, GPIO18, GPIO16, GPIO14, GPIO12, GPIO11, GPIO48]
  vsync_pin: GPIO38
  href_pin: GPIO47
  pixel_clock_pin: GPIO13

  # Image settings
  name: Camera 1
  # ...

  #reset_pin: GPIO1
  #power_down_pin: GPIO2
  resolution: 640x480
  jpeg_quality: 10
  max_framerate: 10 fps
  idle_framerate: 0.2 fps
  #vertical_flip: true
  #horizontal_mirror: true
```


  ## Seeed XIAO ESP32C3 RISC-V

  [https://www.seeedstudio.com/Seeed-XIAO-ESP32C3-p-5431.html]

  
  
