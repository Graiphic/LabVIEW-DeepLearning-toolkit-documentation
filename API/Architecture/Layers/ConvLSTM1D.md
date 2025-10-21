# ConvLSTM1D

> 🔹 *Layer Documentation – Deep Learning Toolkit for LabVIEW*

---

## Description

Setup and add the convolution LSTM 1D layer into the model during the definition graph step.  
Type : *polymorphic.*

<p align="center">
  <img src="./Convolution/conv_lstm_1d_add_to_graph.png" alt="ConvLSTM1D Layer VI" width="400"/>
</p>

---

## Input parameters

| **Parameters** | **Interface** |
|----------------|----------------|
| **![OBJ](./Type/input_object.png) Model in :** *model architecture.* <br> **![FCT](./Type/cluster.png) Parameters :** layer parameters. <br><br> **![I32](./Type/integer-32.png) filters :** *integer*, the dimensionality of the output space.<br>Default value “3”. <br><br> **![I32](./Type/integer-32.png) size :** *integer*, specify the length of the 1D convolution window.<br>Default value “3”. <br><br> **![I32](./Type/integer-32.png) stride :** *integer*, specify the stride length of the convolution.<br>Default value “1”. <br><br> **![I32](./Type/array-integer-32.png) explicit padding :** *array*, specifies the number of pixels to pad at the beginning and end of each spatial axis. Batch and channel axes are not padded. Only used when padding = EXPLICIT.<br>Default value “empty”. <br><br> **![ENUM](./Type/enum.png) padding :** *enum*, type of padding to apply.<br>Default value “VALID”. <br><br> **![FCT](./Type/cluster.png) Activation :** *cluster*, applied to the candidate cell input. This function transforms the new information considered for updating the cell state. <br><br> **![FCT](./Type/cluster.png) Recurrent Activation :** *cluster*, applied to the input, forget, and output gates. It controls which parts of the past information are allowed to pass or be blocked. <br><br> **![FCT](./Type/cluster.png) Output Activation :** *cluster*, applied to the updated cell state before producing the visible hidden output of the LSTM at each time step. <br><br> **![TF](./Type/booleen.png) use bias? :** *boolean*, whether the layer uses a bias vector.<br>Default value “True”. <br><br> **![FCT](./Type/cluster.png) Kernel Initializer :** *cluster*, initializer for the kernel weights matrix, used for the linear transformation of the inputs. <br><br> **![FCT](./Type/cluster.png) Recurrent Initializer :** *cluster*, initializer for the recurrent_kernel weights matrix, used for the linear transformation of the recurrent state. <br><br> **![FCT](./Type/cluster.png) Bias Initializer :** *cluster*, initializer for the bias vector. <br><br> **![TF](./Type/booleen.png) unit forget bias? :** *boolean*, if True, add 1 to the bias of the forget gate at initialization. Use in combination with Bias Initializer = ‘Zeros’.<br>Default value “True”. <br><br> **![SGL](./Type/double.png) dropout :** *float*, between 0 and 1. Fraction of the units to drop for the linear transformation of the inputs. <br><br> **![SGL](./Type/double.png) recurrent dropout :** *float*, between 0 and 1. Fraction of the units to drop for the linear transformation of the recurrent state. <br><br> **![TF](./Type/booleen.png) return sequences? :** *boolean*, whether to return the last output in the output sequence, or the full sequence.<br>Default value “False”. <br><br> **![TF](./Type/booleen.png) stateful? :** *boolean*, if True, the last state for each sample at index i in a batch will be used as initial state for the sample of index i in the following batch.<br>Default value “False”. <br><br> **![FCT](./Type/cluster.png) Kernel Regularizer :** *cluster*, regularizer function applied to the kernel weights matrix. <br><br> **![FCT](./Type/cluster.png) Recurrent Regularizer :** *cluster*, regularizer function applied to the recurrent_kernel weights matrix. <br><br> **![FCT](./Type/cluster.png) Bias Regularizer :** *cluster*, regularizer function applied to the bias vector. <br><br> **![TF](./Type/booleen.png) training? :** *boolean*, whether the layer is in training mode (can store data for backward).<br>Default value “True”. <br><br> **![TF](./Type/booleen.png) store? :** *boolean*, whether the layer stores the last iteration gradient (accessible via the “get_gradients” function).<br>Default value “False”. <br><br> **![TF](./Type/booleen.png) update? :** *boolean*, whether the layer’s variables should be updated during backward. Equivalent to freeze the layer.<br>Default value “True”. <br><br> **![DBL](./Type/double.png) lda coeff :** *float*, defines the coefficient by which the loss derivative will be multiplied before being sent to the previous layer (since during the backward run we go backwards).<br>Default value “1”. <br><br> **![ABC](./Type/string.png) name (optional) :** *string*, name of the layer. | <img src="./_params/conv_lstm_1d_param.png" alt="ConvLSTM1D Parameters" width="250"/> |

---

## Output parameters

**![OBJ](./Type/output_model.png) Model out :** model architecture.

---

## Dimension

### Input shape

4D tensor with shape:
- If *data_format* = ‘channels_last’ : *(samples, time, rows, channels)*.  
- If *data_format* = ‘channels_first’ : *(samples, time, channels, rows)*.

### Output shape

If *return_sequences* = True :
- If *data_format* = ‘channels_last’ : 4D tensor with shape *(samples, timesteps, new_rows, filters)*.  
- If *data_format* = ‘channels_first’ : 4D tensor with shape *(samples, timesteps, filters, new_rows)*.

If *return_sequences* = False :
- If *data_format* = ‘channels_last’ : 3D tensor with shape *(samples, new_rows, filters)*.  
- If *data_format* = ‘channels_first’ : 3D tensor with shape *(samples, filters, new_rows)*.

---

## Example

All these examples are snippets PNG, you can drop these Snippet onto the block diagram and get the depicted code added to your VI (Do not forget to install Deep Learning library to run it).

---

### ConvLSTM1D layer

<p align="center">
  <img src="./Convolution/1-convlstm1d-layer.png" alt="ConvLSTM1D Example"/>
</p>

1 – Generate a set of data  

We generate an array of data of type single and shape [samples = 10, time = 7, channels = 6, rows = 5].

2 – Define graph  

First, we define the first layer of the graph which is an Input layer (explicit input layer method).  
This layer is setup as an input array shaped [time = 7, channels = 6, rows = 5].  
Then we add to the graph the ConvLSTM1D layer.

3 – Run graph  

We call the forward method and retrieve the result with the “Prediction 3D” method.  
This method returns two variables, the first one is the layer information (cluster composed of the layer name, the graph index and the shape of the output layer) and the second one is the prediction with a shape of [samples, filters, new_rows].  
The output dimension depends on the parameters “return-sequences” refer to the chapter “Dimension” of this documentation.

---

### ConvLSTM1D layer, batch and dimension

<p align="center">
  <img src="./Convolution/2-convlstm1d-batch-and-dimension.png" alt="ConvLSTM1D Batch Example"/>
</p>

1 – Generate a set of data  

We generate an array of data of type single and shape [number of batch = 9, samples = 10, time = 7, channels = 6, rows = 5].

2 – Define graph  

First, we define the first layer of the graph which is an Input layer (explicit input layer method).  
This layer is setup as an input array shaped [time = 7, channels = 6, rows = 5].  
Then we add to the graph the ConvLSTM1D layer.

3 – Run graph  

We call the forward method and retrieve the result with the “Prediction 3D” method.  
This method returns two variables, the first one is the layer information (cluster composed of the layer name, the graph index and the shape of the output layer) and the second one is the prediction with a shape of [samples, filters, new_rows].  
The output dimension depends on the parameters “return-sequences” refer to the chapter “Dimension” of this documentation.

---

<p align="center">
  <a href="../Layers.md" style="text-decoration:none; font-weight:bold;">⬅️ Back to Layers</a>
</p>
