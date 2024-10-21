# Raspberry Pi AI Camera (IMX500) Neural Network Models

## Running Example Applications
1. All neural network models in this repository can be installed on Raspberry Pi OS with:
```
sudo apt install imx500-models
```

2. Download the [Picamera2 demo/example scripts](https://github.com/raspberrypi/picamera2/tree/main/examples/imx500) with:
```
git clone https://github.com/raspberrypi/picamera2.git
cd picamera2/examples/imx500
```

Each model under [**reference neural network models**](#reference-neural-network-models) lists a Picamera2 application script command line that can be used to demo the neural network. These application scripts broken down into the following high level tasks:

| Application Name                             | Task                  |
|----------------------------------------------|-----------------------|
| [`imx500_classification_demo.py`](https://github.com/raspberrypi/picamera2/blob/main/examples/imx500/imx500_classification_demo.py)                           | Classification   |
| [`imx500_object_detection_demo.py`](https://github.com/raspberrypi/picamera2/blob/main/examples/imx500/imx500_object_detection_demo.py)                       | Object Detection |
| [`imx500_pose_estimation_higherhrnet_demo.py`](https://github.com/raspberrypi/picamera2/blob/main/examples/imx500/imx500_pose_estimation_higherhrnet_demo.py) | Pose Estimation  |
| [`imx500_segmentation_demo.py`](https://github.com/raspberrypi/picamera2/blob/main/examples/imx500/imx500_segmentation_demo.py)                               | Segmentation     |

## Reference Neural Network Models

### Classification
- **Task:** Categorize input data into predefined classes and provide a confidence score.
- **Training dataset:** `Imagenet`. Designed for use in visual object recognition research. It contains over 14 million images, making it one of the most extensive resources available for training deep learning models. It comprises of [1000 classes](https://github.com/raspberrypi/picamera2/blob/main/examples/imx500/assets/imagenet_labels.txt).

| Model                   | [Top 1] Accuracy - Quantized(Float)   | Input Resolution | Picamera2 Example Script                                                                                               |
|-------------------------|---------------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------|
| EfficientNet-B0         | **72.128​** (73.876)                   | 224x224          | `python imx500_classification_demo.py --model /usr/share/imx500-models/imx500_network_efficientnet_bo.rpk`             |
| EfficientNet Lite-0     | **75.252** (75.28)                    | 224x224          | `python imx500_classification_demo.py --model /usr/share/imx500-models/imx500_network_efficientnet_lite0.rpk`          |
| EfficientNetV2-B0       | **76.674​** (76.424)                   | 224x224          | `python imx500_classification_demo.py --model /usr/share/imx500-models/imx500_network_efficientnetv2_b0.rpk`           |
| EfficientNetV2-B1       | **77.032​** (76.93)                    | 240x240          | `python imx500_classification_demo.py --model /usr/share/imx500-models/imx500_network_efficientnetv2_b1.rpk`           |
| EfficientNetV2-B2       | **77.716** (77.94)                    | 260x260          | `python imx500_classification_demo.py --model /usr/share/imx500-models/imx500_network_efficientnetv2_b2.rpk`           |
| MnasNet1.0              | **73.16​** (73.078)                    | 224x224          | `python imx500_classification_demo.py --model /usr/share/imx500-models/imx500_network_mnasnet1.0.rpk`                  |
| MobileNetV2             | **71.572​​** (71.3)                     | 224x224          | `python imx500_classification_demo.py --model /usr/share/imx500-models/imx500_network_mobilenet_v2.rpk`                |
| MobileViT-XS            | **72.326​** (72.412)                   | 256x256          | `python imx500_classification_demo.py --model /usr/share/imx500-models/imx500_network_mobilevit_xs.rpk`                |
| MobileViT-XXS           | **67.44​0** (67.40)                    | 256x256          | `python imx500_classification_demo.py --model /usr/share/imx500-models/imx500_network_mobilevit_xxs.rpk`               |
| RegNetX-002             | **68.352​** (68.20)                    | 224x224          | `python imx500_classification_demo.py --model /usr/share/imx500-models/imx500_network_regnetx_002.rpk`                 |
| RegNetY-002             | **69.424​** (69.60)                    | 224x224          | `python imx500_classification_demo.py --model /usr/share/imx500-models/imx500_network_regnety_002.rpk`                 |
| RegNetY-004             | **73.83​0** (73.37)                    | 224x224          | `python imx500_classification_demo.py --model /usr/share/imx500-models/imx500_network_regnety_004.rpk`                 |
| ResNet-18               | **68.57​** (68.546)                    | 224x224          | `python imx500_classification_demo.py --model /usr/share/imx500-models/imx500_network_resnet18.rpk`                    |
| ShuffleNetV2-x1.5       | **72.194​** (72.498)                   | 224x224          | `python imx500_classification_demo.py --model /usr/share/imx500-models/imx500_network_shufflenet_v2_x1_5.rpk`          |
| SqueezeNet-V1.0         | **57.598** (57.584)                   | 224x224          | `python imx500_classification_demo.py --model /usr/share/imx500-models/imx500_network_squeezenet1.0.rpk`               |  

### Object Detection
- **Task:** Identify and locate multiple objects within an image by classifying each object.
- **Training dataset**: `COCO`. Designed to encourage research on a wide variety of object categories and is commonly used for benchmarking computer vision models. It comprises of [80 classes](https://github.com/raspberrypi/picamera2/blob/main/examples/imx500/assets/coco_labels.txt).


| Model                           | [mAP] Accuracy - Quantized(Float)  | Input Resolution | Picamera2 Example Script                                                                                                        |
|---------------------------------|------------------------------------|------------------|---------------------------------------------------------------------------------------------------------------------------------|
| Efficientdet Lite-0 (pp*)       | **0.252** (0.2518)​                 | 320x320          | `python imx500_object_detection_demo.py --model /usr/share/imx500-models/imx500_network_efficientdet_lite0_pp.rpk`              |
| Nanodet Plus                    | **0.332**​ (0.3316)                 | 416x416          | `python imx500_object_detection_demo.py --model /usr/share/imx500-models/imx500_network_nanodet_plus_416x416.rpk`               |
| Nanodet Plus (pp*)              | **0.32​0** ​(0.3232)                 | 416x416          | `python imx500_object_detection_demo.py --model /usr/share/imx500-models/imx500_network_nanodet_plus_416x416_pp.rpk`            |
| SSD MobileNetV2 FPN Lite (pp*)  | **0.218** (0.219) ​                 | 320x320          | `python imx500_object_detection_demo.py --model /usr/share/imx500-models/imx500_network_ssd_mobilenetv2_fpnlite_320x320_pp.rpk` |

_*pp = post-processing is included in the network and is executed on the IMX500 Edge AI Processor_

### Semantic Segmentation
- **Task:** Assign a category to each pixel in an image, offering a comprehensive analysis of the image's content.
- **Training dataset:** `PASCAL VOC`. Designed to encourage research on a wide variety of object categories and is commonly used for benchmarking computer vision models. It comprises of [20 object categories](http://host.robots.ox.ac.uk/pascal/VOC/voc2007/htmldoc/voc.html#SECTION00032000000000000000).

| Model                              | [mIOU] Accuracy - Quantized(Float)      | Input Resolution | Picamera2 Example Script                                                                                               |
|------------------------------------|-----------------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------|
| DeepLabv3Plus                      | **0.7214​** (0.724) ​                     | 320x320          | `python imx500_segmentation_demo.py  --model /usr/share/imx500-models/imx500_network_deeplabv3plus.rpk`                         |

### Pose Estimation
- **Task:** Detect key points or landmarks on objects or humans in images or videos.
- **Training dataset:** `COCO (KeyPoints)`

| Model           | [mAP] Accuracy - Quantized(Float)    | Input Resolution | Picamera2 Example Script                                                                                               |
|-----------------|--------------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------|
| HigherHRNet     | **0.188​** (0.1867)                   | 288x384          | `python imx500_pose_estimation_higherhrnet_demo.py --model /usr/share/imx500-models/imx500_network_higherhrnet_coco.rpk`        |

## Licenses

Models in this repo are distributed under a number of licenses listed in in the [LICENSES](LICENSES) directory.
