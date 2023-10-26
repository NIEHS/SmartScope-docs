## Nvidia GPU passthrough

!!! note
    
    SmartScope runs quite fast without GPU since it uses pre-trained models for object detection.

!!! warning

    SmartScope doesn't support the most recent generation of GPU (RTX 30-series). We're working on it.


If you are planning on using GPU acceleration with SmartScope with podman, the nvidia-container-toolkit is required. The documentation on how to set it up for podman or docker can be found [here](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html#podman)