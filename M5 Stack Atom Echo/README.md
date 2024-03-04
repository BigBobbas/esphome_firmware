## M5 Stack Atom echo - ESPHome Voice Assistant
>This configuration is an edited version of the offical config that can be flashed via the ESPHome web installer.
>The alternative method here allows you to add the full config to the ESPHome dashboard you can then easily make changes to the config. The ESPHome web installer only includes a basic configuration which doesn't easy allow for customisation. I will describe two methods for installation below.

* Method 1 - use this method if you already have the device installed and running and your device card in the ESPHome dashboard only contains the minimal config.
 

https://github.com/BigBobbas/esphome_firmware/assets/150487209/1fd827ec-4f0a-4113-8022-06947171df24

 
  
  1 click edit on the device card in the dashboard.
  2 Press CTRL & A on your keyboard to 'select all' 
  3 Press delete o your keyboard.
  4 Copy the code  from [here](<https://github.com/BigBobbas/esphome_firmware/blob/main/M5%20Stack%20Atom%20Echo/m5stack-echo-stock-esphome.yaml>)
  5 paste the config into the now blank edit page.
  6 make any changes required * note that if the device has previously been added to HA then you will need to change the name: for the device to avoid any issues with HA being unable to connect to the device, you will also need to make sure that api: encryption key is copied across and any other relevant credentials.
  7 Click save and install
  8 Select the upload method applicable to your.
  9 Once the config has been uploaded the comple log window should proced do display the logs, if the logs do not show, then exit the editor and try again by clicking on 'logs'

 * Method 2 - you have no device in the dashboard and need to creat a device card.
   
