# Cropping2D

> 🔹 *Layer Documentation – Deep Learning Toolkit for LabVIEW*

---

## Description

Setup and add the cropping 2D layer into the model during the definition graph step.  
Type : *polymorphic.*

<p align="center">
  <img src="./Cropping/cropping_2d_add_to_graph.png" alt="Cropping2D Layer VI" width="400"/>
</p>

---

## Input parameters

| **Parameters** | **Interface** |
|----------------|----------------|
| **![OBJ](./Type/input_object.png) Model in :** *model architecture.* <br> **![FCT](./Type/cluster.png) Parameters :** layer parameters. <br><br> **![FCT](./Type/cluster.png) Height Crop :** *cluster*, interpreted as two different symmetric cropping values for height and width *(top, bottom)*.<br>Default value “(0,0)”. <br><br> **![FCT](./Type/cluster.png) Width Crop :** *cluster*, how many units should be trimmed off at the beginning and end of the cropping dimension *(left, right)*.<br>Default value “(0,0)”. <br><br> **![enum](./Type/enum.png) data format :** *enum*, one of *channels_last* or *channels_first* (default). The ordering of the dimensions in the inputs.<br>**channels_last** corresponds to inputs with shape *(batch, rows, cols, channels)*, while **channels_first** corresponds to *(batch, channels, rows, cols)*.<br>Default value “channels_first”. <br><br> **![TF](./Type/booleen.png) training? :** *boolean*, whether the layer is in training mode (can store data for backward).<br>Default value “True”. <br><br> **![DBL](./Type/double.png) lda coeff :** *float*, defines the coefficient by which the loss derivative will be multiplied before being sent to the previous layer (since during the backward run we go backwards).<br>Default value “1”. <br><br> **![ABC](./Type/string.png) name (optional) :** *string*, name of the layer. | <img src="./Cropping/cropping_2d_param.png" alt="Cropping2D Parameters" width="200"/> |

---

## Output parameters

**![OBJ](./Type/output_model.png) Model out :** model architecture.

---

## Dimension

### Input shape

4D tensor with shape :  
- If `data_format = 'channels_last'` : *(batch_size, rows, cols, channels)*  
- If `data_format = 'channels_first'` : *(batch_size, channels, rows, cols)*

### Output shape

4D tensor with shape :  
- If `data_format = 'channels_last'` : *(batch_size, cropped_rows, cropped_cols, channels)*  
- If `data_format = 'channels_first'` : *(batch_size, channels, cropped_rows, cropped_cols)*

---

## Example

All these examples are snippets PNG, you can drop these Snippet onto the block diagram and get the depicted code added to your VI (Do not forget to install Deep Learning library to run it).

---

### Cropping2D layer

<p align="center">
  <img src="./Cropping/1-cropping2d-layer.png" alt="Cropping2D Layer Example"/>
</p>

1 – Generate a set of data  

We generate an array of data of type single and shape [batch_size = 10, channels = 7, rows = 5, cols = 3].

2 – Define graph  

First, we define the first layer of the graph which is an Input layer (explicit input layer method).  
This layer is setup as an input array shaped [channels = 7, rows = 5, cols = 3].  
Then we add to the graph the Cropping2D layer.

3 – Run graph  

We call the forward method and retrieve the result with the “Prediction 4D” method.  
This method returns two variables:  
- the first one is the layer information (cluster composed of the layer name, the graph index and the shape of the output layer),  
- the second one is the prediction with a shape of [batch_size, channels, cropped_rows, cropped_cols].

---

### Cropping2D layer, batch and dimension

<p align="center">
  <img src="./Cropping/2-cropping2d-batch-and-dimension-1.png" alt="Cropping2D Batch Example"/>
</p>

1 – Generate a set of data  

We generate an array of data of type single and shape [number of batch = 9, batch_size = 10, channels = 7, rows = 5, cols = 3].

2 – Define graph  

First, we define the first layer of the graph which is an Input layer (explicit input layer method).  
This layer is setup as an input array shaped [channels = 7, rows = 5, cols = 3].  
Then we add to the graph the Cropping2D layer.

3 – Run graph  

We call the forward method and retrieve the result with the “Prediction 4D” method.  
This method returns two variables, the first one is the layer information (cluster composed of the layer name, the graph index and the shape of the output layer) and the second one is the prediction with a shape of [batch_size, channels, cropped_rows, cropped_cols].

---

<p align="center">
  <a href="../Layers.md" style="text-decoration:none; font-weight:bold;">⬅️ Back to Layers</a>
</p>
