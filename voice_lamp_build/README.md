### This is my project to take a broken lamp/room atomiser and convert it to a multi sensor with integrated voice assistant.
![20240217_224832](https://github.com/BigBobbas/esphome_firmware/assets/150487209/9467379c-cc30-4fa0-8d69-1bf85fde5fcf)


**Parts :-**
- Faulty lamp carcass
- WS8212b Led's ring, matrix or strips (undecided)
- esp32 c3 supermini - for WLED controller - untested
  >installed tested and working. Thinking of trying it with ESPhome next
- esp32 s3 N16R8 for Voice and sensors
  >added 2 x 1 for esp-idf and 1 for arduino frameworks to allow for media player.
  >**Edit now only using 1 x ESP32-S3 - I have now changed to using ESP-IDF Media Player which has removed the need for a seperate arduino framework device.
- BH1750 - lux sensor
- AHT20 / BMP280 - Temperature, Humidity, Pressure
- LD2410c Radar mmwave presence sensor
- TP2422 Touch sensor / button 
  >added touch ring to top of lamp using esp32 touch pin instead
- SSD1306 OLED (possibility if can install and keep it aesthetically pleasing)
  > oled is installed and functioning


**Operation :-**
- Light to operate as a flame / candle effect in normal use. Turn on or off with long press of the touch button.
- Light will automate to 'normal' on state upon detection of presence if the light level is below the pre-defined threshold.
- Light will automate to off state when the still energy falls below the calibrated defined threshold and time delay of x
- Short press of button will allow voice command without wakeword, button release will return VA to previous state. **Edit this is now using the touch ring
- wakeword detect will change led colours/effect to indicate wakeword has been detected.
- VA Mute on double press possibly - may add another button. Mute is operated from existing button on the base collar
- Oled display to show time / room temp + heating set temp / outside temp / VA in progress / VA Mute or active
- Lamp light to indicate - person on the drive - doorbell pressed - washing machine finished - dryer finished - along with voice alerts. **Edit also added broadcast from HA dashboard


