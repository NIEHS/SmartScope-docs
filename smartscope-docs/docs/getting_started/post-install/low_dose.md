# Low-dose Presets

The idea is to generate a settings file with low-dose mode presets that will work well with the current version of SmartScope.

The following table provides guidelines on how to set up the low-dose mode settings for different microscopes:

{{ read_csv('./low_dose.csv') }}

## Search

The search mag is set in LM mode to allow the capture of an entire square in a single acquisition.
On a K2 detector, we suggest using linear mode for search to maximize contrasts.

##View

The view mag is using a low SA or M mode magnification to view a few holes. It is currently only used to re-center on a hole.

## Preview

Currently, Preview is used to acquire the main high-magnification acquisition because of initial limitations with SerialEM.
Ensure that dose-fraciionation and exposure times are set for that purpose.

## Record

Currenly used to acquire the atlas. Atlas is acquired outside of low-dose mode and current scripting commands for acquiring montage will use Record by default.

!!! note
    
    We're currently testing how to reliably use the mont-map preset for the atlas acquisition, which will allow us to use Record instead of Preview for the acquisition.

## Focus/Trial


Used for autofocus and drift correction. For autofocus, the specified image-shift position that is set will be used for each sample. We suggest changing it when doing data collection to ensure that the focus area illuminates between holes.

!!! note

    This will also be changed in the near future. We plan on including automatic focus positioning relative to the mesh spacing and orientation.

## Non Low-dose Presets
    
The easiest way to set up for the atlas is to create an imaging state for mont-mapping. This way, when acquiring the atlas, it will use the mont-map setting instead of Record.