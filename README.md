# PiCamLite

To start using this go to Releases download the zip and start "picamlite.exe"

### What is this for?
This tool is an **alternative to runtime.exe** bundled with the aSeeVR runtime for the Droolon Pi 1 / Pimax eyetracking module. The official software, even with efforts from the likes of Guppy *(thanks for talking with me and allowing me to use some of your changes!)*, is still very limited in tracking quality. Because of this I first wrote DroolonStreamer to steal the images from runtime.exe to pipe into EyeTrackVR, which worked great, but meant I was still executing the HEAVY algorithms 7invensun applies.<br>
This program replaces runtime.exe, only using certain parts of it's functions to initialize the hardware and get through integrity checks/DRM. *That's why there is 200 odd MB of files for an app that needs 50MB of RAM to run, most of it is only needed to not upset the hotwired DRM and never actually loads!*

### Why not open source?
**Most of it was created using decompilation with Ghidra**, so it's using reverse engineered copyrighted code. I can't in good conscience publish reverse commercial code and probably also legally can't. *Please feel free to run the app through scanners, have fun with Ghidra yourself etc, I know precompiled binaries are sketchy and I wish I could share stuff!*

### How big is the benefit?
**In my usecase with a 9800X3D it dropped a whole 12% off my CPU usage (an entire core)** to not run the official bad inference models. RAM usage dropped by around 300-400 MB, but because runtime.exe is very variable in use it could be less or more (it probably has a memory hole somewhere?).

### What is lost over runtime.exe?
**Every single official tracker feature** which basically amounts to you no longer having access to the absolutely rancid dynamic foveation that wasn't fast enough anyways and direct access to tracker values (which also weren't great... or even working in 80% of cases).
