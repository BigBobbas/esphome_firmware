# H1 Voice Assistant mic audio testing For ESPHome and Home Assistant - Voice Assistant

in order to test that audio is being streamed to Home Assistant and to check the quality of the sound, follow the steps below.

**REMEMBER TO DISABLE ONCE YOU HAVE SOME SAMPLES TO PLAY BACK - YOU MUST RESTART HOME ASSISTANT TO TAKE EFFECT, DON'T JUST RELOAD YAML** 

*the best way I have found of doing this is :-*

- Unplug the device and follow the steps [here](https://www.home-assistant.io/voice_control/troubleshooting/#to-tweak-the-assist-audio-configuration-for-your-device) you can change the dir to a path that HA and you can access from a pc - you may need to install the Samba Share addon from the Home Assistant Add-on store in order to access the share folder from your computer.
- Once you have restarted HA after editing your configuration.yaml file have the /share/assist_pipeline folder open on your desktop.
- Plug in the device and start talking / making a noise, it will basically be an 'open mic' and will record 5 second snippets every 5 seconds.
- You will see folders and files created in the shared folder. Once you have a number of files then unplug the device.
- **IMPORTANT** Comment out the lines you entered to configuration.yaml  save and restart HA - if you do not do this then files will be created indefinitely and gradually fill up your storage. It is only required to have this active for testing. You can delete all files in the assist-pipeline folder when you are finished testing.
- Click through the various wav files and listen to the audio, it should be clear , with little background noise and of a good volume with as little distortion as possible.
- if your recordings are quiet then increase the volume_multiplier: or lower if they are too loud and distorted.

  Once you are happy with the level and clarity of the audio being streamed to Home Assistant you should be good to go and your ESPHome device is functioning as it should be. If you are experiencing issues with wakeword not being detected, or voice commands not functioning, you need to look into the related services within Home Assistant. 
Samples of inmp441 recordings are available [here](https://github.com/BigBobbas/esphome_firmware/tree/main/Mic_Tests/inmp441_mic_tests)
