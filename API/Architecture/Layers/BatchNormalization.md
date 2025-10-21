# BatchNormalization

> 🔹 *Layer Documentation – Deep Learning Toolkit for LabVIEW*

---

## Description

Setup and add the batch normalization layer into the model during the definition graph step.  
Type : *polymorphic.*

<p align="center">
  <img src="./BatchNormalization/batch_normalization_add_to_graph.png" alt="BatchNormalization Layer VI" width="400"/>
</p>

---

## Input parameters

| **Parameters** | **Interface** |
|----------------|----------------|
| **![OBJ](./Type/input_object.png) Model in :** *model architecture.* <br> **![FCT](./Type/cluster.png) Parameters :** layer parameters. <br><br> **![I32](./Type/integer-32.png) axis :** *integer*, the axis that should be normalized (typically the features axis).<br>Default value “-1”. <br><br> **![SGL](./Type/double.png) momentum :** *float*, momentum for the moving average.<br>Default value “0.99”. <br><br> **![SGL](./Type/double.png) epsilon :** *float*, small float added to variance to avoid dividing by zero.<br>Default value “0.001”. <br><br> **![FCT](./Type/cluster.png) Beta Initializer :** *cluster*, initializer for the beta weight. <br> **![FCT](./Type/cluster.png) Gamma Initializer :** *cluster*, initializer for the gamma weight. <br> **![FCT](./Type/cluster.png) Beta Regularizer :** *cluster*, optional regularizer for the beta weight. <br> **![FCT](./Type/cluster.png) Gamma Regularizer :** *cluster*, optional regularizer for the gamma weight. <br><br> **![TF](./Type/booleen.png) training? :** *boolean*, whether the layer is in training mode (can store data for backward).<br>Default value “True”. <br><br> **![TF](./Type/booleen.png) store? :** *boolean*, whether the layer stores the last iteration gradient (accessible via the “get_gradients” function).<br>Default value “False”. <br><br> **![TF](./Type/booleen.png) update? :** *boolean*, whether the layer’s variables should be updated during backward. Equivalent to freeze the layer.<br>Default value “True”. <br><br> **![DBL](./Type/double.png) lda coeff :** *float*, defines the coefficient by which the loss derivative will be multiplied before being sent to the previous layer (since during the backward run we go backwards).<br>Default value “1”. <br><br> **![ABC](./Type/string.png) name (optional) :** *string*, name of the layer. | <img src="./_params/param_batchnormalization.png" alt="BatchNormalization Parameters" width="220"/> |

---

## Output parameters

**![OBJ](./Type/output_model.png) Model out :** model architecture.

---

## Dimension

### Input shape
Input tensor (of any rank).

### Output shape
Same shape as input.

---

## Example

All these examples are snippets PNG, you can drop these Snippet onto the block diagram and get the depicted code added to your VI (Do not forget to install Deep Learning library to run it).

---

### BatchNormalization layer

<p align="center">
  <img src="./BatchNormalization/1-batchnorm-layer.png" alt="BatchNormalization Example 1" width="800"/>
</p>

1 – Generate a set of data  

We generate an array of data of type single and shape [batch_size = 10, input_dim = 5].

2 – Define graph  

First, we define the first layer of the graph which is an Input layer (explicit input layer method).  
This layer is setup as an input array shaped [input_dim = 5].  
Then we add to the graph the BatchNormalization layer.

3 – Run graph  

We call the forward method and retrieve the result with the “Prediction 2D” method.  
This method returns two variables, the first one is the layer information (cluster composed of the layer name, the graph index and the shape of the output layer) and the second one is the prediction with a shape of [batch_size, input_dim].

---

### BatchNormalization layer, batch and dimension

<p align="center">
  <img src="./BatchNormalization/2-batchnorm-batch-and-dimension.png" alt="BatchNormalization Example 2" width="800"/>
</p>

1 – Generate a set of data  

We generate an array of data of type single and shape [number of batch = 9, batch_size = 10, input_dim = 5].

2 – Define graph  

First, we define the first layer of the graph which is an Input layer (explicit input layer method).  
This layer is setup as an input array shaped [input_dim = 5].  
Then we add to the graph the BatchNormalization layer.

3 – Run graph  

We call the forward method and retrieve the result with the “Prediction 2D” method.  
This method returns two variables, the first one is the layer information (cluster composed of the layer name, the graph index and the shape of the output layer) and the second one is the prediction with a shape of [number of batch, batch_size, input_dim].

---

<p align="center">
  <a href="../Layers.md" style="text-decoration:none; font-weight:bold;">⬅️ Back to Layers</a>
</p>
