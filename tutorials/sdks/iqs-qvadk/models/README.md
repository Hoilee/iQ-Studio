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
| Face landmark | DMS | [Google MediaPipe Face Landmarker](https://ai.google.dev/edge/mediapipe/solutions/vision/face_landmarker) |

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

## Face Landmark

The face landmark model is used by DMS on the face found by SCRFD. DMS needs it to run; PPE and defect detection do not.

The DMS application expects the file `models/tflite/face_landmarks_detector_float16.tflite` under `tutorials/sdks/iqs-qvadk/`.

1. Download the Google MediaPipe Face Landmarker package. It is a small zip file of about 4 MB.

    ```bash
    curl -L -o face_landmarker.task \
        https://storage.googleapis.com/mediapipe-models/face_landmarker/face_landmarker/float16/1/face_landmarker.task
    ```

2. Extract the landmark model from the package, then copy it to the iqs-qvadk directory and rename it. Replace `<iQ-Studio>` with the path of your iQ-Studio clone.

    ```bash
    unzip face_landmarker.task face_landmarks_detector.tflite
    mkdir -p <iQ-Studio>/tutorials/sdks/iqs-qvadk/models/tflite
    cp face_landmarks_detector.tflite \
       <iQ-Studio>/tutorials/sdks/iqs-qvadk/models/tflite/face_landmarks_detector_float16.tflite
    ```

3. Check that the file is in place.

    ```bash
    ls -l <iQ-Studio>/tutorials/sdks/iqs-qvadk/models/tflite/face_landmarks_detector_float16.tflite
    ```

## Next Step

Once the models you need are in place, run the application from the iqs-qvadk directory as described in the [application guide](../README.md).
