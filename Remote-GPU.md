### Setup server

#### Linux

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

### Run server

Linux:
```
bash run.sh --is-worker
```

Windows:
```
run_windows.bat --is-worker
```

### Run client

Clients are supported on all platforms. Use this command to run a client:
```
run_mac.sh --worker-host server_address
```
where `server_address` is the IP address or the hostname of the server. Use `run_windows.bat` for Windows and `run.sh` for Linux.