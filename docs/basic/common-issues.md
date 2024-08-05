---
sidebar_position: 10
slug: /common-issues
---

# Common Issues
- When editing existing continents you might encounter terrain un-loading after making sizable height changes, to mitigate that add [this occluder file](pathname:///resources/yourmapname_occ.wdt) to the patch. If you are editing existing maps like Eastern Kingdoms rename and place it in `world/maps/azeroth/azeroth_occ.wdt` where Azeroth is the directory/internal name of your map.
- When you have custom M2s or WMOs in your map they might disappear or not appear at all. You will need to set a bounding box for these FileDataIDs in the MapUpconverter's `meta/blob.json` file and then reconvert to fix this.