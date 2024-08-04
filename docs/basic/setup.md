---
sidebar_position: 1
slug: /
---

# Set up
You will need various things to get started with WoW modding, but don't worry, we'll walk you through it below.

## What you'll need
### WoW client
Right now the tools all work with 3.3.5 assets only, so you'll need a 3.3.5a.12340 enUS client. We can't host one for obvious reasons but it should be relatively easy to find through sites like wowdl.net.  
**Note:** Make sure to put it somewhere where you have enough space for the client (~20GB) and the downconverted assets (~15GB).

### Downported assets
To use modern assets in Noggit, you'll need to download ~15GB of downconverted modern assets from [here](https://drive.google.com/file/d/1B3kS9KB1ZBOsI6EJWt0TT5LQl1oPmDsE/view) and put the MPQ in your client's Data directory.

### Noggit 
Download the latest Noggit release with modern features from the [#releases](https://discord.com/channels/1264317233190928385/1264319052583801059) channel in the Discord and extract it somewhere.

### MapUpconverter
Download the latest `MapUpconverter` from the [#releases](https://discord.com/channels/1264317233190928385/1264319052583801059) channel in the Discord and extract it somewhere.

### Terrain height texture config
The latest `global.cfg` with terrain height texture values from the [#releases](https://discord.com/channels/1264317233190928385/1264319052583801059) channel in the Discord. After making your first Noggit project (see next tutorial) make a folder called `extraData` in your Noggit project folder and put the `global.cfg` in there.  
Then, in the MapUpconverter directory, make a `meta` folder, copy `global.cfg` into it and rename it to `TextureInfoByFilePath.json`.