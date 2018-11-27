# Object-detection

https://github.com/tensorflow/models/tree/master/research/object_detection

# Training Custom Objects
https://tensorflow-object-detection-api-tutorial.readthedocs.io/en/latest/training.html

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
# Add Libraries to PYTHONPATH
```
# From tensorflow/models/research/
export PYTHONPATH=$PYTHONPATH:`pwd`:`pwd`/slim
```
