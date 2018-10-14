# Selfstudy-Neural-Network
Transfer Learning: Train engine classifying flowers by neural networl. 

```
Tran Tue Nhi
```
This script runs using Python 3.

## Preparation

1. Set up Tensorflow:

``` pip install --upgrade "tensorflow==1.7.*"```

2. Clone repository which stores code:

* ```git clone https://github.com/googlecodelabs/tensorflow-for-poets-2```
* ```cd tensorflow-for-poets-2```

3. Run:

```python scripts/retrain.py --output_graph=tf_files/retrained_graph.pb --output_labels=tf_files/retrained_labels.txt --image_dir=tf_files/flower_photos```

## Training process:
* The default mode is the script will run 4000 steps to train.
* In each step, it selects 10 random pictures from training data file and takes bottleneck file from cache and predicts.
* Each picture predicted will be brought to compare with its label to see the accuracy.

## How to test with new flower:
1. Find a random flower picture.

2. Copy this picture to ```tensorflow-for-poets-2``` folder.

3. Run the command to help engine identify the new image you downloaded: ```python scripts/label_image.py --image image.png```

4. If you encounter the error ```The name import / input refers to an Operation not in the Graph ```, open file ```label_image.py```
and change the code from 
``` 
input_height = 224
input_width = 224
input_mean = 128
input_std = 128
input_layer = "input" 
```
to
``` 
input_height = 299
input_width = 299
input_mean = 0
input_std = 255
input_layer = "Mul" 

```

## Result after testing a new dandelion image:

<img src="https://i.imgur.com/1UkqKjy.png">

Accuracy: 99.874%

## References:
* https://towardsdatascience.com/training-inception-with-tensorflow-on-custom-images-using-cpu-8ecd91595f26
* https://www.tensorflow.org/hub/tutorials/image_retraining 
