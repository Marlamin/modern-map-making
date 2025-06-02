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
- Download the required client files from [here](https://marlam.in/u/927Client.zip). Note that this client is a streaming client and it'll stream data.
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

## (Optional) Adding custom hotfixes
> **Note:** This requires sandbox version 0.2.0 or newer and a basic understanding of what DB2 controls what.  

Hotfixes placed in the sandbox's hotfixes directory will be loaded by the sandbox and sent to the game upon login or change of one of the hotfixes.

Filenames should be in `db2name.json` format e.g. `creaturedisplayinfo.json` and contain an array of row data.  
ID field in row should be called `Id`, other field names don't matter but there should be the same amount of the same types as the DB2.

> **Note:** Some DB2 structures that the sandbox uses might be outdated and cause issues with adding custom hotfixes. If you feel like you might have hit this issue with a specific DB2, please let us know in the [troubleshooting channel on the Discord](https://discord.gg/q4tRTwwDEQ).

#### Weather hotfix tutorial
As a quick tutorial we'll be adding a custom weather effect:

- Open up the text editor of your choice (e.g. Visual Studio Code).
- Open up the 9.2.7.45745 DB2 table you are making a hotfix for on [wago.tools](https://wago.tools/db2/Weather?build=9.2.7.45745&sort[ID]=desc) (in this case we want Weather.db2).
- If you want to overwrite an existing record, find the ID of it. If you want to add a new record, find an ID that isn't used (e.g. 500).
- Start writing out JSON and add the ID of your choice as the "Id" field (capitals matter!):
```json
[
    {
        "Id": 500,
    }
]  
```
- Then proceed to fill in the rest of the fields visible on wago.tools with your own values or values copied from another record.  
For example, like this:
```json
[
    {
        "Id": 500,
        "Type": 1,
        "Field_9_0_1_33978_001": 0,
        "TransitionSkyBox": 1.0,
        "AmbienceID": 8536,
        "SoundAmbienceID": 1338,
        "EffectType": 1,
        "EffectTextureFileDataID": 0,
        "WindSettingsID": 129,
        "Scale": 1.0,
        "Volatility": 2.0,
        "TwinkleIntensity": 0.0,
        "FallModifier": 1.0,
        "RotationalSpeed": 0.0,
        "ParticulateFileDataID": 0,
        "VolumeEdgeFadeStart": 0.0,
        "OverrideColor": 0,
        "OverrideColorIntensity": 0.0,
        "OverrideCount": 0.9,
        "OverrideOpacity": 1,
        "VolumeFlags": 56,
        "LightningID": 0,
        "Intensity_0": 0.80000001192,
        "Intensity_1": 0.89999997616,
        "EffectColor_0": 1.0,
        "EffectColor_1": 1.0,
        "EffectColor_2": 1.0
    }
]
```
> **Note:** The above row only has number/float fields. If there is a string field in the DB2, make sure to put the value in quotes.
- Save as `weather.json` in the hotfixes directory. (Make sure file extensions are on so you **don't** make a `weather.json.txt.`)
- Because Weather.db2 also uses [WeatherXParticulate.db2](https://wago.tools/db2/WeatherXParticulate?build=9.2.7.45745&sort[ID]=desc) to connect particle files to weather effects, we'll need to add a `weatherxparticulate.json` with 2 entries as well following the same logic as the above steps:
```json
[
    {
        "Id": 521,
        "FileDataID": 4175807,
        "ParentWeatherID": 500
    },
    {
        "Id": 522,
        "FileDataID": 4175809,
        "ParentWeatherID": 500
    }
]
```
- Save that file as `weatherxparticulate.json` in the hotfixes directory.
- Start the sandbox and client.
- Once in-game, you can use the weather command to look at your new weather effect by using the new !weather command by sending `!weather id intensity` in chat. In this case we've added our effect as ID 500, so the command is `!weather 500 1.0`. Let it snow!
- You can edit the JSON files and change around values to have them instantly be sent to the client upon saving (see below note!).

> **Note:** While some hotfix changes apply instantly, others might require you to make the game look up the record again. In this weather example, you will need to rerun the `!weather 500 1.0` command to make the game check the weather values again.
