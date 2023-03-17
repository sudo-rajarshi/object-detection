# Object Detection

## Create Dataset
![yolo.png](img\dataset.png)
* Create a dataset (i.e. a folder) inside `data`.
* Create `images` and `labels` folders inside `dataset`.
* Create `train` and `val` folders inside both `images` and `labels`
* Keep `80%` of images inside `dataset/images/train` and `20%` of images inside `dataset/images/val`.
* Keep `80%` of labels inside `dataset/labels/train` and `20%` of labels inside `dataset/labels/val`.
* Create a `.yaml` file inside `YOLOvX/version/data` and update the required fields (follow `traffic.yaml` for reference).

<br>

## Train

### YOLOv5

    python YOLOvX\yolov5\train.py --epochs --batch --data --name

* `--epochs` = Number of iterations you want to train model for.
* `--batch` = Number of image you want to train at one cycle.
* `--data` = Path of `.yaml` file where dataset information is stored
* `--name` = Name of the folder where you want to store the results.

*For example,  `python .\YOLOvX\yolov5\train.py --epochs 5000 --batch 16 --data .\YOLOvX\yolov5\data\traffic.yaml --name traffic`*

This will create a folder named `traffic` inside `YOLOvX\yolov5\runs\train` where all the model training characteristics along with the trained model weights will be stored.

Once the training is completed, you can see the path of the weights (.pt) in the terminal as well.

<br>

## Inference

    python .\YOLOvX\yolov5\detect.py --weights --data --source

* `--weights` = Path of the trained model weights inside `YOLOxX\yolov5\runs\train`
* `--data` = Path of `.yaml` file where dataset information is stored
* `--source` = Path of the image on which you want to perform inference.

*For example, `python .\YOLOvX\yolov5\detect.py --weights YOLOvX\yolov5\runs\train\traffic\weights\best.pt --data YOLOvX\yolov5\data\traffic.yaml --source data\traffic\images\val --name traffic`*

This will create a folder named `traffic` inside `YOLOvX\yolov5\runs\detect` where all the model predictions will be stored.

Once inference is completed, you can see the path where the predictions are stored in the terminal as well.


