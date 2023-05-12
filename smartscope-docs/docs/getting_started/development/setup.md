This section aims at describing the setup of a development environment for SmartScope.

1. First, install SmartScope using [Docker or Podman](/getting_started/installation/docker/docker/)

2. (Optional) Then, we suggest to make a fork of the repository.

3. Clone the dev branch from your fork or the main repository. `git clone git@github.com:NIEHS/SmartScope.git SmartScope-dev -b dev`

4. Mount the source code as a volume to the smartscope container. 

    !!! note

        This is the way to make modification possible and any change persistent.

    !!! warning

        The example below assumes that the source code was cloned in the installation directory

    ```yaml
    version: "3"
    services:
    smartscope:
        image: ghcr.io/niehs/smartscope:0.9.1-rc.1  #Change version here
        user: 0:0 #This corresponds to the user running the smarscope.sh script
        volumes:
        ######## ADD YOUR MAIN DATA LOCATION ##########
        - ./SmrtScope-dev/:/opt/smartscope/
        # Example:
        # - /nfs/data/:/mnt/data/
        ######## ADD YOUR MICROSCOPES #########
        # The synthax from the microscope volumes is as follows:
        # - /path/to/where/serialem/will/write/files/:/mnt/your_scope_name_here/
        # Example:
        # - /mnt/gatan_Raid_X/smartscope/:/mnt/arctica/
    ```

5. (Optional) Set up fake scope mode as detailed [here](../fake_scope)
