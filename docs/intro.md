---
sidebar_position: 1
slug: /
---

# Basic Tutorial

What follows is a basic tutorial for people who are new to WoW modding. If you are familiar with WoW modding already, you can skip ahead to the relevant sections in the sidebar on the left.

## Setting up

You will need various things to get started with WoW modding, but don't worry, we'll walk you through it below.

### What you'll need

- A 3.3.5a.12340 enUS World of Warcraft client. We can't host it but it should be relatively easy to find through sites like wowdl.net.
- Downported assets from [here](https://drive.google.com/file/d/1B3kS9KB1ZBOsI6EJWt0TT5LQl1oPmDsE/view).
- The latest `Noggit` and `MapUpConverter` from the [#releases](https://discord.com/channels/1264317233190928385/1264319052583801059) channel in the Discord.
- The latest `global.cfg` from the [#releases](https://discord.com/channels/1264317233190928385/1264319052583801059) channel in the Discord.

### Creating a project in Noggit
Open Noggit, etc etc.

### Your first edits on the template map
Bla

## Issues
- When editing continents you might encounter terrain un-loading after making sizable height changes, to mitigate that add [this occluder file](pathname:///resources/yourmapname_occ.wdt) to the patch. If you are editing existing maps like Eastern Kingdoms rename and place it in `world/maps/azeroth/azeroth_occ.wdt` where Azeroth is the directory/internal name of your map.