# PiCamLite - Droolon Pi 1 camera access tool
![new stuff](https://github.com/user-attachments/assets/99b2bbdc-5279-437e-ba84-688fc41fb9c6)

## Disclaimer
**Your tracker includes a self-bricking function. PiCamLite uses knowledge gained from decompilation to use gutted official functions to prevent triggering this protection. I've tested this for hours on my own hardware, HOWEVER I'm not responsible for bricked trackers!**

## Usage
To start using PiCamLite go to the [Releases](https://github.com/FynnleyNeko/PiCamLite/releases/latest) download the zip and start **picamlite.exe**!

**Configuration is now entirely accessible within the UI**, but *you can still use config.ini* if you really want:
```
[STREAM]
port=8080         # This sets the port of the stream, value is clamped between 1024 and 65535 on launch
framerate=100     # Framerate from 1 to 100, value is seen as "if possible", that means when at 100 
                  # and in highres mode it will automatically be limited to 30 (the hardware limit)
quality=90        # JPEG quality from 1 to 100
[CAMERA]
exposure=100      # Exposure percentage from 70% to 130%, adjusts the brightness of the image
irismode=0        # 0 for 320x240 mode and 1 for 640x480 mode
[SAVED]
preview=0         # This value saves if the preview images were shown on the last run
settings=0        # This value saves if the settings were expanded on the last run
```

## Frequently Asked Questions
### What is this for?
>This tool is an **alternative to the official aSeeVR runtime** for the Droolon Pi 1 / Pimax eye-tracking module. The official software, even with [efforts from the likes of Guppy](https://github.com/guppyexpress/Pimax-Eye-Tracking-Fix) *(who graciously allowed me to use some of his mods here)*, is still very limited in tracking quality. Because of this I first wrote [DroolonStreamer](https://github.com/FynnleyNeko/DroolonStreamer) to steal the images from runtime.exe to pipe into EyeTrackVR, which worked great, but meant I was still executing the **HEAVY** algorithms 7invensun applies.<br>
This program replaces runtime.exe, only using certain parts of it's functions to initialize the hardware and get through integrity checks/DRM. *That's why there is some files you might recognize the names of, even if they are by far smaller than the official files*

### Why not open source?
>**Most of it was created using decompilation with Ghidra**, so it's using a lot of stuff even I don't have the source to. But most importantly I can't in good conscience publish code that might eventually be able to circumvent 7invensuns code for trackers that are not year old abandonware. *Please feel free to run the app through scanners, have fun with Ghidra yourself etc, I know precompiled binaries are sketchy and I wish I could share stuff!*

### How big is the benefit?
>**In my usecase with a 9800X3D it dropped a whole 12% off my CPU usage (an entire core)** to not run the official bad inference models. RAM usage dropped by around 300-400 MB, but because runtime.exe is very variable in use it could be less or more (it probably has a memory hole somewhere?).

### What is lost over runtime.exe?
>**Every single official tracker feature** which basically amounts to you no longer having access to the absolutely rancid dynamic foveation that wasn't fast enough anyways and direct access to tracker values (which also weren't great... or even working in 80% of cases). *But hey you gain the fancy 640x480 mode, that should also count for something right?*
