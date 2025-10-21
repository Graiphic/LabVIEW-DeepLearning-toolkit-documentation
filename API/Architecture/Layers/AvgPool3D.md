# AvgPool3D

> 🔹 *Layer Documentation – Deep Learning Toolkit for LabVIEW*

---

## Description

Setup and add the average pooling 3D layer into the model during the definition graph step.  
Type : *polymorphic.*

<p align="center">
  <img src="./AveragePooling/average_pooling_3d_add_to_graph.png" alt="AvgPool3D Layer VI" width="400"/>
</p>

---

## Input parameters

| **Parameters** | **Interface** |
|----------------|----------------|
| **![OBJ](./Type/input_object.png) Model in :** *model architecture.* <br> **![FCT](./Type/cluster.png) Parameters :** layer parameters. <br><br> **![I32](./Type/array-integer-32.png) size :** *integer array*, factors by which to downscale (dim1, dim2, dim3). (2,2,2) will halve the size of the 3D input in each dimension.<br>Default value “[2,2,2]”. <br><br> **![I32](./Type/array-integer-32.png) stride :** *integer array*, strides values.<br>Default value “[0,0,0]”. <br><br> **![I32](./Type/array-integer-32.png) explicit padding :** *array*, specifies the number of pixels to pad at the beginning and end of each spatial axis. Batch and channel axes are not padded. Only used when padding = EXPLICIT.<br>Default value “empty”. <br><br> **![ENUM](./Type/enum.png) padding :** *enum*, type of padding to apply.<br>Default value “VALID”. <br><br> **![ENUM](./Type/enum.png) data format :** *enum*, one of *channels_last* or *channels_first* (default). The ordering of the dimensions in the inputs. *channels_last* corresponds to inputs with shape *(batch, height, width, channels)* while *channels_first* corresponds to inputs with shape *(batch, channels, height, width)*.<br>Default value “channels_first”. <br><br> **![TF](./Type/booleen.png) training? :** *boolean*, whether the layer is in training mode (can store data for backward).<br>Default value “True”. <br><br> **![DBL](./Type/double.png) lda coeff :** *float*, defines the coefficient by which the loss derivative will be multiplied before being sent to the previous layer (since during the backward run we go backwards).<br>Default value “1”. <br><br> **![ABC](./Type/string.png) name (optional) :** *string*, name of the layer. | <img src="./_params/pooling_3d_param.png" alt="Pooling3D Parameters" width="200"/> |

---

## Output parameters

**![OBJ](./Type/output_model.png) Model out :** model architecture.

---

## Dimension

### Input shape

5D tensor with shape :

- If *data_format = 'channels_last'* : (batch_size, spatial_dim1, spatial_dim2, spatial_dim3, channels).  
- If *data_format = 'channels_first'* : (batch_size, channels, spatial_dim1, spatial_dim2, spatial_dim3).

### Output shape

5D tensor with shape :

- If *data_format = 'channels_last'* : (batch_size, pooled_dim1, pooled_dim2, pooled_dim3, channels).  
- If *data_format = 'channels_first'* : (batch_size, channels, pooled_dim1, pooled_dim2, pooled_dim3).

---

## Example

All these examples are snippets PNG, you can drop these Snippet onto the block diagram and get the depicted code added to your VI (Do not forget to install Deep Learning library to run it).

---

### AvgPool3D layer

<p align="center">
  <img src="./AveragePooling/1-avgpool3d-layer.png" alt="AvgPool3D Layer Example"/>
</p>

1 – Generate a set of data  

We generate an array of data of type single and shape [batch_size = 10, channels = 7, spatial_dim1 = 5, spatial_dim2 = 5, spatial_dim3 = 3].

2 – Define graph  

First, we define the first layer of the graph which is an Input layer (explicit input layer method).  
This layer is setup as an input array shaped [channels = 7, spatial_dim1 = 5, spatial_dim2 = 5, spatial_dim3 = 3].  
Then we add to the graph the AvgPool3D layer.

3 – Run graph  

We call the forward method and retrieve the result with the “Prediction 5D” method.  
This method returns two variables, the first one is the layer information (cluster composed of the layer name, the graph index and the shape of the output layer) and the second one is the prediction with a shape of [batch_size, channels, spatial_dim1, spatial_dim2, spatial_dim3].

---

### AvgPool3D layer, batch and dimension

<p align="center">
  <img src="./AveragePooling/2-avgpool3d-batch-and-dimension.png" alt="AvgPool3D Layer Batch Example"/>
</p>

1 – Generate a set of data  

We generate an array of data of type single and shape [number of batch = 9, batch_size = 10, channels = 7, spatial_dim1 = 5, spatial_dim2 = 5, spatial_dim3 = 3].

2 – Define graph  

First, we define the first layer of the graph which is an Input layer (explicit input layer method).  
This layer is setup as an input array shaped [channels = 7, spatial_dim1 = 5, spatial_dim2 = 5, spatial_dim3 = 3].  
Then we add to the graph the AvgPool3D layer.

3 – Run graph  

We call the forward method and retrieve the result with the “Prediction 5D” method.  
This method returns two variables, the first one is the layer information (cluster composed of the layer name, the graph index and the shape of the output layer) and the second one is the prediction with a shape of [batch_size, channels, spatial_dim1, spatial_dim2, spatial_dim3].

---

<p align="center">
  <a href="../Layers.md" style="text-decoration:none; font-weight:bold;">⬅️ Back to Layers</a>
</p>
