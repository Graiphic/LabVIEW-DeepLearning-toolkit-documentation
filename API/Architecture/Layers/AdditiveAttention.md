# AdditiveAttention

> 🔹 *Layer Documentation – Deep Learning Toolkit for LabVIEW*

---

## Description

Setup and add the additive attention layer into the model during the definition graph step.  
Type : *polymorphic.*

<p align="center">
  <img src="./AdditiveAttention/additive_attention_add_to_graph.png" alt="AdditiveAttention Layer VI" width="400"/>
</p>

---

## Input parameters

| **Parameters** | **Interface** |
|----------------|----------------|
| **![OBJ](./Type/input_object.png) Models in :** *array*, model architecture. Must be query, value, key (key is optional). <br> **![FCT](./Type/cluster.png) Parameters :** layer parameters. <br><br> **![TF](./Type/booleen.png) use scale :** *boolean*, if True, will create a variable to scale the attention scores.<br>Default value “True”. <br><br> **![TF](./Type/booleen.png) training? :** *boolean*, whether the layer is in training mode (can store data for backward).<br>Default value “True”. <br><br> **![TF](./Type/booleen.png) store? :** *boolean*, whether the layer stores the last iteration gradient (accessible via the “get_gradients” function).<br>Default value “False”. <br><br> **![TF](./Type/booleen.png) update? :** *boolean*, whether the layer’s variables should be updated during backward. Equivalent to freeze the layer.<br>Default value “True”. <br><br> **![DBL](./Type/double.png) lda coeff :** *float*, defines the coefficient by which the loss derivative will be multiplied before being sent to the previous layer (since during the backward run we go backwards).<br>Default value “1”. <br><br> **![ABC](./Type/string.png) name (optional) :** *string*, name of the layer. | <img src="./_params/param_attention.png" alt="Attention Parameters" width="200"/> |

---

## Output parameters

**![OBJ](./Type/output_model.png) Model out :** model architecture.

---

## Dimension

### Input shape

List of the following tensors:
- **query** : Query *Tensor* of shape [batch_size, Tq, dim].  
- **value** : Value *Tensor* of shape [batch_size, Tv, dim].  
- **key** : Optional key *Tensor* of shape [batch_size, Tv, dim].  
  If not given, will use *value* for both *key* and *value*, which is the most common case.

### Output shape

Attention outputs of shape [batch_size, Tq, dim].

---
## Example

All these examples are snippets PNG, you can drop these Snippet onto the block diagram and get the depicted code added to your VI (Do not forget to install Deep Learning library to run it).

---

### AdditiveAttention layer with two identical input layer shape

<p align="center">
  <img src="./AdditiveAttention/1-additiveattention-with-two-identical-input-layer-shape.png" alt="AdditiveAttention identical input shapes"/>
</p>

1 – Generate a set of data  

We generate two array of data of type single and shape [batch_size = 10, Tq & Tv = 7, dim = 10] (same input shape).

2 – Define graph  

We first define two input layers named “query_input” and “value_input”.  
This layers is setup as an input array shaped [Tq = 7, dim = 10] and [Tv = 7, dim = 10].  
Finally, we construct an array of the two graphs generated at the input of AdditiveAttention.

3 – Summarize graph  

Returns the summary of the model in file text.

4 – Run graph  

We call the forward method and retrieve the result with the “Prediction 3D” method.  
This method returns two variables, the first one is the layer information (cluster composed of the layer name, the graph index and the shape of the output layer) and the second one is the prediction with a shape of [batch_size, Tq, dim].

---

### AdditiveAttention layer with two different input layer shape

<p align="center">
  <img src="./AdditiveAttention/2-additiveattention-with-two-different-input-layer-shape.png" alt="AdditiveAttention different input shapes"/>
</p>

1 – Generate a set of data  

We generate two array of data of type single and shape1 [batch_size = 10, Tq = 4, dim = 10] and shape2 [batch_size = 10, Tv = 7, dim = 10] (different input shape).  
We can only modify the first dimension (Tq or Tv) because the layer won’t accept different dimension between query, value and key.

2 – Define graph  

We first define two input layers named “query_input” and “value_input”.  
This layers is setup as an input array shaped [Tq = 4, dim = 10] and [Tv = 7, dim = 10].  
Finally, we construct an array of the two graphs generated at the input of AdditiveAttention.

3 – Summarize graph  

Returns the summary of the model in file text.

4 – Run graph  

We call the forward method and retrieve the result with the “Prediction 3D” method.  
This method returns two variables, the first one is the layer information (cluster composed of the layer name, the graph index and the shape of the output layer) and the second one is the prediction with a shape of [batch_size, Tq, dim].

---

<p align="center">
  <a href="../Layers.md" style="text-decoration:none; font-weight:bold;">⬅️ Back to Layers</a>
</p>
