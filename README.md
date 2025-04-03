# Garry's Mod via Zink
Run Garry's Mod on Linux via Zink (Opengl-to-Vulkan translation layer) for better compatibility with addons and performance (?)

# Performance Comparison
Zink is **slightly** slower than pure OpenGL on NVIDIA because their proprietary OpenGL driver is highly optimized already - Zink adds a bit of translation overhead from OpenGL to Vulkan.

While on the other hand AMD’s OpenGL driver (Mesa radeonsi) is not as aggressively optimized as NVIDIA’s proprietary OpenGL driver. That's why Zink can sometimes outperform OpenGL on AMD cards.

## NVIDIA Comparison
https://github.com/user-attachments/assets/a8a2112f-cc61-47ca-b38f-5a6aba98ff37

## AMD Comparison
### Soon..

# Addons Compatibility and Mangohud
## Addons
You might see major improvements when playing with various addons. I'll bring up Modern Warfare Base weapon pack as an example.

Sometimes weapon's models won't render properly, so instead of firing a gun you fire with air. Zink fixes this issue.

Every time I join on my own local server with a few SPECIFIC addons, my fps is around 5 until I change fullscreen to borderless or vice versa. Zink also fixes this issue. 
## Mangohud
For some reason MangoHud does not work via OpenGL in Garry's Mod, praise Zink for fixing this issue.
# How to utilize Zink
1. Apply the patcher: [click](https://github.com/wayzaction/gmod-linux-fix)

2. Install common dependencies (Arch-based Distributions):
`sudo pacman -S mesa && sudo pacman -S vulkan-icd-loader`

3. Install dependencies according to your videocard:

NVIDIA: `sudo pacman -S nvidia-utils && sudo pacman -S lib32-nvidia-utils`

AMD: `sudo pacman -S vulkan-radeon && sudo pacman -S lib32-vulkan-radeon`

4. Put these variables in the game's launch parameters:

`__GLX_VENDOR_LIBRARY_NAME=mesa MESA_LOADER_DRIVER_OVERRIDE=zink GALLIUM_DRIVER=zink %command% `

# Enabling/Disabling MangoHUD
1. Go to Garry's Mod root folder.
2. Find hl2.sh and open it with any text editor.
3. Find `export MANGOHUD=1` variable.
4. Change number from `1` to `0` to disable or vice versa
