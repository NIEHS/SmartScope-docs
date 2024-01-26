# Configure a protocol

Protocols can be definited in `yaml` formats. Default protocols come with SmarScope and some of the plugins.

They can be viewed on the following github pages:
- [Main SmartScope Protocols](https://github.com/NIEHS/SmartScope/tree/latest/config/smartscope/protocols)
- [Ptolemy SmartScope Protocols](https://github.com/JoQCcoz/ptolemy-smartscope)

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

## Custom protocols

Custom can be added directly in the `shared/smartscope/protocols/` directory. It is best to start from one of the existing protocols and edit from there.

All available commands are listed [here](../protocol_commands/)

Commands can be called using the name of the function.

!!! warning "Use the following at your own risk"

    The following commands are widely untested and we don't know the limitations of customization. As we get more use cases, we'll define clearer rules about what can and can't be done with such customization. 
    
    There should be no harm to the microscope in exploring these commands. Only unforseen errors and crashes.

### Special commands

#### call command

[:material-tag-outline: Added in 0.9.2]()

One of the most flexible command is the call command, which can call a SerialEM script that is loaded from script package file (available in the script window). Internally, it uses the SerialEM `Call` command

The yaml synthax of the call command shown in the following example, where the script argument is the `MacroName` of the script:

```yaml
square:
  acquisition:
    [...]
    - call:
        script: Z_byV
    [...]
```

#### callFunction command

[:material-tag-outline: Added in 0.9.2]()

This one is simialar but will call a function within a given name and arguments can be provided. Internally, it will use the SerialEM `CallFuntion` command. 

The yaml synthax of the call command shown in the following example, where the script argument is the `MacroName` of the script:

```yaml
square:
  acquisition:
    [...]
    - callFunction:
        function: MyScript::MyFunction
        args:
            - argument1
            - 2
            - argument3
    [...]
```
