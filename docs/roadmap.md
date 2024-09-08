---
sidebar_position: 99
slug: /roadmap
---

# Roadmap
This page contains a rough set of ideas we want to add to the modern map making/modding pipeline in the future. Progress on all of these is made at different times, so these aren't in any specific order of importance/priority/arrival time.

## LoD (Level of Detail) support (Terrain)
Legion added level-of-detail ADTs to the game that allow the game to render lower resolution terrain at much higher draw distances. While support for this is planned in the MapUpconverter, this is rather complex so will likely take some time. This shouldn't require any editing/user input, so will likely "just work" whenever it is added.

## Lights (Terrain)
Warlords of Draenor added lgt (light) WDTs to the game that allow you to define point lights (which became more advanced in BfA and again in SL afterwards) and spot lights with optional animations for e.g. flickering after Legion. This allows lighting up your map in far more exciting ways compared to what is possible with existing lighting methods. The current idea for this is that we'll provide an asset pack of M2s that will effectively act as placeholders for placing these lights in Noggit and are removed and replaced with these newer lights during upconversion.

## Volumetric fog (Terrain)
Battle for Azeroth added fog WDTs to the game that allows you to define volumetric fog models on any scale for your map. How this will work in terms of editing is unknown and might require defining them in a text format, but we'll figure that out as we get closer.

## High-resolution holes (Terrain)
As of Mists of Pandaria it is possible to define higher resolution terrain holes, Noggit only support low resolution holes, but might be able to support higher resolution ones when Modern Features is enabled in the future.

## WMO upconversion
Adding a tool to upconvert 3.3.5-formatted WMOs to a modern format usable by 8.2+ clients. This would allow e.g. making/modifying WMOs in WoW Blender Studio (which targets 3.3.5) and then after upconversion using them in modern clients and by extension your maps.

## M2 upconversion
Adding a tool to upconvert 3.3.5-formatted M2s to a modern format usable by 8.2+ clients. This would allow e.g. making/modifying M2s in WoW Blender Studio (which targets 3.3.5) and then after upconversion using them in modern clients and by extension your maps.