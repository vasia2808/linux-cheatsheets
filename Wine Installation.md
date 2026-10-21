# Wine Installation

### Install packages

For video playback: **gst-libav**, **gst-plugins-bad** or **gst-plugins-ugly** - test in a specific game
**vulkan-intel** for **Intel** GPU
**vulkan-radeon** for **AMD** GPU

```bash
sudo pacman -S wine wine-mono wine-gecko winetricks zenity gst-libav vulkan-radeon
```

### Install libraries

**dxvk** - for **DirectX 9-11** games
**vkd3d** - for **DirectX 12** games

```bash
winetricks dxvk vkd3d
```

Alternative way:

```bash
paru -S dxvk-bin vkd3d-proton-bin
setup_dxvk install
setup_vkd3d_proton install
```