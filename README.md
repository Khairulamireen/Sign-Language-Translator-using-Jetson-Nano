# Sign-Language-Translator-using-Jetson-Nano


This is my project developed during my Deep Learning in Intelligent Video Analytics and Computer Vision Workshop in IIUM.

This project is about translating Sign Language Alphabet using Jetson Nano.
This project focuses on the Image Classification where every hand posture will be classified to its letter class.

The methodology of this project are:
- Collecting Datasets.
- Training using Resnet18.
- Converting the .pth file into .onnx file.
- Run it on camera.

! Important !
Make sure you have install Python and PyTorch on your Device or Environment.

# Lets Start!
First of all, you need to git clone this repositary. On your Terminal,
```
git clone https://github.com/Khairulamireen/Sign-Language-Translator-using-Jetson-Nano.git
```
After cloning, create folders named 'data' and 'models'. This is the location of the Dataset.
Always make sure your path is on the copied repository folder.


Next, you need to wget the datasets. Make sure you are in the 'data' folder. Using the link below:
```
https://drive.google.com/file/d/1dtQZcwJ0MrHzgXgYt7L8up_1kBSciaSy/view?usp=sharing
```
Download the dataset files and extract the zip file in the 'data' folder.

For Training, on Terminal, cd to the folder path and type this line:
```
$ python train.py --model-dir=models/project --epochs=(insert your epoch value) --batch-size=(insert your batch size of your choice) --workers=1 --lr=0.001 --arch=resnet18 data/dataset
```
Higher number of epoch may increase the accuracy. However, it will consume a lot of time. Make sure the number epoch is reasonable.

For converting .pth file into .onnx file, on Terminal,
```
$ python onnx_export.py --model-dir=models/project
```

Lastly, to test the project. On Terminal,
```
$ python imagenet.py --model=models/project/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=data/dataset/asl.txt /dev/video0
```
Make sure you know your device file name in order to open your camera using Jetson Nano. In my case is 'video0'.

Done! Camera window will pop-out and you can try using alphabet sign language on the camera. The translation will be on the upper left of the window.
Have Fun!







