---
sidebar_position: 4
slug: /modern-lights
---

# Using modern lights
> **Note:** Adding modern lights to your map requires MapUpconverter version 0.9.0 or higher.
## Basic usage
- Download the MPQ patch with some basic lights from the `#guide-resources` channel in the Discord and add it to the Data folder in your WotLK client (you can rename the patch to a different letter if it is already taken).
- Start Noggit, load up your map and open up the asset browser.
- You should now have various lights inside of the "noggit" folder (search for `noggit` to easily find them).
- Light names with "withshadows" will cast shadows on DirectX 12 when the Raytraced Shadows setting is set to "good" or higher.
- Place lights down like any other M2 object. The scale of the object will decide the intensity/radius of the light.
- When placing the objects on the ground, make sure to move them up a bit so the light appears above ground and not under it.
- Make sure "Convert WDT" is checked in the upconverter GUI when adding a light for the first time.
- When the map is converted by the MapUpconverter, it will replace the lights with actual modern lights.
- If this is the first time adding a light, a client restart might be required to pick up on the new WDT file that contains the lights.
> **Note:** Lights do not refresh yet when using "client refresh", you will have to port away/back or relog to reload the map and its lights. This is because the lights are not stored in ADTs but in a WDT.

## Advanced: Adding lights with your own colors/animations
Light colors and animations are based on their model names and the `LightInfo.json` file in the MapUpconverter `meta` directory. 
- Open `LightInfo.json` from the MapUpconverter's `meta` directory in a text editor, preferably one that validates JSON structures and/or highlights formatting mistakes. When in doubt, use Visual Studio Code.  

### Adding a color
- To add a new color, add a new block to the JSON ColorMap block like this for e.g. adding the color "white" (must be lowercase):
```JSON
"white": {
    "R": 255,
    "G": 255,
    "B": 255,
    "A": 0
},
```
- The RGBA values correspond to Red/Green/Blue/Alpha ranging from 0 to 255. The alpha value appears to be unused. You can use many different sites/tools to get RGBA values for colors such as [this site](https://www.flatuicolorpicker.com/).
- Save the JSON and restart the MapUpconverter if it is already running.

### Adding an animation
- To add a new animation, add a new block to the JSON LightAnims block like this for e.g. the animation "flickerharsh":
```JSON
"flickerharsh": {
    "FlickerIntensity": 25,
    "FlickerSpeed": 15,
    "FlickerMode": 3
}
```
- All animation names are required to start with the word `flicker` and must be lowercase.
- The intensity of the flicker is controlled by the `FlickerIntensity` value.
- The speed of the flicker is controlled by the `FlickerSpeed` value.
- There are 4 possible flicker modes for different flicker curves:  
0 = off/no anim  
1 = sine curve (smooth)  
2 = noise curve (noisy/semi-random)  
3 = noise step curve (harsh)  
- Save the JSON and restart the MapUpconverter if it is already running.

### Adding a model using your color/animation
Remember that the only differences between all the light M2s in the patch MPQ are their colors in Noggit.  
**Only the M2 names matter for the actual modern lights. Their contents do not.**

- Extract one of the M2/skin files from the above patch that you want to base your light on or base it from literally any other M2.
- The light model names have to follow this pattern: `noggit_light_<color>(_withshadows)(_flickermode)`.
- `<color>` should be replaced with the color you want from the JSON's `colormap`.  
For example, a model with the example color from the above color paragraph it would start with `noggit_light_white_`.
- `(_withshadows)` is optional. If a model name contains `withshadows` it will have RTX shadows enabled.
- `(_flickermode)` is also optional. If a model name has a part that starts with `flicker` the upconverter will attempt to look up that animation in the `LightAnims` block of the JSON.
- For example, a light that uses all of the newly added above examples (white, harsh flicker) AND casts RTX shadows should be named `noggit_white_withshadows_flickerharsh.m2` one that wouldn't cast shadows would be called `noggit_white_flickerharsh.m2`.
- Add the newly named model to the MPQ patch using MPQ editor (be sure to rename and include the .skin as well). 
- If the MPQ is 'full', extract the current patch to disk in its entirety and make a new MPQ patch based on it + your new light's M2/skin.
- Replace the current light patch MPQ in your WotLK client's Data folder with your newly written MPQ and restart Noggit. Your new light should now be in the asset browser, the rest is the same as described in the "Basic Usage" tutorial above.