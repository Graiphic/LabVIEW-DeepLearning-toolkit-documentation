# ConvLSTM3D

> 🔹 *Layer Documentation – Deep Learning Toolkit for LabVIEW*

---

## Description

Setup and add the convolution LSTM 3D layer into the model during the definition graph step.  
Type : *polymorphic.*

<p align="center">
  <img src="./Convolution/conv_lstm_3d_add_to_graph.png" alt="ConvLSTM3D Layer VI" width="400"/>
</p>

---

## Input parameters

| **Parameters** | **Interface** |
|----------------|----------------|
| **![OBJ](./Type/input_object.png) Model in :** *model architecture.* <br> **![FCT](./Type/cluster.png) Parameters :** layer parameters. <br><br> **![I32](./Type/integer-32.png) filters :** *integer*, the dimensionality of the output space.<br>Default value “1”. <br><br> **![array-I32](./Type/array-integer-32.png) size :** *array integer*, specify the dimensions of the convolution window.<br>Default value “[3,3,3]”. <br><br> **![array-I32](./Type/array-integer-32.png) stride :** *array integer*, specify the strides of the convolution.<br>Default value “[1,1,1]”. <br><br> **![array-I32](./Type/array-integer-32.png) explicit padding :** *array*, specifies the number of pixels to pad at the beginning and end of each spatial axis. Batch and channel axes are not padded. Only used when padding = **EXPLICIT**.<br>Default value “empty”. <br><br> **![enum](./Type/enum.png) padding :** *enum*, type of padding to apply.<br>Default value “VALID”. <br><br> **![cluster](./Type/cluster.png) Activation :** *cluster*, applied to the candidate cell input. This function transforms the new information considered for updating the cell state. <br><br> **![cluster](./Type/cluster.png) Recurrent Activation :** *cluster*, applied to the input, forget, and output gates. It controls which parts of the past information are allowed to pass or be blocked. <br><br> **![cluster](./Type/cluster.png) Output Activation :** *cluster*, applied to the updated cell state before producing the visible hidden output of the LSTM at each time step. <br><br> **![TF](./Type/booleen.png) use bias? :** *boolean*, whether the layer uses a bias vector.<br>Default value “True”. <br><br> **![cluster](./Type/cluster.png) Kernel Initializer :** *cluster*, initializer for the kernel weights matrix used for the linear transformation of the inputs. <br><br> **![cluster](./Type/cluster.png) Recurrent Initializer :** *cluster*, initializer for the recurrent kernel weights matrix used for the linear transformation of the recurrent state. <br><br> **![cluster](./Type/cluster.png) Bias Initializer :** *cluster*, initializer for the bias vector. <br><br> **![TF](./Type/booleen.png) unit forget bias? :** *boolean*, if True, adds 1 to the bias of the forget gate at initialization. Used in combination with Bias Initializer = “Zeros”.<br>Default value “True”. <br><br> **![SGL](./Type/double.png) dropout :** *float*, between 0 and 1. Fraction of the units to drop for the linear transformation of the inputs. <br><br> **![SGL](./Type/double.png) recurrent dropout :** *float*, between 0 and 1. Fraction of the units to drop for the linear transformation of the recurrent state. <br><br> **![TF](./Type/booleen.png) return sequences? :** *boolean*, whether to return the last output in the output sequence, or the full sequence.<br>Default value “False”. <br><br> **![TF](./Type/booleen.png) stateful? :** *boolean*, if True, the last state for each sample in a batch will be used as initial state for the following batch.<br>Default value “False”. <br><br> **![cluster](./Type/cluster.png) Kernel Regularizer :** *cluster*, regularizer function applied to the kernel weights matrix. <br><br> **![cluster](./Type/cluster.png) Recurrent Regularizer :** *cluster*, regularizer function applied to the recurrent kernel weights matrix. <br><br> **![cluster](./Type/cluster.png) Bias Regularizer :** *cluster*, regularizer function applied to the bias vector. <br><br> **![TF](./Type/booleen.png) training? :** *boolean*, whether the layer is in training mode (can store data for backward).<br>Default value “True”. <br><br> **![TF](./Type/booleen.png) store? :** *boolean*, whether the layer stores the last iteration gradient (accessible via the “get_gradients” function).<br>Default value “False”. <br><br> **![TF](./Type/booleen.png) update? :** *boolean*, whether the layer’s variables should be updated during backward (equivalent to freezing the layer).<br>Default value “True”. <br><br> **![DBL](./Type/double.png) lda coeff :** *float*, defines the coefficient by which the loss derivative will be multiplied before being sent to the previous layer (since during the backward run we go backwards).<br>Default value “1”. <br><br> **![ABC](./Type/string.png) name (optional) :** *string*, name of the layer. | <img src="./Convolution/conv_lstm_3d_param.png" alt="ConvLSTM3D Parameters" width="240"/> |

---

## Output parameters

**![OBJ](./Type/output_model.png) Model out :** model architecture.

---

## Dimension

### Input shape

6D tensor with shape:  
- If `data_format = 'channels_last'` : *(samples, time, rows, cols, depth, channels)*  
- If `data_format = 'channels_first'` : *(samples, time, channels, rows, cols, depth)*

### Output shape

- If `return_sequences = True` :  
  - If `data_format = 'channels_last'` : 6D tensor *(samples, timesteps, new_rows, new_cols, new_depth, filters)*  
  - If `data_format = 'channels_first'` : 6D tensor *(samples, timesteps, filters, new_rows, new_cols, new_depth)*  
- If `return_sequences = False` :  
  - If `data_format = 'channels_last'` : 5D tensor *(samples, new_rows, new_cols, new_depth, filters)*  
  - If `data_format = 'channels_first'` : 5D tensor *(samples, filters, new_rows, new_cols, new_depth)*

---

## Example

All these examples are snippets PNG, you can drop these Snippet onto the block diagram and get the depicted code added to your VI (Do not forget to install Deep Learning library to run it).

---

### ConvLSTM3D layer

<p align="center">
  <img src="./Convolution/1-convlstm3d-layer.png" alt="ConvLSTM3D Layer Example"/>
</p>

1 – Generate a set of data  

We generate an array of data of type single and shape [samples = 10, time = 7, channels = 6, rows = 5, cols = 5, depth = 3].

2 – Define graph  

First, we define the first layer of the graph which is an Input layer (explicit input layer method).  
This layer is setup as an input array shaped [time = 7, channels = 6, rows = 5, cols = 5, depth = 3].  
Then we add to the graph the ConvLSTM3D layer.

3 – Run graph  

We call the forward method and retrieve the result with the “Prediction 5D” method.  
This method returns two variables:  
- the first one is the layer information (cluster composed of the layer name, the graph index and the shape of the output layer),  
- the second one is the prediction with a shape of [samples, filters, new_rows, new_cols, new_depth].  

The output dimension depends on the parameters “return_sequences” (refer to the chapter *Dimension*).

---

### ConvLSTM3D layer, batch and dimension

<p align="center">
  <img src="./Convolution/2-convlstm3d-batch-and-dimension.png" alt="ConvLSTM3D Layer Batch Example"/>
</p>

1 – Generate a set of data  

We generate an array of data of type single and shape [number of batch = 9, samples = 10, time = 7, channels = 6, rows = 5, cols = 5, depth = 3].

2 – Define graph  

First, we define the first layer of the graph which is an Input layer (explicit input layer method).  
This layer is setup as an input array shaped [time = 7, channels = 6, rows = 5, cols = 5, depth = 3].  
Then we add to the graph the ConvLSTM3D layer.

3 – Run graph  

We call the forward method and retrieve the result with the “Prediction 5D” method.  
This method returns two variables, the first one is the layer information (cluster composed of the layer name, the graph index and the shape of the output layer) and the second one is the prediction with a shape of [samples, filters, new_rows, new_cols, new_depth].  
The output dimension depends on the parameters “return_sequences”.

---

<p align="center">
  <a href="../Layers.md" style="text-decoration:none; font-weight:bold;">⬅️ Back to Layers</a>
</p>
