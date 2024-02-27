# Configuring the Espressif ESP32-S3-Box3 to work with voice_assistant: and touchscreen: in ESPHome.

>In this guide I will show the steps required to make both Voice assistant and Touchscreen work using ESPHome

First you will need to flash the S3 Box with the ESPHome stock firmware. Either manually using the yaml [Here](<https://github.com/esphome/firmware/blob/main/voice-assistant/esp32-s3-box-3.yaml>) or via web installer [Here](<https://www.home-assistant.io/voice_control/s3_box_voice_assistant/#installing-the-software-onto-the-esp32-s3-box>)

- Once installed, establish connectivity with HA and confirm that Voice_assistant is working.
- reboot the device and edit the config yaml adding the following.
```yaml
i2c:
  - id: bus_a
    sda: GPIO08
    scl: GPIO18
    scan: false
    sda_pullup_enabled: true
    scl_pullup_enabled: true
    frequency: 100kHz

  - sda: GPIO41
    scl: GPIO40
    scan: false
    sda_pullup_enabled: true
    scl_pullup_enabled: true
    frequency: 50kHz
    id: bus_b

touchscreen:
  platform: gt911
  i2c_id: bus_a
  id: gt911_touchscreen
  interrupt_pin: GPIO3

  - platform: touchscreen
    name: Top Left Touch Button
    x_min: 0
    x_max: 100
    y_min: 0
    y_max: 100
    on_press:
      - switch.toggle: mute ### add your own automation here ###

  - platform: touchscreen
    name: Top middle Touch Button
    x_min: 100
    x_max: 200
    y_min: 0
    y_max: 100
    on_press:
      - homeassistant.service:                        ####################################      
          service: switch.toggle                      ### add your own automation here ###
          data:                                       ###  ##########################  ###
            entity_id: switch.sitting_room_sockets_s2 ####################################
binary_sensor:
  - platform: touchscreen
    name: Top right Touch Button
    x_min: 200
    x_max: 300
    y_min: 0
    y_max: 100
    on_press:
      - homeassistant.service:                        ####################################      
          service: switch.toggle                      ### add your own automation here ###
          data:                                       ###  ##########################  ###
            entity_id: switch.sitting_room_sockets_s1 ####################################

```
I have added 3 touch areas accross the top row of the screen as an example. Further information for configuring touch can be found [Here](<https://esphome.io/components/touchscreen/index.html>)

Save and install the configuration and watch the logs that follow flashing. tap on the 3 locations and observe the logs to confirm that these register as button presses.

![image](https://github.com/BigBobbas/esphome_firmware/assets/150487209/7cc2f3e9-e660-4fda-8f00-0ea5ed89e6b5)

Now check that Voice_assistant is also working. If not, reboot the device and test all functionaility again.
If voice or touch are not working still, then do the following.
- comment out the whole yaml you added above.
- save and install and test voice. if all is working then uncomment the code and save and install again then test. 
Removing power to the device once fully working will cause voice to stop functioning and you will need to follow the steps of commenting out the above code, re-installing and repeating if necessary.
I use the sensor base with a battery installed to save having to power off the device should I need to unplug it.




