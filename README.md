# Valorant-Aimbot
An external aimbot with a UI and hitbox overlay. This is a showcase, code will not be made public to prevent cheating.

![gif](./aimbot.gif)

- Fully computer vision based thanks to [OpenCV](https://github.com/opencv/opencv-python)
- No game modifications or memory access
- Undetectable by Riot Vanguard's anti-cheat system

## How it Works

### Target detection

- Screenshot centre
- Filter screenshot for a range of purple pixels to create a binary image
- Recognise clusters of pixels and group them together to get the target's hitbox and head position
- This method is much faster than using my YOLOv5 image classification model used in [Valorant-AI-Bot](https://github.com/mata402/Valorant-AI-Bot), so there is minimal latency between the game and the hitbox overlay

### Input

- Find distance between crosshair and the target's head
- Calculate mouse input, accounting for recoil and smoothing
- Inputs are encoded to an Arduino Leonardo
- Arduino sends mouse input back to the computer as a physical HID to bypass Riot Vanguard's anti-cheat system

### overlay

- PyQt5 transparent window overlayed on the game
- Hitboxes are updated every frame with minimal latency