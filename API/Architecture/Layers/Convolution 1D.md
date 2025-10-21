# Convolution 1D

> 🔹 *Layer Documentation – Deep Learning Toolkit for LabVIEW*

---

## Description

Setup and add the convolution 1D layer into the model during the definition graph step.  
Type : *polymorphic.*

<p align="center">
  <img src="./Convolution/conv_1d_add_to_graph.png" alt="Convolution 1D Layer VI" width="400"/>
</p>

---

## Input parameters

| **Parameters** | **Interface** |
|----------------|----------------|
| **![OBJ](./Type/input_object.png) Model in :** *model architecture.* <br> **![FCT](./Type/cluster.png) Parameters :** layer parameters. <br><br> **![I32](./Type/integer-32.png) filters :** *integer*, the dimensionality of the output space.<br>Default value “3”. <br><br> **![I32](./Type/integer-32.png) size :** *integer*, specify the length of the 1D convolution window.<br>Default value “3”. <br><br> **![I32](./Type/integer-32.png) stride :** *integer*, specify the stride length of the convolution.<br>Default value “1”. <br><br> **![I32](./Type/integer-32.png) dilation rate :** *integer*, specifying the dilation rate to use for dilated convolution.<br>Default value “1”. <br><br> **![I32](./Type/array-integer-32.png) explicit padding :** *array*, number of pixels to pad at the beginning and end of each spatial axis. Batch and channel axes are not padded. Only used when padding = EXPLICIT.<br>Default value “empty”. <br><br> **![FCT](./Type/cluster.png) Activation :** activation function to use. <br> **![TF](./Type/booleen.png) use bias? :** *boolean*, whether the layer uses a bias vector.<br>Default value “True”. <br><br> **![ENUM](./Type/enum.png) padding :** *enum*, type of padding to apply.<br>Default value “VALID”. <br><br> **![ENUM](./Type/enum.png) data format :** *enum*, one of *channels_last* or *channels_first* (default). The ordering of the dimensions in the inputs. <br> • *channels_last* → shape (batch, steps, features) <br> • *channels_first* → shape (batch, features, steps). <br>Default value “channels_first”. <br><br> **![FCT](./Type/cluster.png) Filter Initializer :** initializer for the convolution kernel. <br> **![FCT](./Type/cluster.png) Bias Initializer :** initializer for the bias vector. <br> **![FCT](./Type/cluster.png) Filter Regularizer :** optional regularizer for the convolution kernel. <br> **![FCT](./Type/cluster.png) Bias Regularizer :** optional regularizer for the bias vector. <br><br> **![TF](./Type/booleen.png) training? :** *boolean*, whether the layer is in training mode (can store data for backward).<br>Default value “True”. <br> **![TF](./Type/booleen.png) store? :** *boolean*, whether the layer stores the last iteration gradient (accessible via get_gradients).<br>Default value “False”. <br> **![TF](./Type/booleen.png) update? :** *boolean*, whether the layer’s variables should be updated during backward (equivalent to freeze the layer).<br>Default value “True”. <br><br> **![DBL](./Type/double.png) lda coeff :** *float*, coefficient by which the loss derivative is multiplied before being sent backward.<br>Default value “1”. <br><br> **![ABC](./Type/string.png) name (optional) :** *string*, name of the layer. | <img src="./_params/conv_1d_param.png" alt="Convolution 1D Parameters" width="220"/> |

---

## Output parameters

**![OBJ](./Type/output_model.png) Model out :** model architecture.

---

## Dimension

### Input shape
3-Dimensional tensor with shape : [batch_size, channel, width] (default “channel_first” parameters).  
In case of “channel_last” setup, forward function will input shape [batch_size, width, channel].

### Output shape
Same as input 3-Dimensional tensor with shape : [batch_size, channel, width] (default “channel_first” parameters).  
In case of “channel_last” setup, forward function will input shape [batch_size, width, channel].

---

## Example

All these examples are snippets PNG; you can drop these Snippet onto the block diagram and get the depicted code added to your VI (Do not forget to install the Deep Learning library to run it).

---

### Convolution 1D layer

<p align="center">
  <img src="./Convolution/1-conv1d-layer.png" alt="Conv1D Example 1"/>
</p>

1 – Generate a set of data  

We generate an array of data of type single and shape [batch_size = 10, channel = 5, width = 128] (channel-first default configuration).  
In case of channel-last configuration, shape is [batch_size, width, channel].

2 – Define graph  

First, we define the first layer of the graph which is an Input layer (explicit input layer method).  
This layer is setup as an input array shaped [channel = 5, width = 128].  
Then we add to the graph the Conv1D layer.

3 – Run graph  

We call the forward method and retrieve the result with the “Prediction 3D” method.  
This method returns two variables :  
• the layer information (cluster with the layer name, graph index, and output shape)  
• the prediction with shape [batch_size, filter, new_width].

---

### Convolution 1D layer, batch and dimension

<p align="center">
  <img src="./Convolution/2-conv1d-batch-and-dimension.png" alt="Conv1D Example 2"/>
</p>

1 – Generate a set of data  

We generate an array of data of type single and shape [number of batch = 9, batch_size = 10, channel = 5, width = 128] (channel-first default configuration).  
In case of channel-last configuration, shape is [batch_size, width, channel].

2 – Define graph  

First, we define the first layer of the graph which is an Input layer (explicit input layer method).  
This layer is setup as an input array shaped [channel = 5, width = 128].  
Then we add to the graph the Conv1D layer.

3 – Run graph  

We call the forward method and retrieve the result with the “Prediction 3D” method.  
This method returns two variables :  
• the layer information (cluster with the layer name, graph index, and output shape)  
• the prediction with shape [batch_size, filter, new_width].

---

<p align="center">
  <a href="../Layers.md" style="text-decoration:none; font-weight:bold;">⬅️ Back to Layers</a>
</p>
