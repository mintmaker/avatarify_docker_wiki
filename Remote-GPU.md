### Setup server

#### Linux
The recommended way to setup a Linux server for Avatarify is [Docker](#docker).
This sections explains a native installation.

This guide will assume the OS is Ubuntu 18.04 and latest NVIDIA drivers installed.

See also [provisioning a cloud-based GPU instance](https://github.com/alievk/avatarify/wiki/Provisioning-a-cloud-based-GPU-instance).

1. Download [Miniconda Python 3.7](https://docs.conda.io/en/latest/miniconda.html#linux-installers) and install it:
```bash
bash Miniconda3-latest-Linux-x86_64.sh
```
2. Clone `avatarify` and install its dependencies:
```bash
git clone https://github.com/alievk/avatarify.git
cd avatarify
bash scripts/install.sh --no-vcam
```
3. [Download network weights](#download-network-weights) and place `vox-adv-cpk.pth.tar` file in the `avatarify` directory (don't unpack it).

#### Windows

This guide will assume the OS is Windows 10 and latest NVIDIA drivers installed.

1. Install [Miniconda Python 3.7](https://docs.conda.io/en/latest/miniconda.html#windows-installers).
2. Install [Git](https://git-scm.com/download/win).
3. Press Windows button and type "miniconda". Run suggested Anaconda Prompt.
4. Download and install Avatarify (please copy-paste these commands and don't change them):
```bash
git clone https://github.com/alievk/avatarify.git
cd avatarify
scripts\install_windows.bat
```
5. [Download network weights](#download-network-weights) and place `vox-adv-cpk.pth.tar` file in the `avatarify` directory (don't unpack it).

#### Docker
Docker images are only availabe on Linux.

1. Install Docker following the [Documentation](https://docs.docker.com/engine/install/). Then run this [step](https://docs.docker.com/engine/install/linux-postinstall/#manage-docker-as-a-non-root-user) to make docker available for your user.
2. For using the gpu (hardly recommended): Install nvidia drivers and [nvidia docker](https://github.com/NVIDIA/nvidia-docker#quickstart).
2. Clone `avatarify`:
```bash
git clone https://github.com/alievk/avatarify.git
```
3. Build the Dockerfile:
```bash
docker build -t avatarify
```

### Run server

Linux (native and with Docker):
```
bash run.sh --is-worker
```
Add the flag `--no-gpus` if you don't have a GPU installed.

Windows:
```
run_windows.bat --is-worker
```

### Run client

Clients are supported on all platforms. Use this command to run a client:
```
run_mac.sh --is-client --in-addr tcp://server_address:5557 --out-addr tcp://server_address:5558
```
where `server_address` is the IP address or the hostname of the server. Use `run_windows.bat` for Windows and `run.sh` for Linux. If you run the server with Docker and the client is on the same machine add the `--is-local-client` flag.
