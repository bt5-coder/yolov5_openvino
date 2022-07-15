# YoloV5 OpenVino Env Set Up

This tutorial is based on YoLoV5 Tag 6.1 and it's weight file (yolov5s.pt)
Python version 3.8.13
Openvino version Openvino_2021.4.752

## generate Onnx file and openvino IR file (.xml , .bin)

Download yolov5 https://github.com/ultralytics/yolov5 (Pay attention to the tag!)
Directly run python in yolov5 folder
yolov5\export.py --weights yolov5s.pt --include onnx
check onnx file with NETRON (https://netron.app/)
Find the output Conv





Before running the jupyter notebook, you need to configure openvino.
Step 1 install ANACONDA.
Step 2 open CMD.exe Prompt in ANACONDA.
Step 3 cd C:\Program Files (x86)\Intel\openvino_2022\
run setupvars.bat
Step 4 launch jupter notebook
