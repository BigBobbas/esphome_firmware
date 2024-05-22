## M5 Stack Atom echo & ESP32-S3-Box-3 -  ESPHome Voice Assistant
>This configuration is an edited version of the offical config that can be flashed via the ESPHome web installer.
>The alternative method here allows you to add the full config to the ESPHome dashboard you can then easily make changes to the config. The ESPHome web installer only includes a basic configuration which doesn't easy allow for customisation. I will describe two methods for installation below. These methods are not exclusive to the M5 Stack Atom Echo and can be applied to any ESPHome device.

The ESPHome dashboard should not be confused with the ESPHome integration. The dashboard (add-on) is not required for a device to work and be controlled by HA it is purley a way of creating device configurations (firmware) in order to make the device useable. The integration is how the configured device is installed into HA and the sensors and controls are exposed for you to use. Although the dashboard does not play a part in the running of devices in HA it does enable you to keep your device configs in one place and allows you to view device logs easily.

There are various methods of running ESPHome for configuring and uploading firmware to the device. Documents for these methods can be seen [here for the docker command line install](<https://esphome.io/guides/getting_started_command_line.html>) , [here for windows, mac & Linux](<https://esphome.io/guides/installing_esphome>) and  [here for HA add-on](<https://esphome.io/guides/installing_esphome>)

* Method 1 - use this method if you already have the device installed and running and your device card in the ESPHome dashboard only contains the minimal config.
 

https://github.com/BigBobbas/esphome_firmware/assets/150487209/1fd827ec-4f0a-4113-8022-06947171df24

 
  
  1. click edit on the device card in the dashboard.
  2. Press CTRL & A on your keyboard to 'select all' 
  3. Press delete on your keyboard.
  4. Copy the code  from [here](<https://github.com/BigBobbas/esphome_firmware/blob/main/M5%20Stack%20Atom%20Echo/m5stack-echo-stock-esphome.yaml>) for the M5 Stack Atom Echo or [here](<https://github.com/BigBobbas/esphome_firmware/blob/main/ESPHOME%20ESP32-S3-Box-3/esp32-s3box3-esphome.yaml>) for the S3box
  5. paste the copied config into the now blank edit page by pressing CTRL & V
  6. make any changes required * note that if the device has previously been added to HA then you will need to change the name: for the device to avoid any issues with HA being unable to connect to the device, you will also need to make sure that api: encryption key is copied across and any other relevant credentials. To avoid issues delete the previously installed device in the ESPHome integration if this is applicable.
  7. Click save and install
  8. Select the upload method applicable to your.
  9. Once the config has been uploaded the comple log window should proced do display the logs, if the logs do not show, then exit the editor and try again by clicking on 'logs' on the device card.

 * Method 2 - you have no device in the dashboard and need to create a device card.
   
https://github.com/BigBobbas/esphome_firmware/assets/150487209/b9a26691-4a4f-4097-8192-abedbbb2ae77

  1. click 'NEW DEVICE' in the bottom right of dashboard.
  2. Give the device a name, HA will use this name as the hostname to connect to the device in the format device-name.local if you are re-using an ESP board that has been added to HA previousl, make sure to delete the existing device first from the ESPHome integration in HA. Names must be in lowercase and can only contain "-" to seperate multiple words, numbers are also allowed in the device name.
  3. The board that you select is not important as you will manually configure this in the device config, select any board and click next.
  4. At the encryption screen click skip as you do not want to install at this point.
  5. A new device card should now be showing in the dashboard, click edit.
  6. you will now see the base config that was created when carrying out the previous steps. Press CTRL & A to select all and then press delete.
  8. Copy the code  from [here](<https://github.com/BigBobbas/esphome_firmware/blob/main/M5%20Stack%20Atom%20Echo/m5stack-echo-stock-esphome.yaml>) for the M5 Stack Atom Echo or [here](<https://github.com/BigBobbas/esphome_firmware/blob/main/S3box3_personalised_in_progress/esp32-s3box3-esphome.yaml>)
  9. paste the copied config into the now blank config card by pressing CTRL & V
  10. make any changes required * note that if the device has previously been added to HA then you will need to change the name: for the device to avoid any issues with HA being unable to connect to the device (use the name: previously installed to the device, you will also need to make sure that api: encryption key is copied across and any other relevant credentials.
  11. Click save and install
  12. Select the upload method applicable to your setup.
  13. Once the config has been uploaded the comple log window should proced do display the logs, if the logs do not show, then exit the editor and try again by clicking on 'logs' on the device card

