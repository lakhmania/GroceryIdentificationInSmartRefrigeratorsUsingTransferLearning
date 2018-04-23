"# GroceryIdentificationInSmartRefrigeratorsUsingTransferLearning" 

# Installation Instruction

## Tensorflow object detection API depends upon the following library:

-  Protobuf 3.4.0
-  Python
-  Pillow 1.0
-  lxml
-  tf Slim (which is included in the "tensorflow/models/research/")
-  Jupyter notebook
-  Matplotlib
-  Tensorflow
-  Cython

First clone or download the github of tensorflow,

*git clone https://github.com/tensorflow/models.git*

Next, run the command

```
#### For CPU
pip install tensorflow
#### For GPU
pip install tensorflow-gpu

```
in your terminal window. If you have tensorflow already installed, upgrade it to the latest version. For upgarding tensorflow version, run the command

```
pip install tensorflow --upgrade

```

in your terminal window. Now install all the dependent libraries by running

```
pip install Cython

pip install jupyter

pip install matplotlib

```
## For Protobuf Compilation 
Download the protobuf 4.0 executable from [here](https://github.com/google/protobuf/releases)
Unzip the file and copy protoc.exe from /protoc/bin folder and copy it to models/research folder
Navigate to /models/research folder on the terminal widow and execute
```
protoc object_detection/protos/*.proto --python_out=.

```
Set the environment variable **PYTHONPATH** and set the value as the path to the research folder and also the path till slim folder (which is inside models/research/slim folder inside tensorflow github)

## Testing the installation 
we can test that we have correctly installed the Tensorflow Object Detection API by running the following command:
```
python object_detection/builders/model_builder_test.py

```

## Dataset
Dataset used is [Fruit-360] (https://www.kaggle.com/moltean/fruits) for image classifications and scrapped images from internet for object detection

## Setting up Object Detection API

### Picking Model Parameters
There are a large number of model parameters to configure. The best settings will depend on your given application. Faster R-CNN models are better suited to cases where high accuracy is desired and latency is of lower priority. Conversely, if processing time is the most important factor, SSD models are recommended. In our case we have used RFCN model.

### Defining Inputs
The Tensorflow Object Detection API accepts inputs in the TFRecord file format. Users must specify the locations of both the training and evaluation files. Additionally, users should also specify a label map, which define the mapping between a class id and class name. The label map should be identical between training and evaluation datasets.

An example input configuration looks as follows:

```
tf_record_input_reader {
  input_path: "/usr/home/username/data/train.record"
}
label_map_path: "/usr/home/username/data/label_map.pbtxt"

```
Users should substitute the input_path and label_map_path arguments and insert the input configuration into the train_input_reader and eval_input_reader fields in the skeleton configuration.

