<!--
 Copyright (c) 2025 Innodisk Corp.
 
 This software is released under the MIT License.
 https://opensource.org/licenses/MIT
-->

# iQS-Streampipe
Streampipe is a C++ GStreamer and OpenCV-based multi-stream video processing pipeline. It supports real-time video input from UVC cameras or video files, and displays composite video output using a GStreamer compositor.

The set IDs are ordered on the screen from left to right, then from top to bottom
>Note: The demo GIF may take some time to load. If it does not appear immediately, please wait.

<br />
<div align="center"><img width="80%" height="80%" src="./fig/image0.png"></div>
<br />

<br />
<div align="center"><img width="80%" height="80%" src="./fig/gif0.gif"></div>
<br />

# How to Deploy

## Supported Versions

| BSP Version | QLI Version |
| :--- | :--- |
| 2.5.x | 2.0 |

- **BSP version** — read `/etc/innodisk/BSP-version`.
- **QLI version** — run `uname -a` and look for the `qli-<version>` field.

> Note: On QLI 1.x, see the [changelog](../../../docs/changelog.md) for the matching iQ-Studio release. To move to QLI 2.0, flash an image from [meta-iQ__manifest](https://github.com/InnoIPA/meta-iQ__manifest).

## What You Need?

1. At least 10 GB of free disk space
2. A monitor

## How to Start?
    
```bash
git clone https://github.com/InnoIPA/iQ-Studio.git
cd iQ-Studio
./install.sh
```

# How to Use
1. Use iqs-launcher and autotag tools to automatically pull or build a compatible docker image.
    
    ```bash
    iqs-launcher --autotag iqs-streampipe
    ```
    
2. You will see it on the screen.
    >Note: The demo GIF may take some time to load. If it does not appear immediately, please wait.
    
    ![Recording 2025-08-13 at 15.22.58.gif](./fig/gif1.gif)

# How to Change the Custom Model and Video Source

For advanced features and usage examples, visit this [page](../../sdks/iqs-streampipe/README.md) to learn more.

# Known Issue
The current Qualcomm codec driver may, under certain conditions, cause the system to restart unexpectedly. If this occurs, re-run the process to continue.
