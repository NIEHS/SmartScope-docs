## Setting up external python for SerialEM

Documentation on how to set up can be found on the [SerialEM website](https://bio3d.colorado.edu/SerialEM/hlp/html/about_scripts.htm#Python). We have now installed on a few systems and here are some examples for setting up the `SerialEMproperties.txt`.

`SocketServerIP 1 xxx.xxx.xxx.xxx`, is the IP where the `FEI-SEM-server.exe` is running

Otherwise, `SockerServerIP 7` should be the IP of the SerialEM PC.

**Example: Talos Arctica with K2 or K3**

* Microscope PC IP: 192.168.0.3
* Gatan PC IP: 192.168.0.32
* SerialEM is installed on the Gatan PC

The following lines should be added to `SerialEMproperties.txt`.

```text
SocketServerIP                  1 192.168.0.3
SocketServerPort                1 48892
SocketServerIP                  7 192.168.0.3
SocketServerPort                7 48888
EnableExternalPython            1
```

!!! tip
    
    SerialEM needs to be restarted after changing properties.

## Testing serialEM connection from SmartScope

To quickly test if your settings are good for the python connection to SerialEM, you can use the following commands and replace IP by the gatan PC address and port by 48888.

From our examples above, the Talos Arctica IP K2 PC is 192.168.0.32 and port would be 48888.

=== "Version >= 0.8"

    ```shell-session
    ./smartscope.sh run test_serialem_connection IP port
    ```

    !!! example

        ```
        ./smartscope.sh run test_serialem_connection 192.138.0.32 48888
        ```
    

=== "Version < 0.8"

    ```shell-session
    docker exec smartscope smartscope.py test_serialem_connection IP port
    ```

    !!! example

        ```
        docker exec smartscope smartscope.py test_serialem_connection 192.138.0.32 48888
        ```

If the connection is successful, a `Hello from smartscope` message should appear in the SerialEM log window. Now, you can proceed to adding a microscope.