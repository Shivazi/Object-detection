# Object-detection

https://github.com/tensorflow/models/tree/master/research/object_detection

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
