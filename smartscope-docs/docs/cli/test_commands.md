## Test SerialEM connection

This command is used to quickly test the IP and port combination to connect to the SerialEM python interface. 
It is recommended to use this command during the installation before adding the microscopes in the database.

If the command is successful, a `Hello from SmartScope` should be printed to the SerialEM log window. Otherwise, the command may hang or timeout.

Synthax: `./smartscope.sh run test_serialem_connection IP PORT`

Where:

- IP: IP address to test in the `xxx.xxx.xxx.xxx` format
- PORT: Port number to try. Most likely `48888` which is the default for SerialEM.

## Is GPU enabled

Check whether SmartScope has any GPU available to run the machine learning algorithm. Will return True or False.

!!! note GPU support

    SmartScope does not require GPU to run and the performance is satisfactory over CPU only. 
    Currently, support is limited to older hardware and we are working on updating the dependencies to support the newer GPUs.

Synthax: `./smartscope.sh run is_gpu_enabled`

## List Plugins

Prints all the available plugins that can be used when making a protocol.

Synthax: `./smartscope.sh list_plugins`

## List Protocols

Prints all the available protocols available for use.

Synthax: `./smartscope.sh list_protocols`

