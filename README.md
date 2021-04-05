# MRI Classification App

We are team technophiles and participated in hackathon organized by Microsoft Azure. 

Our college name: Pandit Deendayal Energy University(PDEU)

Team Members: Denish Kalariya, Rushabh Thakkar, Divy Patel, and Yug Thakkar.

---
services: cognitive-services, custom-vision-MRI Detection(HealthCare Sector), 
platforms: java, Android, Azure ,Tensorflow
author: Denish Kalariya, Rushabh Thakkar, Divy Patel, Shubham Vyas, Yug Thakkar
---

# Android application for TensorFlow models of MRI to detect exported from Custom Vision Service

This sample application demonstrates how a [Custom Vision Service](https://www.customvision.ai) exported TensorFlow model is added to a real-time image classification application. 

## Getting Started

### Prerequisites

- [Android Studio (latest)](https://developer.android.com/studio/index.html)
- Android device
- An account at [Custom Vision Service](https://www.customvision.ai) 


### QuickStart

1. Clone the repository and open the project `image_classification` in Android Studio
2. Build and run the sample on your Android device


### Replacing the sample model with your own classifier 
The model provided with the sample recognizes some fruits. To replace it with your own model exported from [Custom Vision Service](https://www.customvision.ai) do the following, and then build and launch the application:

  1. [Create and train](https://docs.microsoft.com/en-us/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier) a classifier with the Custom Vision Service. You must choose a "compact" domain such as **General (compact)** to be able to export your classifier. If you have an existing classifier you want to export instead, convert the domain in "settings" by clicking on the gear icon at the top right. In setting, choose a "compact" model, Save, and Train your project.


  2. Export your model by going to the Performance tab. Select an iteration trained with a compact domain, an "Export" button will appear. Click on *Export* then *TensorFlow Lite* then *Export.* Click the *Download* button when it appears. A *.zip* file will download that contains all of these three files:
      - TensorFlow model (`.tflite`)
      - Labels (`.txt`)
      - Export manifest file (`cvexport.manifest`).

  3. Drop all of `model.tflite`, `labels.txt` and `cvexport.manifest` into your Android project's `assets/sample-tflite.cvmodel` folder.
  
  4. Build and run.

*This sample has been tested on Pixel devices*


### Compatibility

This latest sample application relies on the new Android library *Custom Vision inference run-time* (or simply *run-time*) to take care of compatibility. It handles:
- The following two were originally handled in ‘MSCognitiveServicesClassifier.classifyImage’ but now been encapsulated into the run-time.
- __Subtract mean values__: Check if the exported model has a normalization layer, and if not subtract the RGB mean values from their respective pixel RGB components of the input image before passing to TensorFlow inference engine.
- __Resize and crop input image__: Resize the image such that the longest dimension is 1600 pixels in length then take a center crop after which the image is resized to dimensions is then resized to dimensions that the model network is expecting.

- __Version check__: Check the version of the exported model by looking at `cvexport.manifest` (more specifically, look for *ExporterVersion* field) and switch logic depending on model version.

    - __Forward compatibility__: It is when model version is newer than run-time's maximum supported model version.
    
        - Major version is greater: Throw exception (supposing model format is unknown)

        - Major version is same but minor version is greater: Still works. Run inference.

    - __Backward compatibility__: Any newer version of the run-time should be able to handle older model versions.

> **Video:** [Link to Video](https://youtu.be/bV5bhKFsdYY)

> **APK file:** [Link to APK File](https://drive.google.com/file/d/10DnwVU_na934VCRcrFEpBOYV6pfqOaVp/view?usp=sharing)


> **Profiles of team member:** 

- Denish Kalariya

[Linkedin](https://www.linkedin.com/in/denish-kalariya-b22a641ba/)
[Github](https://github.com/Dk-21)

- Rushabh Thakkar

[Linkedin](https://www.linkedin.com/in/rushabhthakkar/)
[Github](https://github.com/rushabh1605)

- Divy Patel

[Linkedin](www.linkedin.com/in/divy-patel-7b369118b)
[Github](https://github.com/Divy2000)

- Yug Thakkar

[Linkedin](https://www.linkedin.com/in/yug-thakkar-6a0021179/)
[Github](https://github.com/yugthakkar16)
