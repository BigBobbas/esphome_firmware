## ESP32Dev INMP441 Test yaml
For ESPHome and Home Assistant - Voice Assistant

This is a basic functioning yaml I use for testing the functionality of the INMP441 I2s Microphone with a variety of ESP32 boards.

in order to test that audio is being streamed to Home Assistant and to check the quality of the sound, follow the steps below.

How to enable audio recording to allow playback for diagnosis
REMEMBER TO DISABLE ONCE YOU HAVE SOME SAMPLES TO PLAY BACK 
the best way I have found of doing this is :-
Unplug the device and follow the steps here https://www.home-assistant.io/voice_control/troubleshooting/#to-tweak-the-assist-audio-configuration-for-your-device you can change the dir to a path that HA and you can access from a pc

- Once you have restarted HA have the /share/assist_pipeline folder open on your desktop
- plug in the device and start talking / making a noise, it will basically be an 'open mic' and will record 5 second snippets every 5 seconds.
- You will see folders and files created in the shared folder. Once you have a number of files then unplug the device.
- IMPORTANTComment out the lines you entered to configuration.yaml  save and restart HA - if you do not do this then files will be 5. created indefinitely and gradually fill up your storage. It is only required to have this active for testing.
- Click through the various wav files and listen to the audio . it should be clear , with little background noise and of a good volume with as little distortion as possible.
