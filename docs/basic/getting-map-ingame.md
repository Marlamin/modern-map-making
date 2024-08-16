---
sidebar_position: 5
slug: /getting-map-ingame
---

# Getting your map in-game
Depending on what kind of modern client you are using, this part of the tutorial might differ.

## Initial conversion
You should already have set up the MapUpconverter earlier in the tutorial ([Setting up for conversion](/setting-up-template-map#setting-up-for-conversion)), if not go back and do that now.

After setting it up, you will need to do a full map conversion for the first time.  

Open MapUpconverterGUI.exe, make sure `Convert on Save?` is unchecked, do a last check to see if the settings look okay and hit the `Save & Start converter` button. A console window will now open and the converter will do its thing, if there's no errors/warnings and conversion is a success, press enter to exit the console window. 

> If there are warnings or errors, please let us know in the [troubleshooting channel on the Discord](https://discord.gg/q4tRTwwDEQ).

After the initial conversion your map should now be available in the intended output directory depending on your export target:
- For Generic, this is whatever folder you set as output folder. 
- For Epsilon, this is `Epsilon folder/_retail_/patches/EpsilonPatchName`.
- For Arctium, this is `Arctium folder/files/ArctiumPatchName`.

If you selected "Generic" as export target, you will have to get your map into the modern client through your own methods. 

## (Epsilon only) Enabling the patch
If you selected Epsilon as export target, the MapUpconverter will have automatically generated a `patch.json` for the Epsilon launcher to use, but you will still have to enable it manually. Open the Epsilon launcher, go to Patches and make sure the patch is enabled. 

> If the patch is greyed out and cannot be enabled, please let us know the error that it shows when enabling it in the [troubleshooting channel on the Discord](https://discord.gg/q4tRTwwDEQ).

## Teleporting to your map
Once in-game, you can teleport to your with the relevant teleport command (`.worldport` on Epsilon, `!tele` on the Arctium Sandbox). 
To know which coordinates to teleport to, you can use the "server coordinates" that Noggit shows on the bottom left, e.g. if Noggit lists `server: (1961.23, -2162.17, 41.1425)` and you are on the example template map (Map ID 1925) your teleport command on Epsilon will be `.worldport 1961.23 -2162.17 41.1425 1925` or `!tele 1961.23 -2162.17 41.1425 0 1925` on Arctium.

## Previewing updates in-game
When running the MapUpconverter with convert-on-save mode enabled, it will save ADTs to the target output folder every time they change on disk (e.g. when you press Ctrl-S in Noggit). These changes are viewable in-game almost immediately, but will require a map reload.  

> **Note**: If you follow our [sandbox setup guide](/sandbox-setup) you can get it set up to almost instantly view any changes in-game instead of e.g. having to teleport back and forth. [(Example)](https://marlam.in/u/Wow_YbGssG0xpd.mp4)

### (Epsilon only) Quick reload method
On Epsilon, you can do this in a quick manner by teleporting back and forth between GM Island your map by making this macro:
```
.tele gmisland  
.worldport YourCoordinatesAndMapIDGoHere
```
Simply put this macro in your action bar and hit it to teleport to GM Island and hit it again to go back to the set coordinate in the worldport command to reload your map.

> **Note**: In the upcoming Shadowlands release of Epsilon you will be able to instantly view changes without teleporting. [(Example)](https://marlam.in/u/Wow_YbGssG0xpd.mp4)
