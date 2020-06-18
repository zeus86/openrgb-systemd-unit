# openrgb-systemd-unit
User-Systemd-Unit for OpenRGB

---

For use with https://gitlab.com/j-be/OpenRGB on Linux.
This Systemd-User-Unit sets a given Color to your OpenRGB-Controlled RGBs, and turns them off again on shutdown. 

## Usage

```
 mkdir -p ~/.config/systemd/user/
 cp openrgb.service ~/.config/systemd/user/
 systemctl --user daemon-reload
 systemctl --user enable openrgb.service
 ```
 This assumes, that your OpenRGB-Executable is available under `~/bin/OpenRGB/OpenRGB`, as it would be, if you checked the OpenRGB-Repo out in your `~/bin`. 
 
 ## Known Problems
 * If you plan to use Profiles, test them first. I Encountered many combinations, where I end up with broken Profiles, which did not work, even if the User-Unit does. From my understanding the profiles should be world-readable also. 
 * When you also plan to start the GUI of OpenRGB as an autostart-entry of your desktop, you might want to delay the GUI with `sleep5; ./OpenRGB` or something similar. During testing, when both, the Systemd-Unit and the GUI were starting more or less simultaneously, there was a high chance, that the OpenRGB-thread raised by the unit becomes unresponsive, and became a zombie when trying to kill it. 
