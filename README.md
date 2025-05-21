# OSSC Pro SD CARD

[![en](https://img.shields.io/badge/lang-en-red.svg)](README.en.md)
[![es](https://img.shields.io/badge/lang-es-yellow.svg)](README.es.md)

This repository contains my custom configuration for the OSSC Pro SD card, including profiles, scaling algorithms and additional CRT masks. 


## Contents of the SD Card
I have uploaded the complete structure of my SD card, ready to be cloned or downloaded. Be sure to keep the files organised so that OSSC Pro will detect them correctly:

````
├─ ossc_pro.bin              # Firmware update (not included)
├─ prof_n_i.txt              # Names for internal profiles 0-9
├─ prof_n.txt                # Names for profiles in SD 0-99
├─ prof00.bin … prof99.bin   # Profiles saved on SD (slots 00-99)
│
├─ edid/                     # Custom EDID files (not included)
│   └─ your_edid.bin
│
├─ scl_alg/                  # Scaling algorithms
│   ├─ *.cfg                 # Custom scaling algorithm configurations
│   └─ *.txt                 # 64-phase filters from MiSTer project
│
└─ shmask/                   # CRT mask files from MiSTer project
    └─ *.txt
````
Note: It's important that you do not create subfolders within scl_alg/ or shmask/, as OSSC Pro only detects files directly in those folders.
## Profiles
In the root of the repository, you will find my profiles saved on the SD (prof00.bin to prof99.bin), optimised for 4K TVs like the Xiaomi TV F2. Profiles included to date:

* prof00.bin → MyDefault: Default setting for a 4K TV, ideal as a starting point.
* prof01.bin → PS2_480p/i_P4: For 480p/480i 4:3 content (e.g. Persona 4).
* prof02.bin → PS2_480p/i/W_P4: For 480p/480i 16:9 content (e.g. Persona 4).
* prof03.bin → PS2_240p_Pixel: For 240p content in LM mode.
* prof04.bin → PS2_480i_CSNK2: For 480i 4:3 Pixel Art content (e.g. Capcom vs SNK 2).
* prof05.bin → NS_720p1080pScl: For Nintendo Switch (720p/1080p).
* prof06.bin → NS_Retro_LM: For Nintendo Switch (Pixel Art 720p in LM mode).

The prof_n.txt file associates these slots with names that are readable in the OSSC Pro menu. For the names to appear correctly, you must load the corresponding slot profile and then save it to the same slot from OSSC Pro.

Additionally, prof_n_i.txt maps OSSC Pro internal profile slots to custom names.
## Scaling Algorithms (scl_alg/)
In the scl_alg/ folder you will find my custom settings in .cfg format. These combine internal OSSC Pro algorithms (nearest, lanczos3, lanczos3_13, lanczos4, gs_sharp, gs_medium, gs_soft) with 64 phase filters from the MiSTer project (https://github.com/MiSTer-devel/Filters_MiSTer/) like Bicubic.txt, SNES Interpolation, Scanlines, etc..

Note: The scaling algorithms in .txt format are 64-phase filters, as other phases are not supported by OSSC Pro. If you want to use visual effects like Scanlines_*.txt, activate them only in line 2 of your .cfg file and do not combine the scanlines of the scaling algorithms with the internal scanlines function of OSSC Pro.
## CRT masks (shmask/)
The shmask/ folder contains .txt files with CRT masks from the MiSTer project (https://github.com/MiSTer-devel/ShadowMasks_MiSTer). These are loaded in the Post-proc → Shadow mask → Custom menu of OSSC Pro and are divided into:

* Simple (monochrome) masks, such as grids or vertical stripes.
* Complex (multichromatic) masks, sorted by subpixels (RGB, BGR, etc.), including root files such as PVM, Trinitron or Bayer.

Simply copy the mask of your choice, select it in the OSSC Pro menu, adjust the intensity and save the changes with "SD Save profile".