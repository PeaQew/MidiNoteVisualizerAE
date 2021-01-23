# MIDI Visualizer AE
<p align="center">
	<img width="256px" src="assets/logo.png">
</p>
<p align="center">
	<b>An ExtendScript tool that creates a piano roll-style MIDI note visualizer inside of After Effects.</b>
</p>


## Contents
- [Overview](#overview)
- [How To Install](#how-to-install)
- [Usage](#usage)
- [The Workflow](#the-workflow)
- [Future Versions](#future-versions)
- [Settings File](#settings-file)
- [Contact Me](#contact-me)

## Overview
This tool reads data from MIDI files (**M**usical **I**nstrument **D**igital **I**nterface) and creates visuals that simulate a scrolling piano roll, similar to the ones seen in [DAWs](https://en.wikipedia.org/wiki/Digital_audio_workstation). To achieve this, two compositions are created for each MIDI file. One of them contains all of the shapes that represent the notes, and another is responsible for scrolling them across the screen.

This, combined with [upcoming additions](#future-versions), provides an alternative to using real time MIDI visualizers or recording a video of your DAW - plus all of the features After Effects has to offer!

Initially created for personal use, but I decided to make it user-friendly enough and upload it so that everyone can use it!

**Grab the latest release [here!](https://github.com/PeaQew/MidiVisualizerAE/releases/latest)**

## How To Install
To install this script, move the script file (ending with .jsx) to the following locations:

**Windows:**
`C:\Program Files\Adobe\Adobe After Effects *(version)*\Support Files\Scripts\ScriptUI Panels`

**macOS:**
`/Applications/Adobe After Effects *(version)*/Scripts/ScriptUI Panels`

To start the script inside of After Effects, go to `Window -> midi_visualizer.jsx` (at the bottom) and the window will pop up.

## Usage
- First, select a folder containing the MIDI files that you want to process.
- Once you've chosen your folder, all found files will be listed.
  - Here you can select one or multiple MIDI files to change their properties.
  - Changes will be reflected for all selected files at once.
  - The format of the text is `comp name`(`file name`) // `selected color`.
- The settings window can be opened at any time to reveal some additional settings.
  - Hover over the labels to see more detailed explanations.
  - The settings will be applied for this session when you hit the x button and close the window.
  - Settings can be saved as default so that you don't have to set them up every time (see [Settings File](#settings-file) for more information).
- When everything is set-up, hit `Create` and let it do its thing!

## The Workflow
This script will produce a bunch of compositions, two for each MIDI file and one called 'MidiMaster'. The reason there are two compositions for each file is so that we can scroll all the notes (shape layers) effectively. The compositions that handle the scrolling of the notes are prefixed with an underscore, which makes them appear at the top of the list. Now, there are two general workflows you can follow:

1: Put all 'scroller compositions' into a single composition... and there you go! This might be a little hard on your computer though, so this is not the workflow I recommend unless you own a strong machine.

2: My recommended approach is to render out all of the compositions first (the ones that are neatly prefixed with an underscore) and then bringing them back into After Effects. This will significantly improve performance and reliably work even on lower end machines.

I'm no expert on codecs, but what has worked for me is rendering them using the **Animation** codec with the **Quicktime** container. This allows you to create lossless (albeit only 8-bit, but that should be enough for what we're doing) video files that are reasonably sized (~2m30s creates around 1GB of data for each MIDI) and most importantly, they **include the alpha channel**.

From here you can put everything else you want into your video and render the final video!

## Future Versions
I currently call this version 0.8 because I have two updates planned.
Version 0.9 will have improvements in the UI, especially in the settings window. This sets up version 1.0, which will include the following additions:
- **Piano key visuals:** You will have the option to generate a composition (or png file, if that's possible) with a visual representation of all the piano keys (think of a literal piano but vertically).
- **Bar lines:** A visual representation of the beats and steps of the song.
- **Single MIDI file instrument seperation:** Currently, you don't have the option to seperate different channels (or tracks/instruments), meaning you have to export your MIDI files per instrument.

These changes require better UI to allow for customization.

Version 1.0 is what I would call "finished", as in, I don't need it to do more than that for my personal use-case. But you can always [contact me](#contact-me) and ask for new features!

## Settings File
This script will work with an XML settings file called `pq_midi_settings.xml` that is expected to be in the same location as the script. The contents of the file are loaded when the script starts up. You can save the current settings from the settings window as defaults.
For this, the script requires write access. You can enable it under `Edit -> Preferences -> Scripting & Expressions -> Allow Scripts to Write Files and Access Network`. If you don't want to enable this option, you can still manually edit the XML. You can also completely get rid of any read and write operations by opening the script and changing the first line into `var USE_MIDI_SETTINGS_FILE = true;`.

## Contact Me
If you have any problems, questions or want to request new features, here is where you can contact me:

`E-Mail: peaqew@gmail.com`

`Discord: PeaQ#9827`

`Reddit: u/PeaQew`
