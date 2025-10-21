# Bidirectional

> 🔹 *Layer Documentation – Deep Learning Toolkit for LabVIEW*

---

## Description

Setup and add the bidirectional layer into the model during the definition graph step.  
Type : *polymorphic.*

<p align="center">
  <img src="./Bidirectional/bidirectional_add_to_graph.png" alt="Bidirectional Layer VI" width="400"/>
</p>

---

## Input parameters

| **Parameters** | **Interface** |
|----------------|----------------|
| **![OBJ](./Type/input_object.png) Model in :** *model architecture.* <br> **![FCT](./Type/cluster.png) Parameters :** layer parameters. <br><br> **![OBJ](./Type/input_object.png) layer :** *rnn layer instance (RNN, GRU, LSTM, SimpleRNN).* <br><br> **![ENUM](./Type/enum.png) merge mode :** *enum*, mode by which outputs of the forward and backward RNNs will be combined.<br>Default value “concat”. <br><br> **![OBJ](./Type/input_object.png) backward layer :** *rnn layer instance (RNN, GRU, LSTM, SimpleRNN).* <br><br> **![TF](./Type/booleen.png) training? :** *boolean*, whether the layer is in training mode (can store data for backward).<br>Default value “True”. <br><br> **![TF](./Type/booleen.png) store? :** *boolean*, whether the layer stores the last iteration gradient (accessible via the “get_gradients” function).<br>Default value “False”. <br><br> **![TF](./Type/booleen.png) update? :** *boolean*, whether the layer’s variables should be updated during backward. Equivalent to freeze the layer.<br>Default value “True”. <br><br> **![DBL](./Type/double.png) lda coeff :** *float*, defines the coefficient by which the loss derivative will be multiplied before being sent to the previous layer (since during the backward run we go backwards).<br>Default value “1”. <br><br> **![ABC](./Type/string.png) name (optional) :** *string*, name of the layer. | <img src="./_params/param_bidirectional.png" alt="Bidirectional Parameters" width="200"/> |

---

## Output parameters

**![OBJ](./Type/output_model.png) Model out :** model architecture.

---

## Dimension

### Input shape

3D tensor with shape [batch_size, timesteps, features].

### Output shape

If `return_sequences = True` && `merge_mode = concat` : 3D tensor with shape [batch_size, timesteps, 2*units].  
If `return_sequences = True` && `merge_mode ≠ concat` : 3D tensor with shape [batch_size, timesteps, units].  
If `return_sequences = False` && `merge_mode = concat` : 2D tensor with shape [batch_size, 2*units].  
If `return_sequences = False` && `merge_mode ≠ concat` : 2D tensor with shape [batch_size, units].

---

## Example

All these examples are snippets PNG, you can drop these Snippet onto the block diagram and get the depicted code added to your VI (Do not forget to install Deep Learning library to run it).

---

### Bidirectional layer

<p align="center">
  <img src="./Bidirectional/1-bidi-layer.png" alt="Bidirectional layer example"/>
</p>

1 – Generate a set of data  

We generate an array of data of type single and shape [batch_size = 10, timesteps = 7, features = 5].

2 – Define graph  

First, we define the first layer of the graph which is an Input layer (explicit input layer method).  
This layer is setup as an input array shaped [timesteps = 7, features = 5].  
Then we add to the graph the Bidirectional layer.

3 – Run graph  

We call the forward method and retrieve the result with the “Prediction 2D” method.  
This method returns two variables, the first one is the layer information (cluster composed of the layer name, the graph index and the shape of the output layer) and the second one is the prediction with a shape of [batch_size, 2*units].  
The output dimension depends on the parameters `return_sequences` and `merge_mode`, refer to the chapter “Dimension” of this documentation.

---

### Bidirectional layer, batch and dimension

<p align="center">
  <img src="./Bidirectional/2-bidi-batch-and-dimension.png" alt="Bidirectional layer batch and dimension"/>
</p>

1 – Generate a set of data  

We generate an array of data of type single and shape [number of batch = 9, batch_size = 10, timesteps = 7, features = 5].

2 – Define graph  

First, we define the first layer of the graph which is an Input layer (explicit input layer method).  
This layer is setup as an input array shaped [timesteps = 7, features = 5].  
Then we add to the graph the Bidirectional layer.

3 – Run graph  

We call the forward method and retrieve the result with the “Prediction 2D” method.  
This method returns two variables, the first one is the layer information (cluster composed of the layer name, the graph index and the shape of the output layer) and the second one is the prediction with a shape of [batch_size, 2*units].  
The output dimension depends on the parameters `return_sequences` and `merge_mode`, refer to the chapter “Dimension” of this documentation.

---

<p align="center">
  <a href="../Layers.md" style="text-decoration:none; font-weight:bold;">⬅️ Back to Layers</a>
</p>
