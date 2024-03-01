# Configuring the Espressif ESP32-S3-Box3 to work with voice_assistant: and touchscreen: in ESPHome.


https://github.com/BigBobbas/esphome_firmware/assets/150487209/87153460-f26b-4b4f-b243-a4ee599c5156


>In this guide I will show the steps required to make both Voice assistant and Touchscreen work using ESPHome

First you will need to flash the S3 Box with the ESPHome stock firmware found [Here](<https://github.com/BigBobbas/esphome_firmware/blob/main/S3box3_personalised_in_progress/esp32-s3box3-esphome.yaml>) This is an edited config to allow you to install using ESPHome dashboard short video [Here](<https://github.com/BigBobbas/esphome_firmware/blob/main/S3box3_personalised_in_progress/ESPHome%20Dashboard%20.mp4>) showing how to manually add a config to the dashboard. (or your prefered method) I Have also included a [.bin file](<https://github.com/BigBobbas/esphome_firmware/blob/main/S3box3_personalised_in_progress/esp32-s3-box-3-factory.bin>)
- Once installed, establish connectivity with HA and confirm that Voice_assistant is working.
- Reboot the device and edit the config yaml adding the following.
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
I have added 3 touch areas across the top row of the screen as an example. Further information for configuring touch can be found [Here](<https://esphome.io/components/touchscreen/index.html>)

Save and install the configuration and watch the logs that follow flashing. tap on the 3 locations and observe the logs to confirm that these register as button presses.

![image](https://github.com/BigBobbas/esphome_firmware/assets/150487209/7cc2f3e9-e660-4fda-8f00-0ea5ed89e6b5)

Now check that Voice_assistant is also working. If not, reboot the device and test all functionaility again.
If voice or touch are not working still, then do the following.
- comment out the whole yaml you added above.
- save the configuration and exit the editor
- Click on the 3 dot menu of the device card and click 'clean build files' everytime you comment out or add components to a built configuration, make sure to clean build files or you will get an error at the end of compiling and have to clean and compile again (a trait with esp-idf framework)
- save and install and test voice. if all is working then uncomment the code and save and install again then test. 
Removing power to the device once fully working will cause voice to stop functioning and you will need to follow the steps of commenting out the above code, re-installing and repeating if necessary.

I have found that once the device is up and running and functioning with touch and voice, editing the config, for example adding a touch binary button will cause touch not to function after flashing. Carrying out a soft reset/reboot will rectify this. I have added the yaml below to add a 'Reboot' button to the HA inetgration or can be used in an automation on the device for instance assigning to the top left side button on the device.
I use the sensor base with a battery installed to save having to power off the device should I need to unplug it.

## Extras
Presence Sensor (basic binary sensor)
```yaml
binary_sensor:
  - platform: gpio
    pin:
      number: GPIO21
    name: "Presence detect"
    disabled_by_default: false
    device_class: "occupancy"
```
AHT20 - Temperature & Humidity
```yaml
sensor:
  - platform: aht10
    i2c_id: bus_b
    variant: AHT20
    temperature:
      name: "Temperature"
    humidity:
      name: "Humidity"
    update_interval: 5s
```
Soft Reboot button
```yaml
button:
  - platform: restart
    id: reboot
    name: "Reboot"
```


