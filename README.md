# <div align="center">YoloV5 OpenVino Env Set Up</div>

This tutorial is based on YoLoV5 **Tag 6.1 and it's weight file (yolov5s.pt)**

Python version **3.8.13**

Openvino version **Openvino_2021.4.752**

## Generate Onnx file and openvino IR file (.xml , .bin)

1.Download yolov5 https://github.com/ultralytics/yolov5 (Pay attention to the tag!)
  
2.cd into yolov5 folder

3.```python yolov5\export.py --weights yolov5s.pt --include onnx```
  
4.Check onnx file with NETRON (https://netron.app/)
  
5.Find the output Conv
  
![oxxn](https://user-images.githubusercontent.com/11920034/179160966-57c34d4c-eb6f-429b-9795-aa3741eb1cdb.PNG)

6.Using openvino model_optimizer folder to generate IR file

7.```Python mo --input_model yolov5s.onnx --scale 255 --reverse_input_channels --output Conv_198,Conv_217,Conv_236```

## Yolov5 Openvino Script

Then you can test openvino yolov5 with below commands.

Before running the jupyter notebook, you need to configure openvino.

Step 1 install ANACONDA.

Step 2 open CMD.exe Prompt in ANACONDA.

Step 3 ```cd C:\Program Files (x86)\Intel\openvino_2022\```

run ```setupvars.bat```

Step 4 launch jupter notebook
