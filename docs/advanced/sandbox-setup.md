---
sidebar_position: 2
slug: /sandbox-setup
---

# Sandbox modding setup
This guide assumes you've already read, understood and did the relevant parts of the basic guide. If not, start [here](/) and circle back at the end of "Getting your map in-game".

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

## (Optional) Enabling hot-reloading
You can optionally install the hot-reloading extension to almost immediately see any changes you make in-game, check out [this](/hot-reloading) on how to set that up.
