# scene-text-recogntion
 
> Real-time scene text recognition accelerated with NVIDIA TensorRT
 
## Getting Started
 
To get started with scene-text-recognition, follow these steps.
 
### Step 1 - Clone Repo
 ```
 git clone --recurse-submodules
 ```
### Step 2 Install Dependencies
 
1. Install PyTorch and Torchvision.  To do this on NVIDIA Jetson, we recommend following [this guide](https://forums.developer.nvidia.com/t/72048)
 
2. Install [torch2trt](https://github.com/NVIDIA-AI-IOT/torch2trt)
 
    ```python
    git clone https://github.com/akamboj2/torch2trt.git  -b jax-jp4.6.1-trt7
    cd torch2trt
    sudo python3 setup.py install --plugins
    ```
 
3. Install EasyOCR
    ```python
    cd EasyOCR
    sudo python3 setup.py install 
    ```
4. Install other miscellaneous packages 
 
    ```python
    sudo pip3 install argparse
    pip3 install opencv-python 
    ```
    
 
### Step 3 - Run the example files

There are two separate demo files included: 

#### 1. easy_ocr_demo.py
This program uses EasyOCR to read an image or directory of images and output labeled images. The output is in the labeled-images/ directory

To use easy_ocr_demo:
```
python3 easy_ocr_demo.py images
```
where image is an image file or directory of images.

#### 2. easy_ocr_benchmark.py
Using the pretrained EasyOCR detection and recognition models, we benchmark the throughput and latency and show the speedup after it is converted to a TensorRT engine (TRT).
 
 tor 
| Model | Throughput | Latency |
|-------|-------------|---------------|
| Detection | 12.386  | 84.190 |
| Detection TRT | 24.737 | 48.990 |
| Recognition | 174.518 | 5.900 |
| Recognition TRT | 7118.642 | 0.160 |

To run this benchmark:
```
python3 easy_ocr_benchmark.py
```

This program will store the Torch2trt state dictionaries in the torch2trt_models dictionary. 

#### Run the TRT version of EasyOCR:

TODO; edit easy ocr to allow person to pass in a flag and use the trt version
 
#### More:

To train and run your own models please see the EasyOCR instructions: []
## See also
 
- [trt_pose_hand](http://github.com/NVIDIA-AI-IOT/trt_pose_hand) - Real-time hand pose estimation based on trt_pose
- [torch2trt](http://github.com/NVIDIA-AI-IOT/torch2trt) - An easy to use PyTorch to TensorRT converter
 
- [JetBot](http://github.com/NVIDIA-AI-IOT/jetbot) - An educational AI robot based on NVIDIA Jetson Nano
- [JetRacer](http://github.com/NVIDIA-AI-IOT/jetracer) - An educational AI racecar using NVIDIA Jetson Nano
- [JetCam](http://github.com/NVIDIA-AI-IOT/jetcam) - An easy to use Python camera interface for NVIDIA Jetson
 
## References
 
The scene text recogntion framework used here is a modified version of the EasyOCR open-source code [EasyOCR](https://github.com/JaidedAI/EasyOCR). 

Below are the sources of the default [detection](https://arxiv.org/abs/1904.01941) and [recogntion](https://arxiv.org/abs/1507.05717) models:

 
*  Baek, Y., Lee, B., Han, D., Yun, S., & Lee, H. (2019). Character region awareness for text detection. In Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (pp. 9365-9374).
 
*  Xiao, Bin, Haiping Wu, and Yichen Wei. "Simple baselines for human pose estimation and tracking." Proceedings of the European Conference on Computer Vision (ECCV). 2018.__