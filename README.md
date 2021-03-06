# Object-detection

https://github.com/tensorflow/models/tree/master/research/object_detection
# Data download
http://www.image-net.org/challenges/LSVRC/2012/nonpub-downloads
# Step 1 setup for object detection
# Pyhton 3
```
git clone https://github.com/tensorflow/models.git
pip3 install tensorflow-gpu
pip3 install --user Cython
pip3 install --user contextlib2
pip3 install --user pillow
pip3 install --user lxml
pip3 install --user jupyter
pip3 install --user matplotlib
```
# COCO API installation
```
git clone https://github.com/cocodataset/cocoapi.git
cd cocoapi/PythonAPI
make
cp -r pycocotools /home/nybsys/project/object_detection/models/research/
```
# Protobuf Compilation
```
# From tensorflow/models/research/
protoc object_detection/protos/*.proto --python_out=.
```
# Protobuf manualy
```
# From tensorflow/models/research/
wget -O protobuf.zip https://github.com/google/protobuf/releases/download/v3.0.0/protoc-3.0.0-linux-x86_64.zip
unzip protobuf.zip

# From tensorflow/models/research/
./bin/protoc object_detection/protos/*.proto --python_out=.
```
# Add Libraries to PYTHONPATH
```
# From tensorflow/models/research/
export PYTHONPATH=$PYTHONPATH:`pwd`:`pwd`/slim
```

# Opencv installl
```
pip3 install tqdm
pip3 install opencv-contrib-python

```
# Step 2 Custom Object train
# Training Custom Objects
https://tensorflow-object-detection-api-tutorial.readthedocs.io/en/latest/training.html
# Project directory map
```
TensorFlow
├─ addons
│ └─ labelImg
├─ models
│ ├─ official
│ ├─ research
│ ├─ samples
│ └─ tutorials
├─ scripts
│ └─ preprocessing
|    ├─ xml_to_csv.py
|    └─ generate_tfrecord.py
└─ workspace
   └─ training_demo
      ├─ annotations
      ├─ images
      │ ├─ test
      │ └─ train
      ├─ pre-trained-model
      ├─ training
      └─ README.md

```
# Adding necessary Environment Variables

object_detection folder add to python environment
```
nano .bashrc
export PYTHONPATH=$PYTHONPATH:/home/nybsys/project/object_detection/models/research
export PYTHONPATH=$PYTHONPATH:/home/nybsys/project/object_detection/models/research/slim
```
# sub-step 1 
Image collection

# sub-step 2 image labeling

# Object labeling
https://github.com/tzutalin/labelImg

```
git clone https://github.com/tzutalin/labelImg.git
```

# Python 2 + Qt4
```
sudo apt-get install pyqt4-dev-tools
sudo pip install lxml
make qt4py2
python labelImg.py
python labelImg.py [IMAGE_PATH] [PRE-DEFINED CLASS FILE]
```
# Python 3 + Qt5
```
sudo apt-get install pyqt5-dev-tools
cd labelImg/
sudo pip3 install -r requirements/requirements-linux-python3.txt
make qt5py3
python3 labelImg.py
python3 labelImg.py [IMAGE_PATH] [PRE-DEFINED CLASS FILE]
```
collect image and label image and 20% past in test derectory and 80% train derectory

# Convert xml to csv
```
pip3 install pandas
python3 xml_to_csv.py -i /home/nybsys/project/object_detection/workspace/training_demo/images/test -o /home/nybsys/project/object_detection/workspace/training_demo/annotations/test_labels.csv
  
python3 xml_to_csv.py -i /home/nybsys/project/object_detection/workspace/training_demo/images/train -o /home/nybsys/project/object_detection/workspace/training_demo/annotations/train_labels.csv

```
# Creating TFRecords
``` 
 python3 generate_tfrecord.py --label=riksha --csv_input=/home/nybsys/project/object_detection/workspace/training_demo/annotations/train_labels.csv --output_path=/home/nybsys/project/object_detection/workspace/training_demo/annotations/train.record --img_path=/home/nybsys/project/object_detection/workspace/training_demo/images/train
 
 python3 generate_tfrecord.py --label=riksha --csv_input=/home/nybsys/project/object_detection/workspace/training_demo/annotations/test_labels.csv --output_path=/home/nybsys/project/object_detection/workspace/training_demo/annotations/test.record --img_path=/home/nybsys/project/object_detection/workspace/training_demo/images/test
```
# Training model
```
python3 train.py --logtostderr --train_dir=training/ --pipeline_config_path=training/faster_rcnn_inception_v2_coco.config
```
