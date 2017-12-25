# Welcome to the Quake 3 source code!

<img src="https://ci.appveyor.com/api/projects/status/github/kennyalive/Quake-III-Arena-Kenny-Edition?svg=true" alt="Project Badge">

This repository contains updated version of the original Q3 codebase with reorganized code structure, compatibility fixes, build setup for the latest Visual Studio and modifications that update the core tech but preserve original gameplay, look and feel.

The general direction is to simplify the things. The codebase should be easy to build, executable does not require additional shared libraries to work and we do not talk about OOP here. Only Windows platform is supported.

## Usage
* Build `visual-studio/quake3.sln` solution.
* Copy `quake3-ke.exe` to your local Quake-III-Arena installation folder.

## Vulkan and DX12 support 
Vulkan backend provides the same graphics features as original OpenGL-based one including customization via r_xxx cvars and debug visualization.

Initially DirectX 12 backend was an exercise to learn this graphics API. It turned out the implementation is quite concise, so it was merged into the main branch.


#### New cvars:
* **r_renderAPI** - 3D API to use: 0 - OpenGL, 1 - Vulkan, 2 - DX12. Requires vid_restart.

* **r_twinMode** - Debug feature to compare rendering output between OpenGL/Vulkan/DX12 APIs.
    If enabled, renderer uses multiple APIs and renders current frame to two or three side-by-side windows. Requires vid_restart.

*r_twinMode* is a bitmask. The following values can be combined to enable different graphics backends: 1 - OpenGL, 2 - Vulkan, 4 - DX12. For example: r_twinMode=7 (1+2+4) - enables all backends and renders to 3 windows. r_twinMode=3 (1+2) - enables OpenGL and Vulkan backends and renders to 2 windows.
  
    
#### Additional information:
* Q: How to start game with vulkan support? A: `quake3-ke.exe +set r_renderAPI 1`.
* Q: How to enable vulkan support from Q3 console? A: `\r_renderAPI 1` then `\vid_restart`.
* Q: How to enable twin mode from Q3 console? A: `\r_twinMode 7` then `\vid_restart`.
* Q: How to check that Vulkan backend is really active? A: `gfxinfo` console command reports information about active rendering backend.

## Visual Studio
The project files are provided for Visual Studio 2017. Free community version is available online.

`visual-studio/quake3.vcxproj.user.example` file is provided with example configuration options to start the game from visual studio and to enable vulkan validation layers.

![quake3-ke](https://user-images.githubusercontent.com/4964024/28160268-4f0707d4-67c8-11e7-9009-8540789aab0b.jpeg)
