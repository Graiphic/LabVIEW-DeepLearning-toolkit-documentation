# AvgPool1D

> 🔹 *Layer Documentation – Deep Learning Toolkit for LabVIEW*

---

## Description

Setup and add the average pooling 1D layer into the model during the definition graph step.  
Type : *polymorphic.*

<p align="center">
  <img src="./AveragePooling/average_pooling_1d_add_to_graph.png" alt="AvgPool1D Layer VI" width="400"/>
</p>

---

## Input parameters

| **Parameters** | **Interface** |
|----------------|----------------|
| **![OBJ](./Type/input_object.png) Model in :** *model architecture.* <br> **![FCT](./Type/cluster.png) Parameters :** layer parameters. <br><br> **![I32](./Type/integer-32.png) size :** *integer*, size of the average pooling windows.<br>Default value “2”. <br><br> **![I32](./Type/integer-32.png) stride :** *integer*, factor by which to downscale.<br>Default value “0”. <br><br> **![I32](./Type/array-integer-32.png) explicit padding :** *array*, specifies the number of pixels to pad at the beginning and end of each spatial axis. Batch and channel axes are not padded. Only used when padding = EXPLICIT.<br>Default value “empty”. <br><br> **![ENUM](./Type/enum.png) padding :** *enum*, type of padding to apply.<br>Default value “VALID”. <br><br> **![ENUM](./Type/enum.png) data format :** *enum*, one of *channels_last* or *channels_first* (default). The ordering of the dimensions in the inputs.  
`channels_last` corresponds to inputs with shape *(batch, steps, features)*,  
`channels_first` corresponds to inputs with shape *(batch, features, steps).*  
Default value “channels_first”. <br><br> **![TF](./Type/booleen.png) training? :** *boolean*, whether the layer is in training mode (can store data for backward).<br>Default value “True”. <br><br> **![DBL](./Type/double.png) lda coeff :** *float*, defines the coefficient by which the loss derivative will be multiplied before being sent to the previous layer (since during the backward run we go backwards).<br>Default value “1”. <br><br> **![ABC](./Type/string.png) name (optional) :** *string*, name of the layer. | <img src="./_params/pooling_1d_param.png" alt="AvgPool1D Parameters" width="200"/> |

---

## Output parameters

**![OBJ](./Type/output_model.png) Model out :** model architecture.

---

## Dimension

### Input shape

3D tensor with shape:
- If `data_format = 'channels_last'` : *(batch_size, steps, features)*  
- If `data_format = 'channels_first'` : *(batch_size, features, steps)*

### Output shape

3D tensor with shape:
- If `data_format = 'channels_last'` : *(batch_size, downsampled_steps, features)*  
- If `data_format = 'channels_first'` : *(batch_size, features, downsampled_steps)*

---

## Example

All these examples are snippets PNG; you can drop these Snippet onto the block diagram and get the depicted code added to your VI  
(Do not forget to install Deep Learning library to run it).

---

### AvgPool1D layer

<p align="center">
  <img src="./AveragePooling/1-avgpool1d-layer.png" alt="AvgPool1D Example 1"/>
</p>

1 – Generate a set of data  

We generate an array of data of type single and shape [batch_size = 10, features = 7, steps = 5].

2 – Define graph  

First, we define the first layer of the graph which is an Input layer (explicit input layer method).  
This layer is setup as an input array shaped [features = 7, steps = 5].  
Then we add to the graph the AvgPool1D layer.

3 – Run graph  

We call the forward method and retrieve the result with the “Prediction 3D” method.  
This method returns two variables, the first one is the layer information (cluster composed of the layer name, the graph index and the shape of the output layer) and the second one is the prediction with a shape of [batch_size, features, steps].

---

### AvgPool1D layer, batch and dimension

<p align="center">
  <img src="./AveragePooling/2-avgpool1d-batch-and-dimension.png" alt="AvgPool1D Example 2"/>
</p>

1 – Generate a set of data  

We generate an array of data of type single and shape [number of batch = 9, batch_size = 10, features = 7, steps = 5].

2 – Define graph  

First, we define the first layer of the graph which is an Input layer (explicit input layer method).  
This layer is setup as an input array shaped [features = 7, steps = 5].  
Then we add to the graph the AvgPool1D layer.

3 – Run graph  

We call the forward method and retrieve the result with the “Prediction 3D” method.  
This method returns two variables, the first one is the layer information (cluster composed of the layer name, the graph index and the shape of the output layer) and the second one is the prediction with a shape of [batch_size, features, steps].

---

<p align="center">
  <a href="../Layers.md" style="text-decoration:none; font-weight:bold;">⬅️ Back to Layers</a>
</p>
