# Dense Layer

> 🔹 *Layer Documentation – Deep Learning Toolkit for LabVIEW*

---

## Description

Setup and add the dense layer into the model during the definition graph step.  
Type : *polymorphic.*

<p align="center">
  <img src="./Dense/dense_add_to_graph.png" alt="Dense Layer VI" width="400"/>
</p>

---

## Input parameters

| **Parameters** | **Interface** |
|----------------|----------------|
| **![OBJ](./Type/input_object.png) Model in :** *model architecture.* <br> **![FCT](./Type/cluster.png) Parameters :** layer parameters. <br><br> **![I32](./Type/integer-32.png) units :** *integer*, dimensionality of the output space. <br><br> **![FCT](./Type/cluster.png) Activation :** *cluster*, activation function to use. <br><br> **![TF](./Type/booleen.png) use bias? :** *boolean*, whether the layer uses a bias vector.<br>Default value “True”. <br><br> **![FCT](./Type/cluster.png) Weight Initializer :** *cluster*, initializer for the kernel weights matrix. <br><br> **![FCT](./Type/cluster.png) Bias Initializer :** *cluster*, initializer for the bias vector. <br><br> **![FCT](./Type/cluster.png) Weight Regularizer :** *cluster*, regularizer function applied to the kernel weights matrix. <br><br> **![FCT](./Type/cluster.png) Bias Regularizer :** *cluster*, regularizer function applied to the bias vector. <br><br> **![TF](./Type/booleen.png) training? :** *boolean*, whether the layer is in training mode (can store data for backward).<br>Default value “True”. <br><br> **![TF](./Type/booleen.png) store? :** *boolean*, whether the layer stores the last iteration gradient (accessible via the “get_gradients” function).<br>Default value “False”. <br><br> **![TF](./Type/booleen.png) update? :** *boolean*, whether the layer’s variables should be updated during backward. Equivalent to freeze the layer.<br>Default value “True”. <br><br> **![DBL](./Type/double.png) lda coeff :** *float*, defines the coefficient by which the loss derivative will be multiplied before being sent to the previous layer (since during the backward run we go backwards).<br>Default value “1”. <br><br> **![ABC](./Type/string.png) name (optional) :** *string*, name of the layer. | <img src="./_params/dense_param.png" alt="Dense Parameters" width="230"/> |

---

## Output parameters

**![OBJ](./Type/output_model.png) Model out :** model architecture.

---

## Dimension

### Input shape

N-Dimension tensor with shape: [batch size, input_dim1, …, input_dimN].  
The most common situation would be a 2D input with shape [batch size, input_dim].  
(input_dim 1 = Input dimension).

### Output shape

N-Dimension tensor with shape: [batch size, units1, …, unitsN].  
For instance, for a 2D input with shape [batch size, input_dim], the output would have shape [batch size, units].

---

## Example

All these examples are snippets PNG, you can drop these Snippet onto the block diagram and get the depicted code added to your VI (Do not forget to install Deep Learning library to run it).

---

### Dense layer

<p align="center">
  <img src="./Dense/1-dense-layer.png" alt="Dense Layer Example"/>
</p>

1 – Generate a set of data  

We generate an array of data of type single and shape [batch_size = 10, input_dim = 5].

2 – Define graph  

First, we define the first layer of the graph which is an Input layer (explicit input layer method).  
This layer is setup as an input array shaped [input_dim = 5].  
Then we add to the graph the Dense layer.

3 – Run graph  

We call the forward method and retrieve the result with the “Prediction 2D” method.  
This method returns two variables, the first one is the layer information (cluster composed of the layer name, the graph index and the shape of the output layer) and the second one is the prediction with a shape of [batch_size, units].

---

### Dense layer, batch and dimension

<p align="center">
  <img src="./Dense/2-dense-batch-and-dimension.png" alt="Dense Batch and Dimension Example"/>
</p>

1 – Generate a set of data  

We generate an array of data of type single and shape [number of batch = 9, batch_size = 10, input_dim = 5].

2 – Define graph  

First, we define the first layer of the graph which is an Input layer (explicit input layer method).  
This layer is setup as an input array shaped [input_dim = 5].  
Then we add to the graph the Dense layer.

3 – Run graph  

We call the forward method and retrieve the result with the “Prediction 2D” method.  
This method returns two variables, the first one is the layer information (cluster composed of the layer name, the graph index and the shape of the output layer) and the second one is the prediction with a shape of [batch_size, units].

---

### (Expert) Academic train model with dense layers (2D)

<p align="center">
  <img src="./Dense/3-model-academique-training.png" alt="Dense Academic Train Model"/>
</p>

---

### (Expert) Train model with dense layers (2D)

<p align="center">
  <img src="./Dense/3-model-training.png" alt="Dense Train Model"/>
</p>

---

<p align="center">
  <a href="../Layers.md" style="text-decoration:none; font-weight:bold;">⬅️ Back to Layers</a>
</p>
