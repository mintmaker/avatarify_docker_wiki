## Common

**My avatar is distorted**

Please try to match your face position as close as possible to the avatars position and press `X` to calibrate the pose. More [recommendation](https://github.com/alievk/avatarify#driving-your-avatar).

**Avatarify image is frozen in Zoom**

Press on Stop and Start Video in the meeting window.

**No such file or directory: 'vox-adv-cpk.pth.tar'**

Please follow instructions [Download network weights](https://github.com/alievk/avatarify#download-network-weights)

**ASSERT: "false" in file qasciikey.cpp, line 501**

If you have several keyboard layouts, switch to English layout.

## Linux

**My app doesn't see avatarify camera**

1. Exit your app
1. Start Avatarify
1. Start your app and try to find the virtual camera again

**OSError: [Errno 22] Invalid argument (invalid virtual camera)**

If you have several keyboard layouts, switch to English layout.

Make sure `CAMID` in `scripts/settings.sh` is correct. Use `v4l2-ctl --list-devices` to query available devices.

## Mac

**bash run_mac.sh: "Cannot open camera"**

Try to change `MAC_CAMID` in `scripts/settings.sh` (in `avatarify` folder) from 0 to 1, 2, ...

## Windows

**ImportError: DLL load failed: The specified module could not be found.**

Since upgrading to Windows Version 1909 could've deleted previously installed feature packs, you have to install [mediafeaturepack](https://www.microsoft.com/en-us/software-download/mediafeaturepack). Relevant [issue](https://github.com/alievk/avatarify/issues/111).