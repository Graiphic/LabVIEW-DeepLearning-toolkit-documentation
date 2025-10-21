# Convolution 3D

> 🔹 *Layer Documentation – Deep Learning Toolkit for LabVIEW*

---

## Description

Setup and add the convolution 3D layer into the model during the definition graph step.  
Type : *polymorphic.*

<p align="center">
  <img src="./Convolution/conv_3d_add_to_graph.png" alt="Convolution 3D Layer VI" width="400"/>
</p>

---

## Input parameters

| **Parameters** | **Interface** |
|----------------|----------------|
| **![OBJ](./Type/input_object.png) Model in :** *model architecture.* <br> **![FCT](./Type/cluster.png) Parameters :** layer parameters. <br><br> **![I32](./Type/integer-32.png) filters :** *integer*, the dimensionality of the output space.<br>Default value “3”. <br><br> **![I32](./Type/array-integer-32.png) size :** *array integer*, specify the depth, height and width of the 3D convolution window. Can be a single integer to specify the same value for all spatial dimensions.<br>Default value “[3, 3, 3]”. *Never more 3 values.* <br><br> **![I32](./Type/array-integer-32.png) stride :** *array integer*, specify the strides of the convolution along the depth, height and width. Can be a single integer to specify the same value for all spatial dimensions.<br>Default value “[1, 1, 1]”. *Never more 3 values.* <br><br> **![I32](./Type/integer-32.png) dilation rate :** *integer*, specifying the dilation rate to use for dilated convolution.<br>Default value “[1, 1, 1]”. *Never more 3 values.* <br><br> **![I32](./Type/array-integer-32.png) explicit padding :** *array*, specifies the number of pixels to pad at the beginning and end of each spatial axis. Batch and channel axes are not padded. Only used when padding = EXPLICIT.<br>Default value “empty”. <br><br> **![FCT](./Type/cluster.png) Activation :** *cluster*, activation function to use. <br><br> **![TF](./Type/booleen.png) use bias? :** *boolean*, whether the layer uses a bias vector.<br>Default value “True”. <br><br> **![ENUM](./Type/enum.png) padding :** *enum*, type of padding to apply.<br>Default value “VALID”. <br><br> **![ENUM](./Type/enum.png) data format :** *enum*, one of *channels_last* or *channels_first* (default). The ordering of the dimensions in the inputs. *channels_last* corresponds to inputs with shape (batch, steps, features) while *channels_first* corresponds to inputs with shape (batch, features, steps).*<br>Default value “channels_first”. <br><br> **![FCT](./Type/cluster.png) Filter Initializer :** *cluster*, initializer for the convolution kernel. <br> **![FCT](./Type/cluster.png) Bias Initializer :** *cluster*, initializer for the bias vector. <br> **![FCT](./Type/cluster.png) Filter Regularizer :** *cluster*, optional regularizer for the convolution kernel. <br> **![FCT](./Type/cluster.png) Bias Regularizer :** *cluster*, optional regularizer for the bias vector. <br><br> **![TF](./Type/booleen.png) training? :** *boolean*, whether the layer is in training mode (can store data for backward).<br>Default value “True”. <br><br> **![TF](./Type/booleen.png) store? :** *boolean*, whether the layer stores the last iteration gradient (accessible via the “get_gradients” function).<br>Default value “False”. <br><br> **![TF](./Type/booleen.png) update? :** *boolean*, whether the layer’s variables should be updated during backward. Equivalent to freeze the layer.<br>Default value “True”. <br><br> **![DBL](./Type/double.png) lda coeff :** *float*, defines the coefficient by which the loss derivative will be multiplied before being sent to the previous layer (since during the backward run we go backwards).<br>Default value “1”. <br><br> **![ABC](./Type/string.png) name (optional) :** *string*, name of the layer. | <img src="./Convolution/conv_3d_param.png" alt="Convolution 3D Parameters" width="220"/> |

---

## Output parameters

**![OBJ](./Type/output_model.png) Model out :** model architecture.

---

## Dimension

### Input shape

5-Dimension tensor with shape :  
`[batch_size, channel, conv_dim1, conv_dim2, conv_dim3]` (default “channel_first” parameters).  

In case of *channel_last* setup, forward function will input shape :  
`[batch_size, conv_dim1, conv_dim2, conv_dim3, channel]`.

### Output shape

Same shape as input 5-Dimension tensor :  
`[batch_size, channel, conv_dim1, conv_dim2, conv_dim3]` (default “channel_first”).  

In case of *channel_last* setup, forward function will output shape :  
`[batch_size, conv_dim1, conv_dim2, conv_dim3, channel]`.

---

## Example

All these examples are snippets PNG. You can drop these Snippets onto the LabVIEW block diagram and get the depicted code added to your VI.  
*(Do not forget to install Deep Learning library to run it).*

---

### Convolution 3D layer example

<p align="center">
  <img src="./Convolution/1-conv3d-layer.png" alt="Convolution 3D layer"/>
</p>

1 – Generate a set of data  

We generate an array of data of type single and shape `[batch_size = 10, channel = 5, conv_dim1 = 64, conv_dim2 = 64, conv_dim3 = 3]` (channel-first default configuration).  
In case of channel-last configuration, shape is `[batch_size, conv_dim1, conv_dim2, conv_dim3, channel]`.

2 – Define graph  

First, we define the first layer of the graph which is an Input layer (explicit input method).  
This layer is setup as an input array shaped `[channel = 5, conv_dim1 = 64, conv_dim2 = 64, conv_dim3 = 3]`.  
Then we add to the graph the Conv3D layer.

3 – Run graph  

We call the forward method and retrieve the result with the “Prediction 5D” method.  
This method returns two variables:  
- The first is the layer information (cluster composed of the layer name, the graph index and the shape of the output layer).  
- The second is the prediction with a shape of `[batch_size, filter, new_conv_dim1, new_conv_dim2, new_conv_dim3]`.

---

### Convolution 3D layer – batch and dimension

<p align="center">
  <img src="./Convolution/2-conv3d-batch-and-dimension.png" alt="Convolution 3D layer batch and dimension"/>
</p>

1 – Generate a set of data  

We generate an array of data of type single and shape `[number of batch = 9, batch_size = 10, channel = 5, conv_dim1 = 64, conv_dim2 = 64, conv_dim3 = 3]` (channel-first configuration).  
In case of channel-last setup, shape is `[batch_size, conv_dim1, conv_dim2, conv_dim3, channel]`.

2 – Define graph  

First, we define the first layer of the graph which is an Input layer (explicit method).  
This layer is setup as an input array shaped `[channel = 5, conv_dim1 = 64, conv_dim2 = 64, conv_dim3 = 3]`.  
Then we add to the graph the Conv3D layer.

3 – Run graph  

We call the forward method and retrieve the result with the “Prediction 5D” method.  
This method returns two variables:  
- The first is the layer information (cluster composed of the layer name, graph index and output shape).  
- The second is the prediction with shape `[batch_size, filter, new_conv_dim1, new_conv_dim2, new_conv_dim3]`.

---

<p align="center">
  <a href="../Layers.md" style="text-decoration:none; font-weight:bold;">⬅️ Back to Layers</a>
</p>
