# Strawberry Flowers Detector II
[First Phase](https://github.com/wrightchin/strawberry-flowers): (Completed on 10-11-2021)
- Implement a detection model for detecting the location of strawberry flowes in 2 dimensions.

Second Phase: (Completed on 01-05-2022)
- Implement a classifier for classifying a flower is ready for pollination or not.

Third Phase A: (In-Progress)
-Implement a grow stage tracker for tracking a flower and export to the database.

Third Phase B: (Pending)
- Implement a Depth Evaluator for determine the location of strawberry flower in 3 dimensions.   


### Working Environemnt: 
- Cuda: 10.1
- Cudnn: 7
- OpenCV: 3.4.8
- Cmake: 3.16.3
- Python: 3.7 

### Training data: 
- Data collected from Hong Kong Vegetable Marketing Organization ([VMO](https://www.vmo.org/?fbclid=IwAR3Lgiecqcd8clfMTHnLKpwK5ZoIVQzH9yuNOMiBeq5FTi4YQY41U2u-67s)) 

### Usage:
Docker build,
```
docker build -t flower-detection-train2 .
```
Docker run,
```
docker run -it --gpus all -v $PWD:/app/ flower-detection-train2 /bin/bash
```

Start the training,
```
./darknet detector train ./Flower_detection/cfg/flower.data ./Flower_detection/cfg/yolov4-tiny-obj.cfg ./Flower_detection/cfg/yolov4-tiny.conv.29 -map
```

Calcualte the mAP
```
./darknet detector map ./Flower_detection/cfg/flower.data ./Flower_detection/cfg/yolov4-tiny-obj.cfg ./Flower_detection/cfg/weights/[weights]
```

Validate the training,
```
./darknet detector test ./Flower_detection/cfg/flower.data ./Flower_detection/cfg/yolov4-tiny-obj.cfg ./Flower_detection/cfg/weights/yolov4-tiny-obj_3000.weights ./Flower_detection/test01.jpg
```

### Results:
![map results](results/chart_yolov4-tiny-obj.png)

![Alt text](results/test01.jpg)

[More photos ~](results)

### Acknowledgements & Collaborations:
- Hong Kong Vegetable Marketing Organization ([VMO](https://www.vmo.org/?fbclid=IwAR3Lgiecqcd8clfMTHnLKpwK5ZoIVQzH9yuNOMiBeq5FTi4YQY41U2u-67s)) 
- The University of Hong Kong | Department of Electrical and Eletronic Engineering ([HKUEEE](https://www.eee.hku.hk/))
