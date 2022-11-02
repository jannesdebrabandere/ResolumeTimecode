# Resolume Timecode
Touchdesigner Application that generates LTC timecode based on Resolume timeline

Problem: Resolume can't send LTC timecode based on clip playback. A workaround is baking in timecode on one of the audio channels but then you lose stereo audio and have to render each movie file with timecode embedded (or do a collumn trigger).

#How this works
This is a little Touchdesigner program that listens to Resolume OSC commands. When a new clip is triggered, it asks Resolume for the clip name.
If the name starts with <b>TC1</b> it will start sending LTC timecode starting from 1:00:00:00 based on the resolume clip playback. <b>TC2</b> will start the timecode on 2:00:00:00

#Tutorial
- Enable Resolume OSC input and output
- Edit the resolume IP and OSC ports in the "ResolumeTimecodeGenerator" Base in Touch Designer
- Chose your audio interface and enable the output, you can change the channels inside the Base in the "audiodevout1"
- Rename the Resolume clips you want to send timecode to "TC1 NAME"
