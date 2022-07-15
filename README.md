# <div align="center"> YoloV5 OpenVino Inference Tutorial </div>


This tutorial is based on YoLoV5 **Tag 6.1 and it's weight file (yolov5s.pt)**

Python version **3.8.13**

Openvino version **Openvino_2021.4.752**

**The script, openvino model, tutorial can not only run in Windows, but also verified on Raspberry + NCS2**

## Generate Onnx file and openvino IR file (.xml , .bin)

1.Download yolov5 https://github.com/ultralytics/yolov5 (Pay attention to the tag!)
  
2.cd into yolov5 folder

3.```python yolov5\export.py --weights yolov5s.pt --include onnx```
  
4.Check onnx file with [**NETRON**](https://netron.app/)
  
5.Find the three output Conv (step 7 needs them)
  
![oxxn](https://user-images.githubusercontent.com/11920034/179160966-57c34d4c-eb6f-429b-9795-aa3741eb1cdb.PNG)

6.Using openvino model_optimizer folder to generate IR file, model_optimizer path is ```C:\Program Files (x86)\Intel\openvino_2021.4.752\deployment_tools\model_optimizer```

***If you are using openvino on raspberry, there is no model_optimizer folder, you need using your PC to convert the IR model.***

7.```Python mo --input_model yolov5s.onnx --scale 255 --reverse_input_channels --output Conv_198,Conv_217,Conv_236 --data_type FP16```

Tips: latest version yolov5 export.py can directly transfer .ps model into .xml and .bin, but I was failed, so I used openvino self mo.py file to transfer the IR model.

## Yolov5 Openvino and ipynb environment Set Up 

**Pay attention, the tutorial can only inference IMG, no video and cam is supported, if you need inference IMG or video, next chapter would be helpful**

Then you can test openvino yolov5 with below commands.(ipynb)

Before running the jupyter notebook, you need to configure openvino.

Step 1 install ANACONDA. 

Step 2 open CMD.exe Prompt in ANACONDA. **(I am using ANACONDA, you can also open a cmd window by your environment)**

Step 3 ```cd C:\Program Files (x86)\Intel\openvino_2022\```

run ```setupvars.bat``` 

Step 4 launch jupter notebook  ``` jupyter notebook ``` 

## Run Yolov5 Openvino Script and tutorial

If you are using Intel CPU 

```python openvino_test.py.py -i cam.jpg -m yolov5s.xml```

If you are using Intel NCS2

```python openvino_test.py.py -i cam.jpg -m yolov5s.xml -d MYRAID```

## Reference

1. **https://github.com/ultralytics/yolov5/issues/552**

2. **https://github.com/openvinotoolkit/openvino/issues/11458**

3. **https://blog.csdn.net/qq_44166630/article/details/119994949?spm=1001.2014.3001.5501**

4. **https://github.com/violet17/yolov5_demo**

5. **https://github.com/ultralytics/yolov5**
