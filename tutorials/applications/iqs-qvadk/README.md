<!--
 Copyright (c) 2025 Innodisk Corp.
 
 This software is released under the MIT License.
 https://opensource.org/licenses/MIT
-->

# iQS-QVADK

QVADK is a multi-stream AI video pipeline for vertical applications. This demo runs the **PPE (Personal Protective Equipment) detection** application: it analyzes several video channels at the same time with a YOLO26n INT8 model running on the NPU, and displays the detection results on a monitor.

>Note: The demo GIF may take some time to load. If it does not appear immediately, please wait.

<br />
<div align="center"><img width="80%" height="80%" src="./fig/gif0.gif"></div>
<br />

# How to Deploy

## Supported Versions

Pick the iQ-Studio version that matches your platform:

| Your platform | iQ-Studio version |
| :--- | :--- |
| BSP 2.5.x (QLI 2.0) | Latest (`main`) |

- **Check BSP:** `cat /etc/innodisk/BSP-version`
- **Check QLI:** `uname -a`, then look for the `qli-<version>` field.

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

1. Use iqs-launcher and autotag tools to automatically pull or build a compatible docker image.

    ```bash
    iqs-launcher --autotag iqs-qvadk
    ```

2. You will see the PPE detection result on the screen.
    >Note: The demo GIF may take some time to load. If it does not appear immediately, please wait.

    ![ppe demo](./fig/gif0.gif)

# How to Switch and Run the Other Applications

For advanced features and usage examples, visit this [page](../../sdks/iqs-qvadk/README.md) to learn more.
