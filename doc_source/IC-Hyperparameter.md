# Image Classification Hyperparameters<a name="IC-Hyperparameter"></a>


| Parameter Name | Description | 
| --- | --- | 
| num\_classes | Number of output classes\. This parameter defines the dimensions of the network output and is typically set to the number of classes in the dataset\. **Required** Valid values: positive integer  | 
| num\_training\_samples | Number of training examples in the input dataset\. If there is a mismatch between this value and the number of samples in the training set, then the behavior of the `lr_scheduler_step` parameter is undefined and distributed training accuracy might be affected\. **Required** Valid values: positive integer  | 
| augmentation\_type |  Data augmentation type\. The input images can be augmented in multiple ways as specified below\. [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/sagemaker/latest/dg/IC-Hyperparameter.html) **Optional**  Valid values: `crop`, `crop_color`, or `crop_color_transform`\. Default value: no default value  | 
| beta\_1 | The beta1 for `adam`, that is the exponential decay rate for the first moment estimates\. **Optional**  Valid values: float\. Range in \[0, 1\]\. Default value: 0\.9 | 
| beta\_2 | The beta2 for `adam`, that is the exponential decay rate for the second moment estimates\. **Optional**  Valid values: float\. Range in \[0, 1\]\. Default value: 0\.999 | 
| checkpoint\_frequency | Period to store model parameters \(in number of epochs\)\. **Optional** Valid values: positive integer no greater than `epochs`\. Default value: None \(Save checkpoint at the epoch that has the best validation accuracy\.\) | 
| early\_stopping | `True` to use early stopping logic during training\. `False` not to use it\. **Optional** Valid values: `True` or `False` Default value: `False` | 
| early\_stopping\_min\_epochs | The minimum number of epochs that must be run before the early stopping logic can be invoked\. It is used only when `early_stopping` = `True`\. **Optional** Valid values: positive integer Default value: 10 | 
| early\_stopping\_patience | The number of epochs to wait before ending training if no improvement is made in the relevant metric\. It is used only when `early_stopping` = `True`\. **Optional** Valid values: positive integer Default value: 5 | 
| early\_stopping\_tolerance | Relative tolerance to measure an improvement in accuracy validation metric\. If the ratio of the improvement in accuracy divided by the previous best accuracy is smaller than the `early_stopping_tolerance` value set, early stopping considers there is no improvement\. It is used only when `early_stopping` = `True`\. **Optional** Valid values: 0 ≤ float ≤ 1 Default value: 0\.0 | 
| epochs | Number of training epochs\. **Optional** Valid values: positive integer Default value: 30 | 
| eps | The epsilon for `adam` and `rmsprop`\. It is usually set to a small value to avoid division by 0\. **Optional** Valid values: float\. Range in \[0, 1\]\. Default value: 1e\-8 | 
| gamma | The gamma for `rmsprop`, the decay factor for the moving average of the squared gradient\. **Optional** Valid values: float\. Range in \[0, 1\]\. Default value: 0\.9 | 
| image\_shape | The input image dimensions, which is the same size as the input layer of the network\. The format is defined as '`num_channels`, height, width'\. The image dimension can take on any value as the network can handle varied dimensions of the input\. However, there may be memory constraints if a larger image dimension is used\. Typical image dimensions for image classification are '3, 224, 224'\. This is similar to the ImageNet dataset\. **Optional** Valid values: string Default value: ‘3, 224, 224’ | 
| kv\_store |  Weight update synchronization mode during distributed training\. The weight updates can be updated either synchronously or asynchronously across machines\. Synchronous updates typically provide better accuracy than asynchronous updates but can be slower\. See distributed training in MXNet for more details\. This parameter is not applicable to single machine training\. [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/sagemaker/latest/dg/IC-Hyperparameter.html) **Optional** Valid values: `dist_sync` or `dist_async` Default value: no default value  | 
| learning\_rate | Initial learning rate\. **Optional** Valid values: float\. Range in \[0, 1\]\. Default value: 0\.1 | 
| lr\_scheduler\_factor | The ratio to reduce learning rate used in conjunction with the `lr_scheduler_step` parameter, defined as `lr_new` = `lr_old` \* `lr_scheduler_factor`\. **Optional** Valid values: float\. Range in \[0, 1\]\. Default value: 0\.1 | 
| lr\_scheduler\_step | The epochs at which to reduce the learning rate\. As explained in the `lr_scheduler_factor` parameter, the learning rate is reduced by `lr_scheduler_factor` at these epochs\. For example, if the value is set to "10, 20", then the learning rate is reduced by `lr_scheduler_factor` after 10th epoch and again by `lr_scheduler_factor` after 20th epoch\. The epochs are delimited by ","\. **Optional** Valid values: string Default value: no default value | 
| mini\_batch\_size | The batch size for training\. In a single\-machine multi\-GPU setting, each GPU handles `mini_batch_size`/num\_gpu training samples\. For the multi\-machine training in dist\_sync mode, the actual batch size is `mini_batch_size`\*number of machines\. See MXNet docs for more details\. **Optional** Valid values: positive integer Default value: 32 | 
| momentum | The momentum for `sgd` and `nag`, ignored for other optimizers\. **Optional** Valid values: float\. Range in \[0, 1\]\. Default value: 0\.9 | 
| multi\_label |  Flag to use for multi\-label classification where each sample can be assigned multiple labels\. Average accuracy across all classes is logged\. **Optional** Valid values: 0 or 1 Default value: 0  | 
| num\_layers | Number of layers for the network\. For data with large image size \(for example, 224x224 \- like ImageNet\), we suggest selecting the number of layers from the set \[18, 34, 50, 101, 152, 200\]\. For data with small image size \(for example, 28x28 \- like CIFAR\), we suggest selecting the number of layers from the set \[20, 32, 44, 56, 110\]\. The number of layers in each set is based on the ResNet paper\. For transfer learning, the number of layers defines the architecture of base network and hence can only be selected from the set \[18, 34, 50, 101, 152, 200\]\. **Optional** Valid values: positive integer in \[18, 34, 50, 101, 152, 200\] or \[20, 32, 44, 56, 110\] Default value: 152 | 
| optimizer | The optimizer type\. For more details of the parameters for the optimizers, please refer to MXNet's API\. **Optional** Valid values: One of `sgd`, `adam`, `rmsprop`, or `nag`\. [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/sagemaker/latest/dg/IC-Hyperparameter.html) Default value: `sgd` | 
| precision\_dtype | The precision of the weights used for training\. The algorithm can use either single precision \(`float32`\) or half precision \(`float16`\) for the weights\. Using half\-precision for weights results in reduced memory consumption\. **Optional** Valid values: `float32` or `float16` Default value: `float32` | 
| resize | Resizes the image before using it for training\. The images are resized so that the shortest side has the number of pixels specified by this parameter\. If the parameter is not set, then the training data is used without resizing\. **Optional** Valid values: positive integer Default value: no default value  | 
| top\_k | Reports the top\-k accuracy during training\. This parameter has to be greater than 1, since the top\-1 training accuracy is the same as the regular training accuracy that has already been reported\. **Optional** Valid values: positive integer larger than 1\. Default value: no default value | 
| use\_pretrained\_model | Flag to use pre\-trained model for training\. If set to 1, then the pretrained model with the corresponding number of layers is loaded and used for training\. Only the top FC layer are reinitialized with random weights\. Otherwise, the network is trained from scratch\. **Optional** Valid values: 0 or 1 Default value: 0 | 
| use\_weighted\_loss |  Flag to use weighted cross\-entropy loss for multi\-label classification \(used only when `multi_label` = 1\), where the weights are calculated based on the distribution of classes\. **Optional** Valid values: 0 or 1 Default value: 0  | 
| weight\_decay | The coefficient weight decay for `sgd` and `nag`, ignored for other optimizers\. **Optional** Valid values: float\. Range in \[0, 1\]\. Default value: 0\.0001 | 