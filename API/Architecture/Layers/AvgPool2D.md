# AvgPool2D

> 🔹 *Layer Documentation – Deep Learning Toolkit for LabVIEW*

---

## Description

Setup and add the average pooling 2D layer into the model during the definition graph step.  
Type : *polymorphic.*

<p align="center">
  <img src="./AveragePooling/average_pooling_2d_add_to_graph.png" alt="AvgPool2D Layer VI" width="400"/>
</p>

---

## Input parameters

| **Parameters** | **Interface** |
|----------------|----------------|
| **![OBJ](./Type/input_object.png) Model in :** *array*, model architecture. <br> **![FCT](./Type/cluster.png) Parameters :** layer parameters. <br><br> **![I32](./Type/array-integer-32.png) size :** *array*, factors by which to downscale (vertical, horizontal). (2, 2) will halve the input in both spatial dimensions. If only one integer is specified, the same window length will be used for both dimensions.<br>Default value “[2,2]”. <br><br> **![I32](./Type/array-integer-32.png) stride :** *array*, strides values.<br>Default value “[0,0]”. <br><br> **![I32](./Type/array-integer-32.png) explicit padding :** *array*, specifies the number of pixels to pad at the beginning and end of each spatial axis. Batch and channel axes are not padded. Only used when padding = EXPLICIT.<br>Default value “empty”. <br><br> **![ENUM](./Type/enum.png) padding :** *enum*, type of padding to apply.<br>Default value “VALID”. <br><br> **![ENUM](./Type/enum.png) data format :** *enum*, one of *channels_last* or *channels_first (default)*. The ordering of the dimensions in the inputs. *channels_last* corresponds to inputs with shape *(batch, height, width, channels)* while *channels_first* corresponds to inputs with shape *(batch, channels, height, width)*.<br>Default value “channels_first”. <br><br> **![TF](./Type/booleen.png) training? :** *boolean*, whether the layer is in training mode (can store data for backward).<br>Default value “True”. <br><br> **![DBL](./Type/double.png) lda coeff :** *float*, defines the coefficient by which the loss derivative will be multiplied before being sent to the previous layer (since during the backward run we go backwards).<br>Default value “1”. <br><br> **![ABC](./Type/string.png) name (optional) :** *string*, name of the layer. | <img src="./_params/pooling_2d_param.png" alt="Pooling 2D Parameters" width="200"/> |

---

## Output parameters

**![OBJ](./Type/output_model.png) Model out :** model architecture.

---

## Dimension

### Input shape
4D tensor with shape :
- If *data_format = channels_last* : (batch_size, rows, cols, channels)  
- If *data_format = channels_first* : (batch_size, channels, rows, cols)

### Output shape
4D tensor with shape :
- If *data_format = channels_last* : (batch_size, pooled_rows, pooled_cols, channels)  
- If *data_format = channels_first* : (batch_size, channels, pooled_rows, pooled_cols)

---

## Example

All these examples are snippets PNG, you can drop these Snippet onto the block diagram and get the depicted code added to your VI (Do not forget to install Deep Learning library to run it).

---

### AvgPool2D layer

<p align="center">
  <img src="./AveragePooling/1-avgpool2d-layer.png" alt="AvgPool2D Layer Example"/>
</p>

1 – Generate a set of data  

We generate an array of data of type single and shape [batch_size = 10, channels = 7, rows = 5, cols = 3].

2 – Define graph  

First, we define the first layer of the graph which is an Input layer (explicit input layer method).  
This layer is setup as an input array shaped [channels = 7, rows = 5, cols = 3].  
Then we add to the graph the AvgPool2D layer.

3 – Run graph  

We call the forward method and retrieve the result with the “Prediction 4D” method.  
This method returns two variables, the first one is the layer information (cluster composed of the layer name, the graph index and the shape of the output layer) and the second one is the prediction with a shape of [batch_size, channels, rows, cols].

---

### AvgPool2D layer, batch and dimension

<p align="center">
  <img src="./AveragePooling/2-avgpool2d-batch-and-dimension.png" alt="AvgPool2D Batch Example"/>
</p>

1 – Generate a set of data  

We generate an array of data of type single and shape [number of batch = 9, batch_size = 10, channels = 7, rows = 5, cols = 3].

2 – Define graph  

First, we define the first layer of the graph which is an Input layer (explicit input layer method).  
This layer is setup as an input array shaped [channels = 7, rows = 5, cols = 3].  
Then we add to the graph the AvgPool2D layer.

3 – Run graph  

We call the forward method and retrieve the result with the “Prediction 4D” method.  
This method returns two variables, the first one is the layer information (cluster composed of the layer name, the graph index and the shape of the output layer) and the second one is the prediction with a shape of [batch_size, channels, rows, cols].

---

<p align="center">
  <a href="../Layers.md" style="text-decoration:none; font-weight:bold;">⬅️ Back to Layers</a>
</p>
