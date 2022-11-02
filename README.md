# Resolume Timecode
Touchdesigner Application that generates LTC timecode based on Resolume timeline

Problem: Resolume can't send LTC timecode based on clip playback. A workaround is baking in timecode on one of the audio channels but then you lose stereo audio and have to render each movie file with timecode embedded (or do a collumn trigger).

<h1>How this works</h1>

This is a little Touchdesigner program that listens to Resolume OSC commands. When a new clip is triggered, it asks Resolume for the clip name.
If the name starts with <b>TC1</b> it will start sending LTC timecode starting from 1:00:00:00 based on the resolume clip playback. <b>TC2</b> will start the timecode on 2:00:00:00

<h1>Tutorial</h1>

- Enable Resolume OSC input and output
- Edit the resolume IP and OSC ports in the "ResolumeTimecodeGenerator" Base in Touch Designer
- Chose your audio interface and enable the output, you can change the channels inside the Base in the "audiodevout1"
- Rename the Resolume clips you want to send timecode to "TC0 NAME" to send timecode from 0:00:00:00 (and TC1 for 1:00:00:00, ... , TC23 for 23:00:00:00)

<h1>Limitations</h1>
It's possible timecode triggers at the start (for example 00:00:00:00 when you use TC0) don't work. The program has to detect the clip change and then ask the clip name and duration. So it's possible there is a very small delay when the clip is triggered and it only starts sending timecode a few frames later (workaround: set your timecode triggers a few frames later (for example 00:00:00:05) so the program has time to start sending timecode)
