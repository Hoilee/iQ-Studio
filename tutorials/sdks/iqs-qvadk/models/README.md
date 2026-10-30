<!--
 Copyright (c) 2025 Innodisk Corp.
 
 This software is released under the MIT License.
 https://opensource.org/licenses/MIT
-->

# iQS-QVADK: Models You Need to Provide

Some models used by iqs-qvadk are not distributed with iQ-Studio, because their license does not allow us to redistribute them. You need to download them yourself before running the applications that use them.

> **License notice:** These models are provided by third parties. You are responsible for reading their license terms and confirming that your use, especially commercial use, is allowed. Innodisk does not provide or license them.

| Model | Used by | Source |
| --- | --- | --- |
| SCRFD (face detection) | PPE (face mosaic), DMS | [InsightFace](https://github.com/deepinsight/insightface/tree/master/detection/scrfd), converted by [PINTO_model_zoo](https://github.com/PINTO0309/PINTO_model_zoo/tree/main/129_SCRFD) |

## SCRFD

SCRFD is the face detection model behind the **face mosaic** in the PPE demo: it finds the faces in every channel so they can be blurred for privacy. DMS also uses it to find the driver's face. There is nothing to configure; once the file below is in place, the face mosaic runs automatically. Without it, PPE and DMS fail to start.

The applications expect the file `models/tflite/scrfd_integer_quant.tflite` under `tutorials/sdks/iqs-qvadk/`.

1. Download the model package. It is about 3.5 GB, so make sure you have enough disk space.

    ```bash
    git clone --depth 1 https://github.com/PINTO0309/PINTO_model_zoo
    cd PINTO_model_zoo/129_SCRFD
    sh download.sh
    ```

2. Copy the `500m_bnkps` 480x640 model to the iqs-qvadk directory and rename it. Replace `<iQ-Studio>` with the path of your iQ-Studio clone.

    ```bash
    mkdir -p <iQ-Studio>/tutorials/sdks/iqs-qvadk/models/tflite
    cp saved_model_scrfd_500m_bnkps_480x640/model_integer_quant.tflite \
       <iQ-Studio>/tutorials/sdks/iqs-qvadk/models/tflite/scrfd_integer_quant.tflite
    ```

3. Check that the file is in place.

    ```bash
    ls -l <iQ-Studio>/tutorials/sdks/iqs-qvadk/models/tflite/scrfd_integer_quant.tflite
    ```

    The file size should be 812312 bytes.

4. Run the application from the iqs-qvadk directory as described in the [application guide](../README.md).

> Note: Use exactly the `500m_bnkps` 480x640 `model_integer_quant.tflite`. Other SCRFD variants have a different input size or output layout and do not work with the provided configs.
