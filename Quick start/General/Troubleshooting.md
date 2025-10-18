# 🧩 Troubleshooting

This section presents the different errors that can appear when using the library.

---

| **Code** | **VI** | **Information** |
|:--:|:--:|:--|
| **5001** | check_bidirectional_output | The layers sent in the “layer” and “backward_layer” parameters of the **Bidirectional** layer must have the same output shape, unless the value of the merge_mode parameter is “concat”. For layers to have the same output shape, the same value must be set in the “units” parameter (parameter of the layer sent to the bidirectional layer). |
| **5002** | check_bidirectional_return_sequences | The layers sent in the “layer” and “backward_layer” parameters of the **Bidirectional** layer must have the same value for the return_sequences parameter. |
| **5003** | check_conv | The convolution is not feasible because the shape of the input is not large enough.<br>✅ Solutions:<br>• Enlarge the input size<br>• Reduce the size of the kernel<br>• Set the “padding” parameter to “same” (padding will be added to convolve in all cases) |
| **5004 – 5027** | check_attention | The entries in the **Attention** layer do not have the correct input shape. |
| **5004 – 5026** | check_additive_attention | The entries in the **AdditiveAttention** layer do not have the correct input shape. |
| **5004 – 5026** | check_multiheadattention | The entries in the **MultiHeadAttention** layer do not have the correct input shape. |
| **5006** | check_input_same_index | The index selected when formatting the data at the input of the forward is already defined. |
| **5007** | check_input_shape | The input layer does not exist. Add the **Input** layer at the beginning of the model or use the “in/out param” of the starting layer. |
| **5008** | check_nb_input | The number of inputs sent to the forward does not match the number of inputs in the model. |
| **5009** | check_nb_y_true | The number of outputs (y_true) sent to the loss does not correspond to the number of trainable outputs.<br>⚠️ If your forward is in training mode, it will not allow loss; for metric loss, use metric functionalities. |
| **5010** | warning_input_shape | An input already exists, so the input shape you defined in the “in/out param” is ignored. |
| **5011** | check_output_same_index | The index selected when formatting data sent to the loss (y_true) is already defined. |
| **5012** | check_shape | The inputs of the operand (**Add / Average / Multiply / Substract**) do not have the same shape. |
| **5013** | check_shape_concat | The entries of the **Concatenate** layer do not have the same shape.<br>Note that the size of the axis on which we concatenate can differ.<br>Example: for shapes (10, 2, 3) and (10, 2, 4), if “axis=1” an error occurs. If “axis=2”, the layer considers both entries as (10, 2). |
| **5014** | check_shape_set_input | The dimensions of the input array do not match those expected. |
| **5015** | check_shape_set_weight | The dimensions of the weight array do not match those expected. |
| **5016** | check_shape_y_true | The dimensions of the y_true array provided do not match those expected. |
| **5018** | warning_output_index | The output order specified is out of bound *(x < 0 or x > nb_output)*. |
| **5019** | warning_input_name | The layer name specified isn’t an input of the model. |
| **5020** | check_output_same_name | The name specified when formatting data sent to the loss (y_true) is already defined. |
| **5021** | warning_input_index | The input order specified is out of bound *(x < 0 or x > nb_input)*. |
| **5022** | display_name_error | The name specified doesn’t exist in the graph. |
| **5023 – 5039** | check_gpu_layer | One or more layers are not available in CUDA version. |
| **5024** | display_dim_error | The layer does not support the given dimension. |
| **5028 – 5029** | check_dim | The input is incompatible with the layer.<br>Example: input shape (10, 2, 3, 5) gives product 300; if output wants 3D, shape should be (10, 3, 10). |
| **5030** | check_graphs_shape | The output shape of the first graph is incompatible with the input shape of the second. |
| **5031** | warning_y_true_name | The name shown is not a driveable output of the model. |
| **5032 – 5033** | check_pool_shape | The kernel size or the stride does not have correct values. |
| **5034** | check_filter_units | The value assigned to “n_filters” must be strictly positive. |
| **5035** | check_embedding_input_output_dim | The **Embedding** layer must have strictly positive “input_dim” and “output_dim”. |
| **5036** | check_rnn_gpu_integration | The “activation” parameters of the RNN layer cells are incompatible with the CuDNN version. |
| **5037** | check_fit_metric_best | The metric in “Comparison Metric” is not present in the `metrics_array`. |
| **5038** | check_multi_input_batch | The batch size differs between input layers (**Add / Average / Multiply / Substract**). |
| **5040 – 5042** | check_gpu_ready | Your GPU is not ready. You must have a CUDA-compatible GPU or install CUDA.<br>➡️ Use the **installer** to start the installation. |
| **5043** | warning_attention_scale | The **AdditiveAttention** layer has no weight because “use_scale” = False. |
| **5044** | check_index | The index specified doesn’t exist in the graph. |
| **5050** | Licence not installed | The licence is not installed, so the toolkit could not run. |
| **5051** | Licence expired | Licence expired, so the toolkit could not run. |
| **5052** | Runtime Error | Runtime error occurred, toolkit could not run. |
| **5053** | Reactivation needed | Licence reactivation needed (Use **SOTA** to reactivate the licence on this computer). |




