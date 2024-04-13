Video Demo here https://youtube.com/shorts/SqN-0dx5RhM?si=qapFh7S1hyZQu1GR

This little thing is great ... who can resist wearing your ESPHome device and controlling your home from your wrist.
I still have some work to do with screens and menus etc, but with all ESPHome devices the possibilities are endless. 
Bare in mind that this is a development device and not intended as an off the shelf product that you can go mountain climbing and scuba diving in, however I think the screen is nice and clear and bright, the watch construction feels fairly robust. Strap... meh! get used to it. 

I'm using tap to talk rather than wake word for the voice assistant as I think it's more convenient on the wrist. However I do intend to try out micr_wake_word too, just for a test. 

I haven't yet got components for :- (if anyone is willing to hel pout with this , that would be awesome - more than anything the AXP2101 would be make this even more useable)

      AXP2101  - Power management IC
      DRV2605 - Haptic Motor
      BMA423  - Accelerometer 

Things I would like to try but have no clue yet if they will work, is to see if I can connect to my phone hotspot and either use vpn on my phone or wireguard on the watch to connect to home, for when i'm out and about. I don't need it ... it would just be good to check out the possibilities. 

Watch purchased  here >> https://www.aliexpress.com/item/1005005714764027.html
resources and schematics here https://github.com/Xinyuan-LilyGO/TTGO_TWatch_Library/tree/t-watch-s3

display is :-
    platform: ili9xxx
    model: ST7789V

touch :-
platform: ft63x6

Audio :-
 Max98537 DAC 
 PDM Mic

currently running ESPHome 2024.4.0b2
ADF Pipeline from @Mischa https://github.com/gnumpi/esphome_audio
basic config - so far can be found here, (I've not tidied it up yet so excuse the mess)  https://github.com/BigBobbas/esphome_firmware/tree/main/lilygo%20T-Watch%20S3 I have only just started on the display side of things so this is only a very quickly put together lay out , it's a full colour display but Ive opted for mainly B&W because it's clear and easy to read/see. however I will be adding colour to the button / sensor states. 

The wifi and HA logo on the front screen both change to indicate that wifi and api are connected. the esphome logo is just a graphic, and at the moment the battery icon tells lies as there is no actual monitoring currently.  The top 3/4 of the screen on the home page are long press 'tap to talk' and the bottom takes you to the device control screen. I have tested functionality and everything works, but I haven't added all triggers / states etc as yet. 

I'm still experimenting with click times etc to make it better. and I have also tested deep sleep and waking on tap which works well. However I want to test and see how well the battery lasts by just having the backlight off so that I can receive media player tts notifications, for the doorbell, washing machine finished, person detected at the front of the house etc etc 
