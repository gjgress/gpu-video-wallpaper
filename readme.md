# gpu-video-wallpaper

Run a video as animated wallpaper on your Ubuntu/Debian-based desktop with dual/multiple monitor support.

You can either run the application through its GUI or via the command line.

````
CLI usage: gpu-video-wallpaper.sh [--start] [--stop] [--startup] "video_path.mp4"

--start Start playback of video wallpaper. 

--stop  Stop playback.

--startup  Start video wallpaper on system startup.
````

-----

## Installation

To install, simply run `ìnstaller.sh`, which will set up all dependencies, install the necessary files to your system and optionally create a start menu entry.

-----

## Dependencies

All dependencies will be 

- xrandr
- pcregrep
- mpv
- xwinwrap

-----

## changelog

**2021/06/03:**

* Added GUI front-end that handles video file selection and shell parameters and runs everything through to the shell script.
* Created installer to handle dependency checking and menu entry creation.
* Removed the xwinwrap binary from the files and added it as a dependency. The installer will download it from [this repository](https://github.com/mmhobi7/xwinwrap/releases/tag/v0.9) as part of the installation process.
* Added configuration file that stores last used video file and process ID of currently active video wallpaper. That way, stopping video playback will only kill the mpv instance used by the video wallpaper, not all other instances of mpv (including ones that are possibly used for other types of video playback that the user does not want to close).
* Fixed an undesired behaviour where it was possible to start multiple video wallpapers after one another, leading to increased CPU load.
* General clean-up inside gpu-video-wallpaper.sh

Known errors:

* When sourcing 'settings.conf', 'gpu-video-wallpaper.sh' will throw an error because it stumbles over the "\[gpu-video-wallpaper settings\]" section. This section, however, is needed by the python script. Since the shell script does not crash, this error message is tolerated for the moment until I get around to find a more elegant way than just sourcing it 'settings.conf'.
