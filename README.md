#### To run deepstream applications, Make sure DeepStream SDK is properly installed.

#### Check Versions:

##### deepstream-app --version
   
##### Check this tutorial to learn how to install deepstream : https://www.youtube.com/watch?v=Ufd86duobvc

##### Check tensorrt version.  tensorrt –version
  
##### Check cuda version.  nvcc --veersion

##### Clone this repo: git clone https://github.com/AarohiSingla/DeepStream-Yolov8-Jetson-Nano.git

##### Paste yolov8s.pt, yolov8s.onnx, yolov4.weights, yolov4.cfg in this repo.

##### compile the lib:

	export CUDA_VER=10.2
 
For jetson nano (DeepStream 6.0.1 / 6.0 / 5.1 = 10.2)


##### Make the lib:

   make -C nvdsinfer_custom_impl_Yolo clean && make -C nvdsinfer_custom_impl_Yolo
   
   (MAke the changes in MakeFile before executing it)


##### Edit the config_infer_primary_yoloV8.txt file according to your model (example for YOLOv8s with 80 classes)

[property]
onnx-file=yolov8s.onnx
..
num-detected-classes=80

##### Edit the deepstream_app_config file:
...
[primary-gie]
...
config-file=config_infer_primary_yoloV8.txt

##### Testing the model:

deepstream-app -c deepstream_app_config.txt

