# EEG Detection using deep Learning Models application to Epilepsy seizures

# Data Base Description
The data used in this project called Epileptic seizure data extracted copy from the original CHB-
MIT, this data consists of 5 different folders, each one has 100 files and each file representing a
single subject/person.
The files are recording brain activity for 23.6 seconds. The corresponding time series is
sampled into 4097 data points, Each data point represents the value of the EEG recording at a
different point in a specific time.
The number of individuals is 500 with each one has 4097 data points for 23.5 seconds.
The process that applied is :
Each 4097 data points is divided and shuffled into 23 chunks, and each chunk contains 178 data
points for 1 second, and each data point refers to the value of the EEG recording at a different
point in time.

## Experiments and proposed approach
## VGG 16

-  2 x convolution layer of 64 channel of 3x3 kernal and same padding + relu activation. 
-  1 x maxpool layer of 2x2 pool size and stride 2x2.
-  2 x convolution layer of 128 channel of 3x3 kernal and same padding + relu activation.
-  1 x maxpool layer of 2x2 pool size and stride 2x2. 
-  3 x convolution layer of 256 channel of 3x3 kernal and same padding + relu activation.
-  1 x maxpool layer of 2x2 pool size and stride 2x2.
-  3 x convolution layer of 512 channel of 3x3 kernal and same padding + relu activation.
-  1 x maxpool layer of 2x2 pool size and stride 2x2.
-  3 x convolution layer of 512 channel of 3x3 kernal and same padding + relu activation.
-  1 x maxpool layer of 2x2 pool size and stride 2x2.
  
  <img width="625" alt="accu_loss_v16_c2" src="https://user-images.githubusercontent.com/87647184/182105590-a5f6cc5b-0f7a-4087-a0f4-3366b451f7a7.PNG">



## VGG 19

In order to classify epileptic seizure and achieved our aim, we started by import the data and prepare it, then fed it into our model. The  following steps explain how we organized the layer which make up this model.

1. The first two layers are convolutional layers of 64 channel and 3*3 kernel size with same padding.
2. After this, pooling layer was used with max-pool of 2*2 size and stride 2 which reduces the dimension of EEG signal.
3. This is followed by 2 more convolution layers of 128 channel.
4. Then a pooling layer is used with max-pool of 2*2 size and stride 2.
5. Four more convolution layers are added with depth of  256  and the same padding.
6. Then a pooling layer is used with max-pool of 2*2 size and stride 2.
7. Four more convolution layers are added with 512 channel and the same padding.
8. This is followed by a pooling layer with max-pool of 2*2 size and stride 2.
9. Again,Four more convolution layers are added with 512 channels and the same padding.
10. The previous layer is followed by a pooling layer with max-pool of 2*2 size and stride 2.

Each Convolution layer has Relu as an activation function for the purpose of stop forwarding
negative values through the network.
After the final pooling layer the output obtained is flattened into Fully Connected (FC) layer with
4096 channels and softmax output of 2 classes so we added:
- 1 x Dense layer of 4096 units + RELU activation.
- 1 x Dense layer of 4096 units + RELU activation.
- 1 x Dense Softmax layer of 2 units.
<img width="580" alt="vgg192classes_accuracy_loss" src="https://user-images.githubusercontent.com/87647184/182106130-4aff0391-1215-43dd-85e0-fe468acfbeab.png">


