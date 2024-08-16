---
sidebar_position: 2
slug: /sandbox-setup
---

# Sandbox modding setup
## Setting up the sandbox
If you want to do client previews of your maps locally you can use the sandbox for that. Note that the sandbox/launcher used in this article is specifically made to only work with a 9.2.7.45745 client. 

- Make a folder somewhere that can host the sandbox and the client.
- Download the latest release of the [Sandbox](https://github.com/ModernWoWTools/Sandbox/releases) and extract it to a subfolder called Sandbox.

## (Option 1) Setting up a new client
- Download the required client files from [here](https://wow.tools/pub/927Client.zip). Note that this client is a streaming client and it'll stream data.
- Extract it to a subfolder called Client.

## (Option 2) Setting up an existing client
If you have an existing **_unmodified_** 9.2.7.45745 client you can also use that with some modifications.

> **Note:** Unmodified means unmodified, so **do not** try this with e.g. an Epsilon client.

- In `WTF/Config.wtf` change the `SET portal` line to `SET portal "127.0.0.1:8000"`.
- In `WTF/Config.wtf` change the `SET synchronizeSettings "0"` line to `SET synchronizeSettings "0"`.  
Add it if it does not exist.
- Optionally, create a new file called `login.txt` next to WoW.exe that has the following contents so it logs you in automatically:
```
arctium@arctium
arctium
```
## Setting up the launcher
> **Note:** Windows Defender might flag the download as a virus, this is a false positive and an exception might need to be added before redownloading.   
- Download the latest release of the [Launcher](https://github.com/ModernWoWTools/Launcher/releases) and extract it next to WoW.exe (should be in `Client/_retail_`).

## Configuring the upconverter
- In the MapUpconverter set the export target to "Arctium" and set the folder to the folder "Arctium WoW Launcher.exe" is in (again, should be `Client/_retail_`).
- If this is the first time converting the map, make sure Convert-on-save is disabled.

## Running the sandbox
- Double click "Arctium WoW Sandbox.exe".
- If prompted for a firewall exception (first time only) allow it. This sandbox does not connect to the internet but still has to bind itself on local ports. 
- Let it start.

## Running the client
- Double click "Arctium WoW Launcher.exe" (not Wow.exe!). For the first launch it might take a minute to show anything as it is downloading required files.
- If it doesn't automatically log you in with the included `login.txt`, you can login manually with the account `arctium@arctium` and password `arctium`.
- Select the realm, create a character and log into the world as usual.

## (Optional) Installing the hot-reload extension
The hot-reloading extension DLL allows you to hot-reload changes between Noggit, the MapUpconverter and the 9.2.7 client within a second after saving in Noggit ([example](https://marlam.in/u/Wow_YbGssG0xpd.mp4)). If you think this is useful for you, this might be something you want.

> **Note:** This requires MapUpconverter 0.8.2 or newer. 
 
> **Note:** For Epsilon users, hot reloading is coming with the Shadowlands release. Do not attempt to use this with Epsilon. 

- Download the Arbiter DLL from [here](https://marlam.in/u/arbiterdll.dll) (GitHub releases coming soon™) and place it next to WoW.exe.
- As Arbiter also adds Epsilon's patch tech, we have to use "Epsilon" as export target in MapUpconverter. Outside of having to enable patches (all patches in the Patches directory are always on), the rest is the same as Epsilon's patch behavior.
- In the Epsilon Settings tab in MapUpconverter, set the directory to the directory containing `_retail_`. e.g. if your Wow.exe is in `F:/Client/_retail_/Wow.exe` then set this to `F:/Client`.
- In the Advanced Settings tab in MapUpconverter, turn on "Enable Client Refreshing" and if you know it enter the MapID of your map (the ID you use in teleport commands, this makes reloads faster).
- Make sure you convert your map without Convert-on-save mode on once to make sure all files are present in the new patch.
- Launch the client with "Arctium WoW Launcher.exe" as normal, it will do the same as it usually does but it will skip Arctium's file patching in favor of Arbiters Epsilon-like patching.
- Once in world, enable Convert-on-save mode in the MapUpconverter and start it. It will wait for changes to files in the input directory (Noggit project).
- Change something in Noggit and save (Ctrl-S), when a change is detected MapUpconverter converts the changed files and if needed updates the patch manifest and tells the client to refresh.
- Your change should show up in-game shortly after saving. If not, check the MapUpconverter console for any possible issues and report them on the Discord.

> **Tip:** If you have 2 monitors, move Noggit (or WoW) to your secondary monitor so you can preview changes without alt-tabbing. If you have 1 monitor, you can also use PowerToys [Always On Top](https://learn.microsoft.com/en-us/windows/powertoys/always-on-top#install-powertoys) to stick Noggit on top of WoW while editing (as shown in the [example](https://marlam.in/u/Wow_YbGssG0xpd.mp4) video).