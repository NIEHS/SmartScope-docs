# Docker Installation


## Regular installation

!!! note
    
    To avoid file permission issues, you should perform these steps as the user that will run the smartscope software.

### 1. Download the minimal configuration files.

```shell-session
wget docs.smartscope.org/downloads/SmartScopeInstallation.tar.gz --no-check-certificate
tar -xvf SmartScopeInstallation.tar.gz 
cd SmartScope
```


The directory contains 5 files that can be divided in 3 categories:

- Docker files:

    - `docker-compose.yml`: Main file for the docker environment. Should not need to be changed.
    - `smartscope.yml`: Simpler version of the docker-compose.yml to add additional settings. This one needs to be changed.

- Configuration:

    - `database.conf`: Contains the configuration for the database connections to share between smartscope and the database.
    - `smartscope.conf`: Contains the configuration that is unique to smartscope.

- Script:

    - `smartscope.sh`: Used to start and stop the smartsocpe software.

### 2. Create a directory on your SerialEM computer where SmartScope will save data and a storage area for smartscope.


```shell-session
mkdir /mnt/serialemComputer/smartscope
mkdir /mnt/nas/smartscope
```


### 3. Edit the `smartscope.yml` file to add your microscope path and the paths that you just created.

```yaml
version: "3"
services:
smartscope:
  image: ghcr.io/niehs/smartscope:0.8-rc.2  
  user: ${UID}:${GID}
  volumes: 
    # - /home/ubuntu/SmartScope/:/opt/smartscope/
    ######## ADD YOUR MAIN DATA LOCATION ##########
    - /mnt/nas/smartscope/:/mnt/data/
    # Example:
    # - /nfs/data/:/mnt/data/
    ######## ADD YOUR MICROSCOPES #########
    # The synthax from the microscope volumes is as follows:
    # - /path/to/where/serialem/will/write/files/:/mnt/your_scope_name_here/
    - /mnt/serialemComputer/smartscope/:/mnt/myscope1/
    # Example:
     # - /mnt/gatan_Raid_X/smartscope/:/mnt/arctica/
```


!!! info "Multiple microscopes in a single installation"

    You can add multiple microscopes to the same SmartScope installation. Simply add an additional entry to the volumes section.

### (Optional) Edit the configuration files to your needs.

Detailed information about the configuration variables can be found [here](/getting_started/advanced_setup/environment).

### 4. Start SmartScope

The first start will download all the container images and is expected to 

```shell-session

./smartscope.sh start

#Outputs should look like this
Starting smartscope
[+] Running 5/5
⠿ Network installation_smartscopenet  Created      0.0s
⠿ Container installation-cache-1      Started      0.7s
⠿ Container smartscope-db             Started      0.6s
⠿ Container smartscope                Started      1.0s
⠿ Container installation-nginx-1      Started      1.4s
```

### 5. Log in to the web interface with the initial admin account.

You should now be able to access the smartscope interface at [http://localhost:48000/](http://localhost:48000/).

The initial account is `admin` with password `smartscope`. 

!!! note

    You may need to change the domain and port number to reflect the docker-compose file with the port specified in the nginx service and one of the domains specified in the ALLOWED_HOSTS of the smartscope service.

### 6. The installation is done!
    
There is a few more set up steps to do in SerialEM and in the web portal to get up and running. [Click here](/getting_started/post-install/external_python). for the instructions