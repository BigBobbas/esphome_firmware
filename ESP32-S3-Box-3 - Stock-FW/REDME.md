## ESPHome - ESP32-S3-Box-3 .bin manual install process
1. Download the [s3b_stock.bin](<https://github.com/BigBobbas/esphome_firmware/blob/main/ESP32-S3-Box-3%20-%20Stock-FW/s3b_stock.bin>) file
2. go to https://web.esphome.io
3. connect your S3 Box 3 to your computer with a usb DATA cable
4. click connect <br>![image](https://github.com/user-attachments/assets/93794a42-6712-405e-b87e-218ac95dd43a)<br><br>
5. Choose your com port - it will be similar to the one in the screenshot below but the port number will be different <br>
![image](https://github.com/user-attachments/assets/4d7bb0fd-fbcd-4942-b395-25bd171d5108)<br><br>
6. Click install <br>![image](https://github.com/user-attachments/assets/9238005d-d1de-4244-bc79-dbf39025ae7f)<br><br>
7. browse to the .bin file that you saved, then click install<br><br>
![image](https://github.com/user-attachments/assets/074b99cc-0314-4999-923b-a2ff266142e6)<br><br>
![image](https://github.com/user-attachments/assets/e7b13495-7ce1-4373-8680-9bf2700c094e)<br><br>
![image](https://github.com/user-attachments/assets/34477c5d-5937-4762-8ae1-0a66ce2dd746)<br><br>
You should then get 'connecting' followed by 'erasing' and then the install will start<br><br>
![image](https://github.com/user-attachments/assets/98c6dfc9-d83f-41c4-b917-3f0c6c31eb41)<br><br>
![image](https://github.com/user-attachments/assets/872d4cd5-b22e-42d2-8594-256f68ec24ad)<br><br>
8. From a wifi enabled device, scan for wireless networks and connect to esp32-s3-box-3 - this is an open network and the devices access point.
9. Once connected open a browser and type the following url in the address bar http://192.168.4.1/ <br><br>
You should now see a list of available wireless networks that the device can connect to.<br><br>
![image](https://github.com/user-attachments/assets/92d05d5e-bde3-4a04-8e10-66b3f3f913cc)<br><br>
Once connected - on the computer that you connected to disconnect from esp32-s3-box-3 and connect to your usual network.
The box should now be connected to your wireless network and you can continue to add the device to Home Assistant.










