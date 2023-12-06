# Requirements

* Thermo Fisher or JEOL microscope:

    * JEOL scopes are now supported but not widely tested.

* SerialEM >= 4.1-beta:
   
    [Click here](https://bio3d.colorado.edu/SerialEM/) for instructions about how to install and use SerialEM.


* A **linux** workstation that is on the same network as the SerialEM computer:

    * Required to connect to SerialEM via the [python module](https://bio3d.colorado.edu/SerialEM/hlp/html/about_scripts.htm).
    * Hard drive accessible by SerialEM and SmartScope in real time mounted via NFS, SMB or similar protocol.
    * 4 cpu cores (Recommended 8)
    * 24 GB RAM per microscope that will connect to the instance.

    !!! note "Windows support"

        It should be possible to run SmartScope on windows with Windows >=10 or Windows Server >= 2016 with Docker but it was not tested.

* Chrome Web or Firefox web browser

    !!! warning "Safari compatibility"
        
        Safari browser is incompatible.
    
     
## Installation options

### Docker

Docker is much easier to set up on most linux distributions and is therefore recommended. [Click here to learn how to install docker](https://docs.docker.com/engine/install/).

### Podman

!!! note
    
    The installation requires Podman version >=3.0 and podman-compose 0.1.x. If you are using podman >=3.4, you can use podman-compose from the main branch on github.

Here are the links on how to install Podman and podman-compose:

* [Podman](https://podman.io/getting-started/installation)
* [podman-compose 0.1.x](https://github.com/containers/podman-compose/tree/0.1.x). For use with podman >=3.0,<3.4
* [podman-compose stable](https://github.com/containers/podman-compose/tree/stable>). For use with podman >=3.4