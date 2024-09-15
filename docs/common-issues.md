---
sidebar_position: 10
slug: /common-issues
---

# FAQ & common issues
First off, make sure you've followed all steps of the tutorial correctly. Most of the issues people bring up in the Discord can be fixed by following the tutorial steps properly. If you still have an issue that is not listed below, feel free to post in the #troubleshooting channel of our Discord (invite link in menu).

## Tools
### I want to convert a different map that isn't called CustomMap.
You'll have to make sure that the map name is correct everywhere, including Map.dbc, the Noggit input folder structure, the custom listfile and in the converter settings. We'll have a tutorial on this at some point in the future that goes into more detail.

### My map doesn't convert and I am getting "access to x is denied" errors in console.
Make sure the MapUpconverter has read/write access to the target directory, if your target folder is in e.g. Program Files folder you'll have to run the MapUpconverter as administrator (or fix the folder rights to give it access). 

## Terrain
### My terrain is flickering in/out of existence!
When editing existing continents you might encounter terrain un-loading after making sizable height changes, to mitigate that add [this occluder file](pathname:///resources/yourmapname_occ.wdt) to the patch. If you are editing existing maps like Eastern Kingdoms rename and place it in `world/maps/azeroth/azeroth_occ.wdt` where Azeroth is the directory/internal name of your map.

## Models
### My custom M2/WMO is not appearing ingame or appearing/disappearing.
When you have custom M2s or WMOs in your map they might disappear or not appear at all. You will need to set a bounding box for these FileDataIDs in the MapUpconverter's `meta/blob.json` file and then reconvert to fix this. You can view the a bounding box for your custom M2/WMO by dropping it on top of the MetaGen tool that is included with MapUpconverter 0.9+.

## Ground effects
### Ground effects are showing up where I don't want them (e.g. roads).
In Noggit while in the texturing tool, click the "In Development" button on the bottom right. In the "Ground Effects Tool" window that opens up, check Brush Mode on the bottom left and then click Paint Exclusion. You can now ctrl-click on the terrain to paint exclusion zones where ground effects should not show up. 
> **Note:** At time of writing, the rest of the ground effects tool UI is not finished and should not be used yet.

### No ground effects are appearing in-game for certain textures.
We use Blizzard's ground effect mappings by default. If you are for example using a texture newer than is available in your client version by default (e.g. a Dragonflight texture while on a Shadowlands client), you won't have any ground effects there.  
Some other textures might simply not have ground effects assigned by Blizzard either. Try a different but similar texture that might have effects attached to them. 
> **Advanced users:** If you know what you are doing, you can edit the `meta/GroundEffectIDsByTextureFileID.json` file to attach [GroundEffectTexture](https://wago.tools/db2/GroundEffectTexture?build=9.2.7.45745) IDs to texture FileDataIDs.