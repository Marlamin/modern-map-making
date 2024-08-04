---
sidebar_position: 3
slug: /setting-up-template-map
---

# Setting up the template map
## Making the map
- Open your project in Noggit if you haven't already.
- On the bottom left click "Add New Map".
- In the map directory field enter `custommap`.
- In the map name input you can put anything you want e.g. `My New Map`.
- Hit Save.
- It will warn you about the map being empty, just hit Yes.
- Close Noggit.

## Getting the template map
- Go to the [#guide-resources](https://discord.com/channels/1264317233190928385/1268871553010106480) channel in our Discord and go to the Mega link under "Template Maps".
- Download and extract `CustomMap(335).zip` to your Noggit project folder in the subdirectory `world/maps/`. The eventual path for the various WDT/WDL/ADT files in the zip should look like this: `Noggit Project Folder/world/maps/CustomMap/custommap.wdt`.
- If you are targeting an Epsilon client, download and extract `CustomMap(Modern).zip` to the Epsilon patches directory.
- Download `custom-listfile.csv` and put it in the MapUpconverter directory in a subdirectory called `meta` (it should already exist from the last set up step).

## Setting up for conversion
- Open MapConverterGUI.exe from the MapUpconverter directory.
- After opening, on the bottom right a few files need to be downloaded. Hit the Download buttons for files that still need to be downloaded. Based on internet speed, this might take a minute (listfile is 100MB+).
- Set the input directory to your Noggit project folder.
- Set the output directory to where the converter should save converted files. When using Epsilon, this is the `Epsilon folder/_retail_/patches/CustomMap` folder.
- Set the map name to "custommap".
- If using Epsilon, set the relevant Epsilon settings as well.
- When done, hit Save Settings.