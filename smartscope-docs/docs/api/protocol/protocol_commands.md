# Protocol Commands


Protocol commands are used in the `protocol.yaml` files as building block for the `acquisition` blocks. Different protocols can be built with different combinations of commands.

All protocol commands have the same input arguments:

- scope: The microscope interface instance
- params: The data collection parameters specified during session setup.
- instance: The instance of the database object that is being worked on. Atlas, Square, Hole, Highmag object


## Available commands

### SmartScope core commands

::: core.protocol_commands
    options:
        show_root_heading: True
        show_source: false

### Commands specific to plugins

#### Ptolemy

::: ptolemy-smartscope.smartscope_plugin.protocol_commands
    options:
        show_root_heading: True
        show_source: false