# Configure a protocol

Protocols can be definited in `yaml` formats. They can be added directly in the `config/smartscope/protocols/` directory.

At it's base level. A protocols contains 6 sections:

## General

- **name:** just a string containing a name for the procotol. Needs to be unique.
- **description:** optinal protocol description to show in the webpage. Coming soon.

## Magnification levels:

- atlas
- square
- mediumMag
- highMag

Each magnification levels contains these subsections:

- **acquisition:** filled with a list of commands from the protocol_commands
- **targets:** filled with lists of algorithms from the plugins section.

!!! example

    ```yaml
    name: SPA
    atlas:
    acquisition:
        - setAtlasOptics 
        - atlas
    targets:
        finders:
        - AI square finder
        selectors:
        - Size selector
    square:
    acquisition:
        - moveStage
        - realignToSquare
        - eucentricSearch
        - square
    targets:
        finders:
        - AI hole finder
        - Regular pattern
        selectors:
        - Graylevel selector
    mediumMag:
    acquisition:
        - setFocusPosition
        - tiltToAngle
        - moveStage
        - loadHoleRef
        - alignToHoleRef
        - mediumMagHole
    highMag:
    acquisition:
        - highMag
    ```

