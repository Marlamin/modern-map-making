---
sidebar_position: 3
slug: /setting-up-template-map
---

# Setting up the template map
This step uses the template map but will still be useful if you're working with your own map, although some parts might not apply.

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
- If you are targeting Epsilon or Arctium, download and extract `CustomMap(Modern).zip` to the `Epsilon folder/_retail_/patches` or `Arctium folder/files` directory.
- Download `custom-listfile.csv` and put it in the MapUpconverter directory in a subdirectory called `meta` (it should already exist from the last set up step).

## Setting up for conversion
- Open MapUpconverterGUI.exe from the MapUpconverter directory.
- After opening, on the bottom right a few files need to be downloaded. Hit the Download buttons for files that still need to be downloaded. Based on internet speed, this might take a minute (listfile is 100MB+).
- Set the input directory to your Noggit project folder.
- Set the output directory to where the converter should save converted files.  
- Set the map name to "custommap".
- Set the export target, when targeting Epsilon/Arctium select one of those, if you just want it output to a folder select "Generic".
> **Note**: When using Epsilon/Arctium export targets, the output folder setting is ignored and the converter instead outputs files to `Epsilon folder/_retail_/patches/EpsilonPatchName` or `Arctium folder/files/ArctiumPatchName` depending on what you set in the Epsilon/Arctium-specific settings tab.
- When done, hit Save Settings.

### Arctium/Epsilon-specific settings
When using Arctium/Epsilon integration you will need to set up some other things as well.

- In the Epsilon/Arctium directory enter the folder that `Epsilon.exe` or `Arctium WoW Launcher.exe` are in. 
- In the patch name enter `CustomMap`, this should match the name of the extracted folder from `CustomMap(Modern).zip`.
- For WDT FileDataID you need to set an ID of a WDT that is referenced by Map.db2 in your version.  
For 8.x-9.x you can use FileDataID `1949764` (Map.db2 ID 1925). If you are on another version, you can use [wago.tools](https://wago.tools/db2/Map?build=11.0.2.55959) to find a different ID of a map present in that version. WDT FileDataIDs are listed in the `WdtFileDataID` column.
> **Note**: Maps can have different flags set in Map.db2, some flags can affect rendering.

> **Advanced**: If you can add hotfixes (e.g. on the Arctium sandbox) you can create your own map and assign a custom FileDataID.  
