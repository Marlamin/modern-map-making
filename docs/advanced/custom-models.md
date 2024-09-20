---
sidebar_position: 5
slug: /custom-models
---

# Working with custom models
When using the MapUpconverter with custom models (M2 or WMO), some additional steps are needed to prevent missing bounding box errors/failed model mappings.
- Add all custom files for the model to `meta/custom-listfile.csv` in the `fdid;path` format (e.g. `92720000;custom/mymodel.m2`).  
**Note:** Make sure all the model paths match the ones you're using in Noggit exactly, otherwise upconversion will fail for these.
- Add bounding boxes for your model to `meta/custom-blob.json` in the same format as `meta/blob.json`.  
You can generate a bounding box for a model by dropping either an M2 or WMO file on top of MetaGen.exe, included with the MapUpconverter. The output will look something along the lines of this: 
```json
{
  "BottomCorner": {
    "X": -7.7407446,
    "Y": -2.777778,
    "Z": -1.389679
  },
  "TopCorner": {
    "X": 2.7595077,
    "Y": 2.777778,
    "Z": 51.003826
  }
}
```
Then merge that into `meta/custom-blob.json` with as key the FileDataID of the model you assigned in the first step. After merging, it should look something along the lines of this (with your own FileDataID/bounding box obviously):
```
{
  "92720000": {
    "BottomCorner": {
        "X": -7.7407446,
        "Y": -2.777778,
        "Z": -1.389679
    },
    "TopCorner": {
        "X": 2.7595077,
        "Y": 2.777778,
        "Z": 51.003826
    }
  },
  ...more entries here if present...
}
```
- The MapUpconverter should now be able to map your custom models to their proper IDs and bounding boxes.
- Obviously, also make sure that your custom models are available to whatever client you're loading them in under the IDs you assigned in the earlier steps.