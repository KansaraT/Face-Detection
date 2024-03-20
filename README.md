# Face-Detection

**Download the Dataset**
* If you plan to execute the training commands on terminal, you can download the dataset by executing the following command.
```
!pip install roboflow

from roboflow import Roboflow
rf = Roboflow(api_key="4vKWas6B0A0k6NFigsbU")
project = rf.workspace("facial-emotion-recognition-qgrl7").project("fre-qvgk1")
version = project.version(1)
dataset = version.download("yolov8")
```

**Setting Up YOLOv8 to Train on Custom Dataset**
* Install the ultralytics package using pip.
```
!pip install ultralytics
```

* Go inside the directory.
```
cd /content/datasets/FRE-1
```

**Commands for Training YOLOv8 on Custom Dataset**
```
!yolo task=detect mode=train model=yolov8n.pt imgsz=640 data=data.yaml epochs=80 batch=8 name=yolov8n_custom
```

* We can also evaluate the best model using the following command.
```
!yolo task=detect mode=val model=runs/detect/yolov8n_custom/weights/best.pt name=yolov8n_eval data=data.yaml imgsz=1280
```

* Run inference on a video using the trained YOLOv8 Nano model.
```
!yolo task=detect mode=predict model=runs/detect/yolov8n_custom/weights/best.pt name=yolov8n_eval data=data.yaml imgsz=1280 source=/content/sample.mp4 show=True imgsz=1280 name=yolov8n_v8_50e_infer1280 hide_labels=True
```


https://github.com/KansaraT/Face-Detection/assets/91043060/ed13d302-0b52-47a7-b889-0725a1be6738




