---
sidebar_position: 3
slug: /hot-reloading
---

# Hot reloading
Hot reloading allows you to hot-reload changes between Noggit, the MapUpconverter and a 9.2.7 client within a second after saving in Noggit ([example](https://marlam.in/u/Wow_YbGssG0xpd.mp4)). If you think this is useful for you, this might be something you want.

> **Note:** This requires MapUpconverter 0.8.2 (or newer) and 0.1.1 of the Launcher (or newer). 
 
> **Note:** For Epsilon users, as Epsilon already supports client refreshing out of the box, you need to skip the first 4 steps (not doing so will break your client).

- Download the Arbiter DLL from [here](https://marlam.in/u/arbiterdll.dll) (GitHub releases coming soon™) and place it next to WoW.exe.
- Create an empty "Patches" directory next to WoW.exe.
- As Arbiter also adds Epsilon's patch tech, we have to use "Epsilon" as export target in MapUpconverter. Outside of having to enable patches (all patches in the Patches directory are always on), the rest is the same as Epsilon's patch behavior.
- In the Epsilon Settings tab in MapUpconverter, set the directory to the directory containing `_retail_`. e.g. if your Wow.exe is in `F:/Client/_retail_/Wow.exe` then set this to `F:/Client`.
- In the Advanced Settings tab in MapUpconverter, turn on "Enable Client Refreshing" and if you know it enter the MapID of your map (the ID you use in teleport commands, this makes reloads faster).
- Make sure you convert your map without Convert-on-save mode on once to make sure all files are present in the new patch.
- (Epsilon users only) Enable the patch in the Epsilon Launcher and start the game as normal.
- (Arctium users only) Launch the client with "Arctium WoW Launcher.exe" as normal, it will do the same as it usually does but it will skip Arctium's file patching in favor of Arbiters Epsilon-like patching.
- Once in world, enable Convert-on-save mode in the MapUpconverter and start it. It will wait for changes to files in the input directory (Noggit project).
- Change something in Noggit and save (Ctrl-S), when a change is detected MapUpconverter converts the changed files and if needed updates the patch manifest and tells the client to refresh.
- Your change should show up in-game shortly after saving. If not, check the MapUpconverter console for any possible issues and report them on the Discord.

> **Tip:** If you have 2 monitors, move Noggit (or WoW) to your secondary monitor so you can preview changes without alt-tabbing. If you have 1 monitor, you can also use PowerToys [Always On Top](https://learn.microsoft.com/en-us/windows/powertoys/always-on-top#install-powertoys) to stick Noggit on top of WoW while editing (as shown in the [example](https://marlam.in/u/Wow_YbGssG0xpd.mp4) video).
