# Convolution 2D

> 🔹 *Layer Documentation – Deep Learning Toolkit for LabVIEW*

---

## Description

Setup and add the convolution 2D layer into the model during the definition graph step.  
Type : *polymorphic.*

<p align="center">
  <img src="./Convolution/conv_2d_add_to_graph.png" alt="Convolution 2D Layer VI" width="400"/>
</p>

---

## Input parameters

| **Parameters** | **Interface** |
|----------------|----------------|
| **![OBJ](./Type/input_object.png) Model in :** *model architecture.* <br> **![FCT](./Type/cluster.png) Parameters :** layer parameters. <br><br> **![I32](./Type/integer-32.png) filters :** *integer*, the dimensionality of the output space.<br>Default value “3”. <br><br> **![I32](./Type/array-integer-32.png) size :** *array integer*, specify the height and width of the 2D convolution window. Can be a single integer to specify the same value for all spatial dimensions.<br>Default value “[3,3]”. *Never more 2 values.* <br><br> **![I32](./Type/array-integer-32.png) stride :** *array integer*, specify the strides of the convolution along the height and width. Can be a single integer to specify the same value for all spatial dimensions.<br>Default value “[1,1]”. *Never more 2 values.* <br><br> **![I32](./Type/integer-32.png) dilation rate :** *integer*, specifying the dilation rate to use for dilated convolution.<br>Default value “[1,1]”. *Never more 2 values.* <br><br> **![I32](./Type/array-integer-32.png) explicit padding :** *array*, specifies the number of pixels to pad at the beginning and end of each spatial axis. Batch and channel axes are not padded. Only used when padding = EXPLICIT.<br>Default value “empty”. <br><br> **![FCT](./Type/cluster.png) Activation :** *cluster*, activation function to use.<br>Default value “Linear”. <br><br> **![TF](./Type/booleen.png) use bias? :** *boolean*, whether the layer uses a bias vector.<br>Default value “True”. <br><br> **![ENUM](./Type/enum.png) padding :** *enum*, type of padding to apply.<br>Default value “VALID”. <br><br> **![ENUM](./Type/enum.png) data format :** *enum*, one of *channels_last* or *channels_first* (default). The ordering of the dimensions in the inputs.<br> *channels_last* corresponds to inputs with shape *(batch, steps, features)* while *channels_first* corresponds to *(batch, features, steps)*.<br>Default value “channels_first”. <br><br> **![FCT](./Type/cluster.png) Filter Initializer :** *cluster*, initializer for the convolution kernel. <br> **![FCT](./Type/cluster.png) Bias Initializer :** *cluster*, initializer for the bias vector. <br> **![FCT](./Type/cluster.png) Filter Regularizer :** *cluster*, optional regularizer for the convolution kernel. <br> **![FCT](./Type/cluster.png) Bias Regularizer :** *cluster*, optional regularizer for the bias vector. <br><br> **![TF](./Type/booleen.png) training? :** *boolean*, whether the layer is in training mode (can store data for backward).<br>Default value “True”. <br><br> **![TF](./Type/booleen.png) store? :** *boolean*, whether the layer stores the last iteration gradient (accessible via the “get_gradients” function).<br>Default value “False”. <br><br> **![TF](./Type/booleen.png) update? :** *boolean*, whether the layer’s variables should be updated during backward. Equivalent to freeze the layer.<br>Default value “True”. <br><br> **![DBL](./Type/double.png) lda coeff :** *float*, defines the coefficient by which the loss derivative will be multiplied before being sent to the previous layer (since during the backward run we go backwards).<br>Default value “1”. <br><br> **![ABC](./Type/string.png) name (optional) :** *string*, name of the layer. | <img src="./_params/pooling_2d_param.png" alt="2D Convolution Parameters" width="220"/> |

---

## Output parameters

**![OBJ](./Type/output_model.png) Model out :** model architecture.

---

## Dimension

### Input shape

4-Dimension tensor with shape : [batch_size, channel, row, column] *(default “channel_first” parameters).*  
In case of “channel_last” setup, forward function will input shape [batch_size, row, column, channel].

### Output shape

Same as input 4-Dimension tensor with shape : [batch_size, channel, row, column] *(default “channel_first” parameters).*  
In case of “channel_last” setup, forward function will input shape [batch_size, row, column, channel].

---

## Example

All these examples are snippets PNG, you can drop these Snippet onto the block diagram and get the depicted code added to your VI (Do not forget to install Deep Learning library to run it).

---

### Convolution 2D layer

<p align="center">
  <img src="./Convolution/1-conv2d-layer.png" alt="Convolution 2D Layer Example"/>
</p>

1 – Generate a set of data  

We generate an array of data of type single and shape [batch_size = 10, channel = 5, row = 128, column = 128] *(channel first is default layer configuration).*  
In case of channel last layer configuration, shape is [batch_size, row, column, channel].

2 – Define graph  

First, we define the first layer of the graph which is an Input layer (explicit input layer method).  
This layer is setup as an input array shaped [channel = 5, row = 128, column = 128].  
Then we add to the graph the Conv2D layer.

3 – Run graph  

We call the forward method and retrieve the result with the “Prediction 4D” method.  
This method returns two variables, the first one is the layer information (cluster composed of the layer name, the graph index and the shape of the output layer) and the second one is the prediction with a shape of [batch_size, filter, new_row, new_column].

---

### Convolution 2D layer, batch and dimension

<p align="center">
  <img src="./Convolution/2-conv2d-batch-and-dimension.png" alt="Convolution 2D Layer Batch and Dimension Example"/>
</p>

1 – Generate a set of data  

We generate an array of data of type single and shape [number of batch = 9, batch_size = 10, channel = 5, row = 128, column = 128] *(channel first default layer configuration).*  
In case of channel last layer configuration, shape is [batch_size, row, column, channel].

2 – Define graph  

First, we define the first layer of the graph which is an Input layer (explicit input layer method).  
This layer is setup as an input array shaped [channel = 5, row = 128, column = 128].  
Then we add to the graph the Conv2D layer.

3 – Run graph  

We call the forward method and retrieve the result with the “Prediction 4D” method.  
This method returns two variables, the first one is the layer information (cluster composed of the layer name, the graph index and the shape of the output layer) and the second one is the prediction with a shape of [batch_size, filter, new_row, new_column].

---

<p align="center">
  <a href="../Layers.md" style="text-decoration:none; font-weight:bold;">⬅️ Back to Layers</a>
</p>
