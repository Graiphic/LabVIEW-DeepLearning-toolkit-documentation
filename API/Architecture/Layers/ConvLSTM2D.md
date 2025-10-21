# ConvLSTM2D

> 🔹 *Layer Documentation – Deep Learning Toolkit for LabVIEW*

---

## Description

Setup and add the convolution LSTM 2D layer into the model during the definition graph step.  
Type : *polymorphic.*

<p align="center">
  <img src="./Convolution/conv_lstm_2d_add_to_graph.png" alt="ConvLSTM2D Layer VI" width="400"/>
</p>

---

## Input parameters

| **Parameters** | **Interface** |
|----------------|----------------|
| **![OBJ](./Type/input_object.png) Model in :** *model architecture.* <br> **![FCT](./Type/cluster.png) Parameters :** layer parameters. <br><br> **![I32](./Type/integer-32.png) filters :** *integer*, the dimensionality of the output space.<br>Default value “1”. <br><br> **![I32](./Type/array-integer-32.png) size :** *array*, specify the dimensions of the convolution window.<br>Default value “[3,3]”. <br><br> **![I32](./Type/array-integer-32.png) stride :** *array*, specify the strides of the convolution.<br>Default value “[1,1]”. <br><br> **![I32](./Type/array-integer-32.png) explicit padding :** *array*, specifies the number of pixels to pad at the beginning and end of each spatial axis. Only used when padding = *EXPLICIT.*<br>Default value “empty”. <br><br> **![ENUM](./Type/enum.png) padding :** *enum*, type of padding to apply.<br>Default value “VALID”. <br><br> **![FCT](./Type/cluster.png) Activation :** *cluster*, applied to the candidate cell input.<br>Transforms new information considered for updating the cell state. <br><br> **![FCT](./Type/cluster.png) Recurrent Activation :** *cluster*, applied to input, forget, and output gates.<br>Controls which parts of past information are allowed to pass or be blocked. <br><br> **![FCT](./Type/cluster.png) Output Activation :** *cluster*, applied to the updated cell state before producing the visible hidden output. <br><br> **![TF](./Type/booleen.png) use bias? :** *boolean*, whether the layer uses a bias vector.<br>Default value “True”. <br><br> **![FCT](./Type/cluster.png) Kernel Initializer :** *cluster*, initializer for the *kernel* weights matrix.<br>Used for linear transformation of the inputs. <br><br> **![FCT](./Type/cluster.png) Recurrent Initializer :** *cluster*, initializer for the *recurrent_kernel* weights matrix.<br>Used for linear transformation of the recurrent state. <br><br> **![FCT](./Type/cluster.png) Bias Initializer :** *cluster*, initializer for the bias vector. <br><br> **![TF](./Type/booleen.png) unit forget bias? :** *boolean*, if True, add 1 to the bias of the forget gate at initialization.<br>Use in combination with Bias Initializer = ‘Zeros’.<br>Default value “True”. <br><br> **![DBL](./Type/double.png) dropout :** *float*, fraction of the units to drop for the linear transformation of the inputs (0–1). <br><br> **![DBL](./Type/double.png) recurrent dropout :** *float*, fraction of the units to drop for the linear transformation of the recurrent state (0–1). <br><br> **![TF](./Type/booleen.png) return sequences? :** *boolean*, whether to return the last output or the full sequence.<br>Default value “False”. <br><br> **![TF](./Type/booleen.png) stateful? :** *boolean*, if True, the last state for each sample will be used as initial state for the next batch.<br>Default value “False”. <br><br> **![FCT](./Type/cluster.png) Kernel Regularizer :** *cluster*, regularization function applied to *kernel* weights. <br><br> **![FCT](./Type/cluster.png) Recurrent Regularizer :** *cluster*, regularization function applied to *recurrent_kernel* weights. <br><br> **![FCT](./Type/cluster.png) Bias Regularizer :** *cluster*, regularization function applied to the bias vector. <br><br> **![TF](./Type/booleen.png) training? :** *boolean*, whether the layer is in training mode (can store data for backward).<br>Default value “True”. <br><br> **![TF](./Type/booleen.png) store? :** *boolean*, whether the layer stores the last iteration gradient (accessible via “get_gradients”).<br>Default value “False”. <br><br> **![TF](./Type/booleen.png) update? :** *boolean*, whether the layer’s variables should be updated during backward (freeze layer if False).<br>Default value “True”. <br><br> **![DBL](./Type/double.png) lda coeff :** *float*, defines the coefficient by which the loss derivative will be multiplied before being sent to the previous layer.<br>Default value “1”. <br><br> **![ABC](./Type/string.png) name (optional) :** *string*, name of the layer. | <img src="./_params/pooling_2d_param.png" alt="ConvLSTM2D Parameters" width="230"/> |

---

## Output parameters

**![OBJ](./Type/output_model.png) Model out :** model architecture.

---

## Dimension

### Input shape

5D tensor with shape:
- If `data_format = 'channels_last'` : (samples, time, rows, cols, channels)  
- If `data_format = 'channels_first'` : (samples, time, channels, rows, cols)

### Output shape

- If `return_sequences = True` :  
  - `channels_last` → 5D tensor with shape (samples, timesteps, new_rows, new_cols, filters)  
  - `channels_first` → 5D tensor with shape (samples, timesteps, filters, new_rows, new_cols)

- If `return_sequences = False` :  
  - `channels_last` → 4D tensor with shape (samples, new_rows, new_cols, filters)  
  - `channels_first` → 4D tensor with shape (samples, filters, new_rows, new_cols)

---

## Example

All these examples are snippets PNG, you can drop these Snippet onto the block diagram and get the depicted code added to your VI (Do not forget to install Deep Learning library to run it).

---

### ConvLSTM2D layer

<p align="center">
  <img src="./Convolution/1-convlstm2d-layer.png" alt="ConvLSTM2D layer example"/>
</p>

1 – Generate a set of data  
We generate an array of data of type single and shape [samples = 10, time = 7, channels = 6, rows = 5, cols = 5].

2 – Define graph  
First, we define the first layer of the graph which is an Input layer (explicit input layer method).  
This layer is setup as an input array shaped [time = 7, channels = 6, rows = 5, cols = 5].  
Then we add to the graph the ConvLSTM2D layer.

3 – Run graph  
We call the forward method and retrieve the result with the “Prediction 4D” method.  
This method returns two variables:
- the layer information (name, graph index, and shape of the output layer)
- the prediction with shape [samples, filters, new_rows, new_cols].  

The output dimension depends on the parameter `return_sequences`; see the “Dimension” chapter.

---

### ConvLSTM2D layer, batch and dimension

<p align="center">
  <img src="./Convolution/2-convlstm2d-batch-and-dimension.png" alt="ConvLSTM2D batch and dimension"/>
</p>

1 – Generate a set of data  
We generate an array of data of type single and shape [number of batch = 9, samples = 10, time = 7, channels = 6, rows = 5, cols = 5].

2 – Define graph  
We define the first layer of the graph as an Input layer with shape [time = 7, channels = 6, rows = 5, cols = 5].  
Then we add to the graph the ConvLSTM2D layer.

3 – Run graph  
We call the forward method and retrieve the result with the “Prediction 4D” method.  
This method returns:
- the layer information (cluster with layer name, graph index, and shape)
- the prediction with shape [samples, filters, new_rows, new_cols].  
The output dimension again depends on the parameter `return_sequences`.

---

<p align="center">
  <a href="../Layers.md" style="text-decoration:none; font-weight:bold;">⬅️ Back to Layers</a>
</p>
