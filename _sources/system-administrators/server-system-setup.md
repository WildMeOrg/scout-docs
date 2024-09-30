# Server System Setup

Scout can be configured a number of ways, some of which require additional system setup.

## Operating System
The Wild Me team develops and tests on Linux Ubuntu. We have external verification that Scout runs on macs, but it may be necessary to test locally before updating your production system. Instructions below assume Ubuntu for commands.

## Storage

```{warning}
Ensure the user account has write permissions for all folders and is the same account used to start the Scout container.
```

Scout is designed to process large volumes of aerial survey imagery, which may come in terabytes. Ensure you have adequate image storage available.

1. Create a directory for image storage, such as `/data/scout`
    * Subsequent instructions in this documentation refers to the path as `/data/scout` for all file creation.
2. Create a subfolder in the directory such as `/data/scout/images` which will store images that will be added to Scout.
    * As soon as this subfolder is created, you can begin copying your images into it.
3. The first should be for data storage. We recommend `/data/scout/db`
4. The second is for temporary use during processing. We recommend `/data/scout/tmp`

### CUDA toolkit

To update your system’s CUDA Toolkit:

1. Visit [CUDA Toolkit resources](https://developer.nvidia.com/cuda-downloads?target_os=Linux&amp;amp;target_arch=x86_64&amp;amp;Distribution=Ubuntu)
2. Select the version of Ubuntu you are using.
3. Select **deb(local)** for your installer type.
4. Follow the download instructions for the toolkit installation.
5. Follow the download instructions for the driver installation.
6. Once installed, you will need to reboot the server to ensure the toolkit is available.

### NVIDIA Docker

Ensure Docker is installed.

To install NVIDIA Docker:

1. Visit [NVIDIA Docker resources](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html#docker).
2. Follow the Installation instructions.
3. Follow the Configuring Docker instructions.

### Verify GPU compute with ScoutBot demo

From the Terminal window, you can test GPU execution on the laptop by executing some of Scout’s GPU-enabled ML capabilities.

1. Run the following command: `docker run -it --rm --gpus all -p 5000:7860 wildme/scoutbot:main python3 app2.py`
2. Open a separate Terminal window to watch GPU performance.
3. Press CTRL-C to end the test.

```{note}
If the command results in an error containing `nvidia`, you may not have the correct GPU to use this tool. To verify, install `nvtop` and run the command `nvtop` in your console. If you have nvidia GPU, it will display use information and the name of an nvidia GPU. 
```
