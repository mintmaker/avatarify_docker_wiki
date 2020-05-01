# Linux

### Remove Avatarify  
Find where you downloaded `avatarify` directory and delete it.

### Remove Miniconda
1. Open terminal window
2. Find `conda` location:  
```
which conda  
```  
3. Remove Miniconda directory. For example, if the previous command returned `/home/einstein/miniconda3/bin/conda`, then remove `/home/einstein/miniconda3`:  
```
rm -rf /home/einstein/miniconda3
``` 

If you don't want to remove Miniconda, then just remove `avatarify` environment:
```
conda env remove --name avatarify
```

### Remove v4l2loopback
If v4l2loopback was installed using `scripts/install.sh`, then just remove `v4l2loopback.ko`:
```
sudo rm /lib/modules/$(uname -r)/extra/v4l2loopback.ko
```

# Mac

### Remove Avatarify  
Find where you downloaded `avatarify` directory and delete it.

### Remove Miniconda
#### If Miniconda was installed from a downloaded package:  
1. Open terminal window
2. Find `conda` location:  
```
which conda  
```  
3. Remove Miniconda directory. For example, if the previous command returned `/opt/miniconda3/bin/conda`, then remove `/opt/miniconda3`:  
```
rm -rf /opt/miniconda3
``` 

#### If Miniconda was installed using brew:
1. Open terminal window
2. Run:
```
brew cask uninstall miniconda
```

If you don't want to remove Miniconda, then just remove `avatarify` environment:
```
conda env remove --name avatarify
```

### Remove CamTwist  
Go to Programs and move CamTwist to Trash.

There is a known issue when Mac can't recognize your camera after CamTwist removal. If that's the case, please check `(Your HD) -> Library -> CoreMediaIO -> Plug-Ins -> DAL` and delete `CamTwist.plugin`.

# Windows

### Remove Avatarify
Find where you downloaded `avatarify` directory and delete it.

### Remove Miniconda
Go to Settings -> Apps and remove Miniconda3.

If you don't want to remove Miniconda, then just remove `avatarify` environment. Open Miniconda prompt and run:
```
conda env remove --name avatarify
```

### Remove OBS Studio
Go to Settings -> Apps and remove OBS Studio and OBS-VirtualCam.

### Remove Git
Go to Settings -> Apps and remove Git.