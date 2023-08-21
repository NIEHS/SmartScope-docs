Fake scope mode is a good way to test SmartScope without a miscope. It will pull random images from the different magnifications out of an image bank.

## Setting up the image bank
=== "Version >=0.9.2"

    ```
    smarscope.sh run download_testfiles
    ```

=== "Version <=0.9.1"

    1. Download the bank

        ```shell-session
        wget docs.smartscope.org/downloads/smartscope_testfiles.tar.gz
        tar -xvf smartscope_testfiles.tar
        ```

    2. Add an extra volume in `smartscope.yml` to add the archive to the smartscope container.

        In the container, it is mounted to `/mnt/testfiles`
        ```yaml
        version: "3"
        services:
        smartscope:
            ...
            volumes: 
                ...
                - /path/to/smartscope_testfiles/:/mnt/testfiles/
        ```

    3. Restart smartscope

        ```shell-session
        ./smartscope.sh stop
        ./smartscope.sh
        ```

