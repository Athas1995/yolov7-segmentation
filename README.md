# yolov7-instance-segmentation

## Features
- How to run Code on Windows
- How to run Code on Linux
- How to train on Custom Data

## Coming Soon
- Development of streamlit dashboard for Instance-Segmentation with Object Tracking

## Requirements
- GPU (Needed for installation of detectron2)
- Git for Windows <a href="https://git-scm.com/download/win">Download Link</a>  
- Git on Linux (Install git on linux by using command in terminal. ```sudo apt-get install git```)

## Steps to run Code

### Linux Users
- Open the terminal and run mentioned command below to download & install anaconda for linux operating system
```
wget https://repo.anaconda.com/archive/Anaconda3-2022.05-Linux-x86_64.sh

#(you will need to accept license terms from terminal, then you installation will continue)
bash Anaconda3-2022.05-Linux-x86_64.sh
```
- Once Anaconda Installed, restart your machine.

- Open the terminal in <B>home folder</B>, and run the mentioned command below.
```
cd ~
sudo chmod 777 .conda
```
- Clone the repository.
```
git clone https://github.com/RizwanMunawar/yolov7-instance-segmentation
```
- Goto the cloned folder.
```
cd yolov7-instance-segmentation
```
- Create envirnoment
```
conda env create -f envirnoment.yml
```
- Activate the envirnoment
```
conda activate detectron2
```
- Install extra modules
```
pip install -r requirements.txt
```
- Download weights
```
wget https://github.com/WongKinYiu/yolov7/releases/download/v0.1/yolov7-mask.pt
```
- Run Code with mentioned command.
```
#Basic Usage
python instance-segmentation.py

#For LiveStream(Ip Stream URL Format i.e "rtsp://username:pass@ipaddress:portno/video/video.amp")
python instance-segmentation.py --source "your IP Camera Stream URL"

#For WebCam
python instance-segmentation.py --source 0

#For External Camera
python instance-segmentation.py --source 1
```
- Output file will be created in the working directory with name ("your-file-name-without-extension"+"_segmentation.mp4")

### Window Users
- Download the <a href="https://repo.anaconda.com/archive/Anaconda3-2022.05-Windows-x86_64.exe">64-Bit</a> or <a href="https://repo.anaconda.com/archive/Anaconda3-2022.05-Windows-x86.exe">32-Bit</a> Anaconda <B>(Based on your system specifications)</B>.
- Install the executable
- Goto Start Menu and search for "Anaconda Prompt". Double Click to Open it.
- Change the path of anaconda prompt with mentioned command below.
```
cd "C:\Users\"yourusername"\Desktop
```
- Clone the repository.
```
git clone https://github.com/RizwanMunawar/yolov7-instance-segmentation
```
- Goto the cloned folder.
```
cd yolov7-instance-segmentation
```
- Create envirnoment
```
conda env create -f environment.yml
```
- Activate the envirnoment
```
conda activate detectron2
```
- Install extra modules
```
pip install -r requirements.txt
```
- Download weights from <a href="https://github.com/WongKinYiu/yolov7/releases/download/v0.1/yolov7-mask.pt">link</a> and move them to the cloned folder.
- Run Code with mentioned command.
```
#Basic Usage
python instance-segmentation.py

#For LiveStream (Ip Stream URL Format i.e "rtsp://username:pass@ipaddress:portno/video/video.amp")
python instance-segmentation.py --source "your IP Camera Stream URL"

#For WebCam
python instance-segmentation.py --source 0

#For External Camera
python instance-segmentation.py --source 1
```
- Output file will be created in the working directory with name ("your-file-name-without-extension"+"_segmentation.mp4")

### RESULTS
<table>
  <tr>
    <td>Football Match Image Segmentation</td>
     <td>Cricket Match Image Segmentation</td>
    <td>FPS and Time Comparision Graph</td>
     </tr>
  <tr>
    <td><img src="https://user-images.githubusercontent.com/62513924/185704342-59cb9bce-6be1-432b-90fc-2064feed4a67.png" width=640 height=180></td>
    <td><img src="https://user-images.githubusercontent.com/62513924/185706834-19ee1c9f-de91-439d-bba3-6b05c00be226.png" width=640 height=180></td>
    <td><img src="https://user-images.githubusercontent.com/62513924/185712079-e8ffcdfb-8d3b-467a-9620-d6186976370c.png" width=640 height=180></td>
  </tr>
  </tr>
 </table>
 

## Training
- Make sure to follow above mentioned steps before you will start training on custom dataset.
- Make a folder name inside <b>yolov7-instance-segmentation</b> with name <b>dataset</b>.
- Move your (segmentation custom labelled data) inside that folder with mentioned structure.

└── dataset

    └── train

        └── images (folder including all training images)
    
        └── labels (folder including all training labels)
  
    └── test
   
        └── images (folder including all testing images)
    
        └── labels (folder including all testing labels)

- Go to the <b>data</b> folder and create a file with name <b>custom.yaml</b> and paste the mentioned code below inside that.

```
train: "path to train folder"
val: "path to validation folder"

# number of classes
nc: 2

# class names
names: [ 'person','Bike']
```

- Go to the terminal, and run mentioned command below. (Make sure to activate first conda envirnoment "detectron2")
```
python train.py --weights yolov7-mask.pt --cfg cfg/yolov7-mask.yaml --batch-size 4 --img 256 --hyp data/hyp.scratch.mask.yaml --data data/custom.yaml 
```

## Testing
```
python test.py --data data/custom.yaml --img 256 --conf 0.25 --iou 0.65 --weights yolov7-mask.pt
```

## References
- https://github.com/WongKinYiu/yolov7
- https://github.com/ultralytics/yolov5

## My Medium Articles
- https://medium.com/augmented-startups/yolov7-training-on-custom-data-b86d23e6623
- https://medium.com/augmented-startups/roadmap-for-computer-vision-engineer-45167b94518c
- https://medium.com/augmented-startups/yolor-or-yolov5-which-one-is-better-2f844d35e1a1
- https://medium.com/augmented-startups/train-yolor-on-custom-data-f129391bd3d6
- https://medium.com/augmented-startups/develop-an-analytics-dashboard-using-streamlit-e6282fa5e0f
